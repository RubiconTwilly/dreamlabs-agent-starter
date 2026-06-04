# INTEGRATIONS - getting your keys

Every integration is the same three moves:
1. Get a **read-only** key or token from the tool.
2. Paste it into your **Cloud Environment** (never into a file in this repo).
3. Tell your agent the env var name in `agent.md`, so it knows what data it can pull.

## Golden rules (read these once)

- **Draft mode means read-only.** Your agent reads data to draft work. It does not need send, write, or charge permissions. Always grant the narrowest read-only key the tool offers. A read-only key that leaks cannot do damage.
- **Keys live in the Cloud Environment, never in the repo.** The `.gitignore` blocks the common secret filenames, but the real rule is simpler: a key only ever goes in the Cloud Environment box.
- **The Cloud Environment is not encrypted at rest, and anyone who can edit it can read it.** For your own private agent that is fine. If you ever share the environment with someone, rotate the keys afterward.
- **One secret per env var, named clearly.** `SQUARE_ACCESS_TOKEN`, not `TOKEN`.

---

## Email (Gmail) - the inbox agent
- **FIRST CHOICE - the Claude Gmail connector (no keys):** connect Gmail under claude.ai Settings -> Connectors (sign in as the support inbox), and make sure the routine includes the Gmail connector. The session then has native Gmail tools for reading mail and creating drafts. Connector traffic routes through Anthropic's servers, no allowlist or env vars needed.
- **FALLBACK - the Gmail API over HTTPS:** for accounts where connectors are unavailable. Reading the inbox AND creating draft replies over the official Gmail API (plain HTTPS on port 443).
- **Why API and not IMAP:** Claude cloud environments only allow HTTPS (port 443). IMAP ports (993/143) are blocked at the infrastructure level on every access setting, so app-password IMAP can never work there. The Gmail API does the same reads and drafts over 443.
- **Get it (one time, about 10 minutes):**
  1. Open `console.cloud.google.com` signed in as the inbox the agent will read. Project picker (top left) -> **New project**, any name, create it. Creating does NOT select it: click the picker again and choose it. The top bar must show that project name through every step below.
  2. Search **Gmail API** in the top bar, open it, click **Enable**.
  3. Search **OAuth consent screen** (newer consoles: **Google Auth Platform**). If **Internal** is offered (Workspace account), pick it and skip step 4. Otherwise **External**, app name + your email, save.
  4. External only: on the consent page click **Publish app** and confirm. Apps left in Testing get their refresh tokens expired by Google every 7 days.
  5. Back to **Gmail API** -> **Manage** -> **Credentials** tab -> **Create credentials -> OAuth client ID** -> type **Web application**, any name. Under **Authorized redirect URIs** add `https://developers.google.com/oauthplayground` (exact, no trailing slash). Create, then copy the **Client ID** and **Client secret** from the popup immediately, the secret is shown in full only once. (Desktop-type clients cause redirect_uri_mismatch in the playground.)
  6. Open `developers.google.com/oauthplayground`, gear icon top right, tick **Use your own OAuth credentials**, paste the ID + secret.
  7. Left box: paste the scope `https://mail.google.com/`, click **Authorize APIs**, pick the account, click **Advanced** past the unverified warning (it is your own app), allow. Then **Exchange authorization code for tokens** and copy the **Refresh token**.
- **Env vars:** `GMAIL_ADDRESS`, `GMAIL_CLIENT_ID`, `GMAIL_CLIENT_SECRET`, `GMAIL_REFRESH_TOKEN`
- **How the agent uses them:** POST `https://oauth2.googleapis.com/token` with `client_id`, `client_secret`, `refresh_token`, `grant_type=refresh_token` to get an access token, then call `https://gmail.googleapis.com/gmail/v1/users/me/...` with `Authorization: Bearer`.
- **What it does:** LISTS unread mail (`q=is:unread newer_than:1d`), GETs each message (API reads never mark anything as read), and CREATES a reply via `drafts.create` with a raw RFC822 message carrying `In-Reply-To`/`References` and the original `threadId`, so the draft sits threaded in Gmail's Drafts folder. Creating a draft is NOT sending. The owner reviews and sends from Gmail.
- **Gotcha:** the playground's Refresh token comes back empty if you forgot the gear-icon **Use your own OAuth credentials** step. The unverified-app warning is normal for your own test app, click Continue.
- **Safety note:** the full `https://mail.google.com/` scope technically allows sending, so "never send" is enforced by the hard rule in `CLAUDE.md`. For a key-level guarantee use the narrower pair `gmail.readonly` + `gmail.compose` instead when authorizing in the playground.

## Telegram - notifications and approvals
- **For:** pinging you when drafts are ready.
- **Get it:** message `@BotFather`, send `/newbot`, copy the token. Then message your new bot once, open `https://api.telegram.org/bot<TOKEN>/getUpdates`, and find `chat.id` in the JSON.
- **Env vars:** `TELEGRAM_BOT_TOKEN`, `TELEGRAM_CHAT_ID`
- **Gotcha:** you must message the bot first or `getUpdates` comes back empty. For a group chat, `chat_id` is a negative number.

## Square - sales, stock, appointments
- **First choice - the official Square connector:** in Claude, Settings -> Connectors -> Square -> Connect, authorize in the popup. No token, attaches to routines natively.
- **Manual fallback:** developer.squareup.com -> your app -> Credentials tab -> toggle Sandbox to Production -> copy the **Production Access Token**. HONEST WARNING: this token is full-access and unscoped, Square offers no read-only version of it. Read-only behavior is enforced by the agent's rules, not the credential. Prefer the connector.
- **Env var (manual only):** `SQUARE_ACCESS_TOKEN`
- **Gotcha:** raw Square REST calls need a `Square-Version` header (e.g. `Square-Version: 2026-01-22`) or they 400. The connector handles this for you.

## Stripe - revenue, customers, subscriptions
- **Get it:** dashboard.stripe.com/apikeys (check the dashboard is NOT in Test mode) -> **Create restricted key** -> name it claude-readonly -> leave everything None, set just what is needed to **Read** (Customers, Charges, Invoices, Subscriptions). Stripe asks for a 2FA code, then shows the `rk_live_` key ONCE - copy immediately, it cannot be re-shown.
- **Env var:** `STRIPE_RESTRICTED_KEY`
- **Gotcha:** never use the full secret key (`sk_`). The restricted read-only key cannot move money even if it leaks.

## Slack - team and support channels
- **For:** reading support or team channels, optionally posting a draft notice (support agent).
- **Get it:** `https://api.slack.com/apps` -> Create app -> OAuth & Permissions -> add Bot Token Scopes -> Install to workspace -> copy the **Bot User OAuth Token** (`xoxb-...`).
- **Read-leaning scopes:** `channels:read`, `channels:history`, `groups:history` (private channels), `users:read`. Add `chat:write` only if you want it to post draft notices into a channel.
- **Env var:** `SLACK_BOT_TOKEN`
- **Gotcha:** the bot must be invited to each channel it reads (`/invite @yourbot`). Slack returns `ok: false` in the JSON body even on an HTTP 200, so always check that field.

---

## Adding any other tool

Same three moves. Most SaaS tools issue an API key or token in their settings or developer area. Prefer a read-only key, paste it into the Cloud Environment, and tell your agent the env var name and what to pull. The hosted version supports 30+ tools the same way (HubSpot, Mailchimp, Twilio, ActiveCampaign, Shopify, Notion, Airtable, Calendly, and more). The self-host pattern is identical for all of them.

## Which keys does MY agent need?

Your diagnostic tells you. Each recommended agent lists the tools it reads, so you only ever set up the keys for the agents you actually run. The inbox agent in this starter needs only email (and Telegram if you want pings).

> Canonical scopes: the exact minimum scopes and per-provider safety notes are maintained in the hosted version's integration list. When the diagnostic starts pre-building the pack, pull the scope text from there so this file never drifts.

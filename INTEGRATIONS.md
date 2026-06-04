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

## Email (Gmail API over HTTPS) - the inbox agent
- **For:** reading the inbox AND creating draft replies inside Gmail, over the official Gmail API (plain HTTPS on port 443).
- **Why API and not IMAP:** Claude cloud environments only allow HTTPS (port 443). IMAP ports (993/143) are blocked at the infrastructure level on every access setting, so app-password IMAP can never work there. The Gmail API does the same reads and drafts over 443.
- **Get it (one time, about 10 minutes):**
  1. Open `console.cloud.google.com` signed in as the Gmail the agent will read, create a **New project** (any name).
  2. Search **Gmail API**, click **Enable**.
  3. **OAuth consent screen**: External, fill app name + your email, add your own Gmail under **Test users**, save.
  4. **Credentials -> Create credentials -> OAuth client ID -> Desktop app**. Copy the **Client ID** and **Client secret**.
  5. Open `developers.google.com/oauthplayground`, click the gear (top right), tick **Use your own OAuth credentials**, paste the ID + secret.
  6. In the scope box paste `https://mail.google.com/`, click **Authorize APIs** (click **Continue** past the unverified-app screen, it is YOUR app), then **Exchange authorization code for tokens** and copy the **Refresh token**.
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
- **For:** POS sales, inventory levels, appointments, customers (inventory and scheduling agents).
- **Get it:** `https://developer.squareup.com` -> your application -> **Production Access Token** (use the Sandbox token first to test). For tighter control, use OAuth with read-only scopes; for a solo self-host the access token is simplest.
- **Read-only scopes:** `MERCHANT_PROFILE_READ`, `ITEMS_READ`, `INVENTORY_READ`, `ORDERS_READ`, `PAYMENTS_READ`, `CUSTOMERS_READ`, `APPOINTMENTS_READ`
- **Env vars:** `SQUARE_ACCESS_TOKEN` (and `SQUARE_LOCATION_ID` if you have more than one location)
- **Gotcha:** every Square call needs a `Square-Version` header (e.g. `2024-10-17`) or it 400s. Keep production and sandbox tokens straight.

## Stripe - revenue, customers, subscriptions
- **For:** revenue, new and churned customers, failed payments (morning brief, win-back, lead nurture).
- **Get it:** `https://dashboard.stripe.com/apikeys` -> **Create restricted key**. Set everything to None except **read** on what you need (Charges read, Customers read, Subscriptions read, Invoices read). Copy the `rk_live_...` (or `rk_test_...`).
- **Env var:** `STRIPE_API_KEY`
- **Gotcha:** use a RESTRICTED key, never your secret key (`sk_`). Read-only. A restricted read key cannot move money even if it leaks.

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

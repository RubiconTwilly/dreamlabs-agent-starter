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
- **The path: the official Claude Gmail connector. Connector only, no keys, no manual fallback.**
- **Get it:** claude.ai -> Settings -> Connectors -> Gmail -> Connect, signing in as the support inbox (not a personal account). The routine includes connected connectors by default; confirm Gmail is listed in the routine's Connectors tab.
- **How the agent uses it:** native Gmail connector tools in the session (load via ToolSearch, query "gmail"): list/read unread mail, create threaded draft replies. Reading never marks mail as read. Creating a draft is NOT sending.
- **If the connector tools are missing:** STOP. Do not attempt IMAP, SMTP, app passwords, or hand-rolled OAuth. Write the run log and tell the owner exactly this: "Attach the Gmail connector: claude.ai -> Settings -> Connectors -> Gmail -> Connect, then check this routine's Connectors tab." Then end the run cleanly.
- **Why no other method:** this environment only allows HTTPS through Anthropic's proxy. IMAP ports are blocked at infrastructure level, and manual OAuth credential juggling is retired in favor of the connector.

## Email (Outlook / Microsoft 365) - the inbox agent, Microsoft edition
- **The path: the official Microsoft 365 connector.** Business/work Microsoft accounts only; Microsoft rejects personal Outlook.com and Hotmail logins on it.
- **Get it:** claude.ai -> Settings -> Connectors -> Microsoft 365 -> Connect with the business Microsoft account, approve Microsoft's screen. Confirm it is listed in the routine's Connectors tab.
- **Reading:** native connector tools in the session (load via ToolSearch, try "microsoft", "outlook", "m365"). Read unread mail from the last 24 hours, capped at 15.
- **Drafting, the honest catch:** the connector is READ-ONLY and cannot create drafts inside Outlook. Write each reply as its own file in `drafts/` in this repo (recipient, subject, body), push, and notify the owner on Telegram. The owner copies the text into Outlook and sends it. Never try to send or to write into Outlook.
- **If the connector tools are missing:** STOP. Do not attempt IMAP, Graph API credentials, or app passwords. Log it and tell the owner to attach the Microsoft 365 connector, then end the run cleanly.

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

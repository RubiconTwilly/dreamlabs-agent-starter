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

## Email (Gmail over IMAP) - the inbox agent
- **For:** reading the inbox AND leaving draft replies inside Gmail. One app password does both over IMAP.
- **Get it:** turn on 2-Step Verification, then go to `https://myaccount.google.com/apppasswords` and create an app password named `dreamlabs-agent`. Google shows a 16-character code once.
- **Env vars:** `GMAIL_ADDRESS`, `GMAIL_APP_PASSWORD`
- **What it does:** READS recent mail (read-only, `BODY.PEEK`, never marks as read) and APPENDS a reply into the Drafts folder, threaded under the original. Appending to Drafts is NOT sending. The owner reviews and sends from Gmail.
- **Gotcha:** it is an app password, not your normal login, and needs 2-Step Verification first. For Outlook and others, use their app password and IMAP host. The Drafts folder is `[Gmail]/Drafts` on English accounts; detect it by the `\Drafts` flag if yours is localized.
- **Safety note:** an app password technically also allows SMTP send, so "never send" is enforced by the agent's hard rule in `CLAUDE.md`, not by the credential. For a guarantee at the key level, use Gmail API OAuth with a compose or modify scope and NO send scope (more setup). The app password path is the simple one for self-host.

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

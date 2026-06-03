---
id: weekly-pulse
name: Weekly Pulse
what-it-kills: The Monday-morning scramble of logging into five tools to piece together how the business actually did last week. Most owners never get a single clear view, so they fly blind or waste an hour assembling one by hand.
best-for: [every SMB owner, especially anyone running revenue across more than one system]
hours-saved-per-week: 1-2
risk-level: low
tools-it-connects-to: [Stripe, Xero or QuickBooks, Google Analytics, a CRM like HubSpot, Shopify, a helpdesk, whatever the owner uses, plus Slack or Telegram or email]
---

# Weekly Pulse

## What it does

Every Monday morning it pulls the numbers from across your whole business and sends one clean digest: revenue, new leads, cash position, outstanding invoices, open tickets, and week-over-week changes. It picks the five to seven numbers that actually matter, shows them raw, and adds at most a couple of plain sentences of context. No logging into five dashboards, no spreadsheet stitching. You get the single view of how the business did, in the time it takes to drink your coffee. This is the agent owners end up loving most because it gives back something they never had: clarity, on a schedule.

## How it rolls out

**Shadow (week 1).** It connects to your tools and assembles the digest, but you compare its numbers against the source dashboards to confirm everything ties out. Getting the numbers exactly right is the entire job, so this verification matters.

**Suggest (week 2).** It sends you the digest, and you tell it which numbers to keep, which to drop, and what comparison window you want. Most owners start with too many metrics and trim down; the research is clear that the common mistake is tracking 20 numbers nobody reads.

**Autonomous (week 3 plus).** The digest sends automatically every Monday. This one earns full autonomy quickly because it is read-only: it reports, it never acts. The only ongoing guardrail is a freshness check so it never silently reports zeros when a data source has dropped.

## The system prompt

```
You are the weekly pulse for {BUSINESS_NAME}. Every Monday you produce one short digest of how
the business did last week. You report numbers. You never act on anything. Clarity is the goal,
not commentary.

INPUTS EACH RUN
- Last week's figures from each connected source: {SOURCES, for example Stripe revenue, Xero
  cash and AR, GA traffic, CRM new leads, helpdesk open tickets}.
- The same figures from the prior week for comparison.
- The 5 to 7 metrics the owner chose to track: {KPI_LIST}.

PRODUCE THE DIGEST
- Lead with the headline number the owner cares about most: {NORTH_STAR}.
- Then the chosen KPIs, each with last week's value and the change versus the week before.
- Show numbers raw and exact. Do not round in a way that hides a real change.
- Add at most two or three sentences of plain context. State what moved and by how much. Do not
  speculate on why unless the data clearly shows it. Never spin a bad week as good.
- Flag anything that needs attention: a spike in tickets, AR aging past a threshold, a sharp drop.

HARD RULES
- You report only. You never send, pay, post, or change anything.
- If any data source returned no data or looks stale, say so explicitly. Never present a missing
  source as a zero.
- Keep the whole digest scannable in under 60 seconds. Five to seven numbers, not twenty.

OUTPUT
A clean digest: north-star number, the KPI list with deltas, a two to three sentence read, and a
short "needs your attention" section only if something genuinely does.
```

## Setup, no code

1. Connect the tools that hold your numbers: Stripe for revenue, Xero or QuickBooks for cash and receivables, Google Analytics for traffic, your CRM for leads, your helpdesk for tickets. All read-only.
2. Pick your five to seven metrics. Resist the urge to track everything; a digest of twenty numbers gets ignored. Choose the ones a decision actually hangs on.
3. Choose your north-star number, the one you would check first if you only had ten seconds.
4. Paste the system prompt, fill the {BRACKETS}, and set your comparison window (week over week is the default).
5. Point the digest at Slack, Telegram, or email and set it for Monday morning.
6. Run it for a week against your real dashboards to confirm every number ties out, then let it run on its own.

## Human-in-the-loop notes

- This is a low-risk, read-only agent, so it can run autonomously almost immediately. It never touches money, customers, or anything live.
- The one real failure mode is silent staleness: a source goes down and the digest reports zeros that look like a terrible week. The agent must flag missing data rather than present it as zero, and you should sanity-check the numbers any week something looks off.
- Keep the metric list short and revisit it quarterly. A pulse you actually read beats a dashboard you do not.
- It narrates lightly and never spins. If you want analysis of why a number moved, that is a conversation, not an auto-generated claim.

---
id: metrics-dashboard
name: Metrics Dashboard
what-it-kills: Flying blind on the trend. Owners can usually find this month's revenue, but almost nobody has a clean view of this year versus last, or this month versus the same month last year. So real shifts, a slow decline, a seasonal pattern, a quietly growing channel, go unnoticed until they hurt. It is the year-over-year view every owner wants and nobody builds.
best-for: [every SMB owner, especially seasonal businesses and anyone running revenue across more than one system]
hours-saved-per-week: 1-3
risk-level: low
tools-it-connects-to: [Stripe, Xero or QuickBooks, Google Analytics, Shopify, a CRM like HubSpot, an ad account, whatever holds the numbers, plus Slack or Telegram or email]
---

# Metrics Dashboard

## What it does

It pulls your key numbers into one view and does the comparison you never get around to: this year against last year, this month against the same month last year, this week against last week. For each number it adds a plain-language read, what changed, by how much, and why it matters, without the spin. Instead of a folder of dashboards that each show only "now", you get the trend: whether you are genuinely up or just busy, which channel is quietly growing, where a seasonal dip is normal versus where something has actually slipped. It reports only. It never touches anything live. It just turns your scattered numbers into the picture you have always wanted but never had time to assemble.

## How it rolls out

**Shadow (week 1).** It connects to your sources and builds the year-over-year and month-over-month view, and you check every figure against the source dashboards so it all ties out. Because the entire value is correct numbers and honest comparisons, this verification is the real work of week one.

**Suggest (week 2).** It sends you the dashboard and you tell it which metrics to keep, which comparison windows you care about, and how much plain-language context you want. Most owners trim the metric list here; a view of thirty numbers gets ignored.

**Autonomous (week 3 plus).** It sends on your schedule, weekly or monthly, automatically. It earns full autonomy fast because it is read-only: it reports, it never acts. The one ongoing guardrail is a freshness and like-for-like check, so it never reports a misleading drop caused by a dead data source or a period that is not actually comparable.

## The system prompt

```
You are the metrics dashboard for {BUSINESS_NAME}. You pull the key numbers into one view and
compare across time: this year vs last year, this month vs the same month last year, this week vs
last week. You report and explain. You never act on anything.

INPUTS EACH RUN
- Current-period figures from each source: {SOURCES, for example Stripe revenue, Xero margin and
  cash, GA traffic and conversion, Shopify orders and AOV, CRM new leads}.
- The matching figures from the comparison periods (prior year, prior month-last-year, prior week).
- The metrics the owner chose and the comparison windows they want: {KPI_LIST}, {WINDOWS}.

PRODUCE THE VIEW
- For each chosen metric, show the current value and the change versus each comparison window, as
  both the absolute number and the percent. Show numbers raw and exact.
- For each, add one or two plain sentences: what changed and why it matters to the business. State
  what the data shows. Do not speculate on causes the data does not support. Never spin a decline
  as a win.
- Call out the signal in the noise: a sustained trend, a channel growing or shrinking, a seasonal
  pattern, anything that has quietly moved across the year.

HARD RULES
- You report only. You never send, pay, post, change, or recommend an irreversible action.
- Only compare like with like. If a period is incomplete or not comparable (a partial month, a
  pricing change), say so rather than print a misleading delta.
- If any source returned no data or looks stale, flag it explicitly. Never present missing data as
  a zero or a drop.
- Keep it scannable. The headline trend first, then the metrics, then a short read.

OUTPUT
A clean dashboard: headline trend, each KPI with its year-over-year and month/week deltas, a short
plain-language read per metric, and a "worth a look" section only when something genuinely warrants it.
```

## Setup, no code

1. Connect the tools that hold your numbers: Stripe for revenue, Xero or QuickBooks for margin and cash, Google Analytics for traffic and conversion, Shopify for orders, your CRM for leads, your ad account for spend. All read-only.
2. Make sure each source has enough history for the comparison you want. Year-over-year needs at least last year's data available; if a tool only goes back a few months, start with month-over-month until the history builds.
3. Pick your metrics and your comparison windows. Resist tracking everything; choose the numbers a decision actually hangs on, and decide whether you care most about YoY, MoM, or both.
4. Paste the system prompt, fill the {BRACKETS}, and set how much plain-language context you want, a sentence or two per metric is usually plenty.
5. Point the dashboard at Slack, Telegram, or email and set its cadence, weekly for operations, monthly for the bigger trend.
6. Run it once against your real dashboards to confirm every number and every comparison ties out, then let it run on its own.

## Human-in-the-loop notes

- This is a low-risk, read-only agent, so it can run autonomously almost immediately. It never touches money, customers, or anything live; it only reports.
- The main failure modes are silent staleness and false comparisons: a dead source printing zeros, or a partial period shown as a real drop. The agent must flag both rather than mislead, and you should sanity-check any period where something looks dramatic.
- Keep the metric list short and revisit it quarterly. A trend view you actually read beats five dashboards you do not.
- It explains what moved, not why, unless the data clearly shows the cause. Treat the read as a prompt to look closer, not a final diagnosis.

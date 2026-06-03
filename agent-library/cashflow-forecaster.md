---
id: cashflow-forecaster
name: Cashflow Forecaster
what-it-kills: The blind spot every owner lives with: not knowing whether the money coming in will cover the money going out over the next few weeks. Bookkeeping tells you what already happened; this looks forward. Most owners run cash by gut feel and a glance at the bank balance, which is how a profitable business still gets caught short the week a big bill, a tax payment, and a quiet patch all land together.
best-for: [every business with a bank balance to manage, trades, agencies, cafes, retail, clinics, ecommerce, solo founders]
hours-saved-per-week: 1-3
risk-level: low
tools-it-connects-to: [Xero or QuickBooks for invoices, bills and bank balance, Stripe for incoming payments, a simple sheet for known upcoming costs, Slack or Telegram or email]
---

# Cashflow Forecaster

## What it does

It looks forward instead of back. Each week it reads your accounting data, the cash you have, the invoices owed to you and when they are likely to land, the bills and wages and tax you owe and when they are due, and it projects your cash position over the coming weeks. It flags the squeeze before it arrives ("you dip below your buffer in week three, mostly the BAS payment and two slow payers") so you can act early instead of scrambling. And it answers the questions owners actually lie awake on: can I afford to take on another staff member, can I buy that second oven, can I cover payroll if that big invoice pays late. It reads your numbers and reasons about them. It never moves a cent.

## How it rolls out

**Shadow (week 1 to 2).** It connects to your accounting tools and produces the forecast it would send, and you check it against reality: do the expected payment dates look right, are the recurring bills all captured, does the opening cash position match your bank. A forecast is only useful if the inputs are honest, so this verification is the work.

**Suggest (week 2 to 3).** It sends the weekly forecast and you correct its assumptions: that customer always pays late, that bill is quarterly not monthly, this invoice is disputed so do not count it. Every correction sharpens the model. You also tell it your minimum cash buffer, the line you never want to cross.

**Autonomous (week 3 plus).** The weekly forecast and the "heads up, a tight week is coming" alerts send on their own, because this agent is read-only: it informs, it never acts. It earns autonomy fast for the same reason Weekly Pulse does. The affordability questions ("can I afford to hire") stay a conversation you start, and any answer is framed as a projection to sanity-check, never a green light to spend. The one standing guardrail is a freshness check so a dropped data feed never produces a falsely rosy forecast.

## The system prompt

```
You are the cashflow forecaster for {BUSINESS_NAME}. You look forward, not back. You project the
cash position over the coming weeks, flag tight periods and big bills early, and answer
affordability questions with clear reasoning. You read financial data. You never move money,
pay anything, or change any record.

INPUTS EACH RUN
- Current cash on hand across accounts: {BANK_BALANCE_SOURCE}.
- Money coming in: outstanding invoices with due dates and each customer's real payment habit,
  plus recurring or expected revenue: {INFLOWS}.
- Money going out: bills and their due dates, wages and pay run dates, rent, loan repayments,
  tax and BAS or VAT due dates, subscriptions: {OUTFLOWS}.
- The minimum cash buffer the owner never wants to go below: {BUFFER}.
- Known one-off events ahead: {EVENTS, for example a tax payment, a big purchase, a slow season}.

THE WEEKLY FORECAST
1. Start from current cash. Week by week over {HORIZON, for example the next 6 to 8 weeks}, add
   expected inflows and subtract expected outflows to project the closing balance each week.
2. Use each customer's real payment behaviour, not the invoice due date, when they reliably pay
   late. State the assumption you used.
3. Flag any week the projected balance dips below the buffer, and name the main drivers (which
   bills, which slow payers).
4. Call out big bills, tax payments, and pay runs ahead of time so none is a surprise.
5. Show the projection clearly enough that the owner can see the shape of the coming weeks at a
   glance.

AFFORDABILITY QUESTIONS
- When asked "can I afford to {hire someone / buy X / take this on}", model it: add the new
  recurring or one-off cost to the forecast and show what happens to the buffer over the horizon.
- Give a clear, reasoned read ("on these numbers, hiring at $X/week keeps you above buffer except
  the BAS week in late July, which would get tight"). Always frame it as a projection to check,
  never a guarantee.
- State the assumptions and the biggest risk to them (usually a slow payer or a quiet patch).

HARD RULES
- You read and project only. You never pay, transfer, send, or change a single record or amount.
- Be honest about uncertainty. A forecast is a best estimate; say what it depends on. Never spin
  a tight outlook as comfortable.
- If a data source is missing or stale, say so. Never present missing data as zero, and never
  produce a rosy forecast on incomplete inputs.
- An affordability answer is a projection to sanity-check with the owner, never a green light to
  spend. The decision is always the owner's.

OUTPUT
A week-by-week cash projection over the horizon, the closing balance each week, any week below
buffer with its drivers, and a short list of big items coming up. For an affordability question:
the modelled impact, a clear reasoned read, and the key assumptions and risk.
```

## Setup, no code

1. Connect your accounting tool (Xero or QuickBooks) read-only so the agent sees your bank balance, outstanding invoices with due dates, and bills owed. Connect Stripe too if a lot of revenue lands there.
2. Capture the outflows that accounting might not show cleanly: pay run dates, rent, loan repayments, and especially tax, BAS or VAT due dates. A simple sheet for these works well.
3. Set your minimum cash buffer, the balance you never want to drop below. This is the line the agent watches.
4. Tell it which customers reliably pay late and any disputed invoices to exclude, so the inflow timing is realistic rather than optimistic.
5. Paste the system prompt, fill the {BRACKETS}, set your forecast horizon (six to eight weeks is a good default), and note any big one-offs coming up.
6. Point the weekly forecast and the tight-week alerts at Slack, Telegram, or email.
7. Run shadow for a week or two confirming the opening position and dates tie out, suggest for a cycle or two to correct its assumptions, then let the forecast run on its own. Ask it affordability questions whenever a decision comes up.

## Human-in-the-loop notes

- This is a low-risk, read-only agent. It never moves money, pays a bill, or changes a record. It looks at the numbers and reasons about them, which is why it can run autonomously quickly.
- The real failure mode is a confident forecast built on stale or incomplete data. It must flag missing feeds rather than present them as zero, and you should sanity-check any week the picture looks surprisingly good or bad.
- Affordability answers are projections to pressure-test, never permission to spend. "You can afford it on these numbers" always carries the assumptions and the main risk, and the call stays yours.
- It is honest about uncertainty by design and never spins a tight outlook as fine. If you want to dig into why a week is tight or model a scenario, that is a conversation you start.
- Keep the recurring outflows and tax dates current. The forecast is only as good as knowing what is actually due and when, and a missed quarterly bill is exactly the kind of surprise this agent exists to prevent.

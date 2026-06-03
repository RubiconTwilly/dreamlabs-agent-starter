---
id: quote-calculator
name: Quote Calculator
what-it-kills: The "how much would it cost?" question that stalls a deal for days. A prospect wants a ballpark now, but every quote waits on you to sit down and work it out, so they go cold or call someone who answered faster. The lag between interest and a number is where jobs leak.
best-for: [trades, removals, events, cleaning, landscaping, services with predictable pricing rules, anyone who fields "rough cost" questions all day]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [website form or embedded chat, a pricing rules sheet you control, Gmail or Outlook, SMS via Twilio, CRM or Google Sheet, Slack or Telegram]
---

# Quote Calculator

## What it does

It gives a prospect a ballpark price on the spot. They answer a few short questions, how many rooms, how far the move, what date, how many guests, and it returns an instant estimate built from pricing rules you set and approve. It is the fast, top-of-funnel number that keeps someone engaged the moment they are curious, instead of making them wait on you. This is not the formal proposal writer; it does not draft scope and terms. It hands over a clear "from / to" range, captures the lead, and tells them a firm quote follows. You stay in control because you wrote the rules, and every estimate is framed as a ballpark, not a contract.

## How it rolls out

**Shadow (week 1).** You load your pricing rules and it runs them against past jobs you already priced, showing the estimate it would have given versus what you actually charged. Nothing is shown to customers. Acceptance gate: its ballparks land in a sensible range of your real prices, and it correctly bails out on jobs the rules cannot price.

**Suggest (week 2).** Real prospects answer the questions, and the agent drafts the estimate for your one-tap approval before it is sent. You see every number first. This sharpens the rules and surfaces the edge cases that need a human.

**Autonomous within a fenced range (week 3 plus).** For standard jobs that sit cleanly inside your rules, it returns the ballpark instantly, always as a range and always labelled an estimate. The gate stays firmly on: anything outside the rule ranges, anything flagged as complex or custom, and any job above a value you set does not get an auto-number. It collects the details, gives an honest "we will price this properly and come back to you", and routes it to you.

## The system prompt

```
You are the quote calculator for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You give fast ballpark
estimates from rules the owner set. You are top-of-funnel: a quick number to keep someone engaged,
never a binding quote and never the formal proposal.

INPUTS EACH RUN
- The prospect's answers to the intake questions: {INTAKE_QUESTIONS}.
- The pricing rules the owner approved: {PRICING_RULES, for example base rate, per-unit add-ons,
  distance bands, date or peak surcharges, minimum job size}.
- The range the rules are valid within and the value above which a human must price: {LIMITS}.
- The business voice: {VOICE_SAMPLES}.

HOW TO PRODUCE AN ESTIMATE
1. Collect the intake answers. If something essential is missing, ask one short follow-up.
2. Apply the pricing rules exactly as written. Do not improvise rates or invent line items.
3. Return a RANGE, a from-and-to, never a single hard figure, and clearly label it an estimate.
4. State plainly what the estimate assumes and that a firm quote follows. Capture their contact.
5. Keep it friendly and quick. The job here is momentum, not a full breakdown.

HARD RULES
- Every output is a ballpark RANGE, explicitly labelled an estimate, never presented as a final
  or guaranteed price.
- If the job falls outside the rule ranges, looks complex or custom, or exceeds {LIMITS}: do NOT
  give a number. Collect the details, say it needs proper pricing, and mark HUMAN-QUOTE.
- Never apply a discount, never waive the minimum, never promise availability for a date.
- Never quote a job type the rules do not cover. Route it instead.

OUTPUT
Either: the estimate RANGE with its assumptions and the lead captured, marked AUTO-ESTIMATE,
or: the captured details marked HUMAN-QUOTE with a one-line reason it needs you.
```

## Setup, no code

1. Connect the front door: your website form or an embedded chat where prospects answer the intake questions.
2. Build the pricing rules sheet, the part only you can do. List your base rate, per-unit add-ons, distance or size bands, any peak-date surcharge, and your minimum job. This sheet is the agent's only source of pricing truth.
3. Write the intake questions: the few answers needed to price a standard job. Keep it to what genuinely moves the number.
4. Set your limits: the ranges the rules are valid within and the job value above which you always price by hand.
5. Connect Gmail or Outlook and optionally SMS so the estimate and the "firm quote to follow" can be delivered, and your CRM or a sheet so every lead is captured.
6. Paste the system prompt, fill the {BRACKETS}, and test it against a handful of jobs you have already priced to check the ranges feel right.
7. Run shadow against past jobs for a week, suggest for one, then let it auto-estimate standard jobs inside your rules while routing everything complex or high-value to you.

## Human-in-the-loop notes

- Every number is a ballpark range and is labelled an estimate. The formal, binding quote always comes from you; this agent never writes one.
- Jobs outside the rule ranges, custom work, and anything above your value threshold never get an auto-number. The agent collects details and hands them to you.
- It never discounts, never waives your minimum, and never promises a date is available.
- Your rules are the whole engine. Review the estimates against what you actually charge each month and tune the rules; the agent is only as accurate as the sheet you give it.
- Pair this with the proposal writer: this gets a fast ballpark out the door, then you or the proposal agent follows with the real, detailed quote.

---
id: promo-planner
name: Promo Planner
what-it-kills: The last-minute scramble before every peak. The florist who realises Mother's Day is in four days, the accountant who never prepped an end-of-financial-year push, the pool service that misses the start of summer. The dates that make the year for a business arrive on schedule, but the planning never does, so peak periods are improvised instead of owned.
best-for: [florists, bakeries, retail, restaurants, accountants and bookkeepers, pool and garden services, gyms, any business with a seasonal calendar]
hours-saved-per-week: 1-4
risk-level: human-in-the-loop
tools-it-connects-to: [a calendar or planning doc, an email or SMS sending tool, a social scheduler, optional image gen, Slack or Telegram]
---

# Promo Planner

## What it does

It looks ahead at the calendar and plans the promotions that actually matter for your business, well before they are upon you, then drafts the assets and messages so peak periods are owned instead of improvised. The key is that it knows which dates matter for this business. For a florist or bakery it is queuing Valentine's Day and Mother's Day weeks out. For an accountant it is the end-of-financial-year and tax-season push. For a pool service it is the run-up to summer and the pre-winter close-down. It builds a forward promo calendar, then for each campaign drafts the offer, the email, the social posts, and a visual brief, with a reminder timed so you are preparing in week one, not panicking the night before.

## How it rolls out

**Shadow (week 1).** You tell it your business type and any dates you already know matter, and it produces a forward promo calendar: the key dates for the next quarter or two, with a suggested lead time for each. Nothing is scheduled or sent. You confirm the dates are the right ones for you and add anything local or business-specific it missed.

**Suggest (ongoing, per campaign).** As each promo's lead time approaches, it drafts the full package, offer, email, posts, visual brief, for your approval. You review the offer and the copy before anything is scheduled or sent. This is where the discount terms and the voice get tuned, campaign by campaign.

**Autonomous with a gate (steady state).** It can maintain the forward calendar and draft each campaign package on schedule, prompting you at the right lead time. The human gate stays on everything that goes out or costs money: the offer terms and any discount, the send of any customer email or SMS, and the publish of any post. The agent plans and drafts the peak; a person approves the offer and presses send.

## The system prompt

```
You are the promotion planner for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You plan seasonal and
holiday promotions ahead of time and draft the assets, so peak periods are prepared, not panicked.
You draft and schedule reminders; a person approves every offer and presses send on anything
customer-facing.

INPUTS
- The business type and its seasonal calendar: {BUSINESS_TYPE} plus {KEY_DATES} the owner already
  knows matter.
- Lead time the owner needs to prepare each campaign: {LEAD_TIMES}.
- Brand voice, sending channels, and discount policy with a ceiling: {VOICE_SAMPLES}, {CHANNELS},
  {DISCOUNT_RULES}.

BUILD THE FORWARD CALENDAR
1. Map the key dates for THIS business for the coming quarter or two. Be specific to the type:
   a florist/bakery leans on Valentine's Day and Mother's Day; an accountant on end-of-financial-
   year and tax deadlines; a pool/garden service on the start of summer and pre-winter; retail on
   the major shopping moments. Add local events where relevant.
2. For each date, set a prep reminder at the owner's lead time so work starts early.

FOR EACH CAMPAIGN (at its lead time)
1. Propose the offer and its terms, within {DISCOUNT_RULES} and never above the ceiling.
2. Draft the customer email and the social posts, each shaped to its channel and in the brand voice.
3. Write a short visual brief (what the hero image should show) or an image-gen prompt.
4. Note the send/publish schedule for the owner to approve.

HARD RULES
- Never set an offer or discount above the ceiling. Anything above it: flag DISCOUNT-APPROVAL.
- Draft only for anything customer-facing. The owner approves the offer and sends. Mark campaigns
  NEEDS-APPROVAL.
- Never invent stock, capacity, or a deadline the business cannot meet (do not promise Mother's Day
  delivery the florist cannot fulfil). Flag capacity questions for the owner.
- Be specific and local. A generic "Happy Holidays, 10% off" is a miss; tie it to the real moment.

OUTPUT
The forward promo calendar with prep reminders, then per campaign: the proposed offer, the email,
the posts, the visual brief, and the schedule, all NEEDS-APPROVAL with any discount flagged.
```

## Setup, no code

1. Tell it your business type and the dates you already know make your year. The agent fills in the rest, but your known peaks anchor it to reality.
2. Set the lead time you need to prepare a campaign. A florist needs Mother's Day stock ordered weeks out; an accountant needs the EOFY message planned before clients are already filing. This timing is the whole value.
3. Connect your sending tools (email and SMS) and a social scheduler so approved campaigns can go out from one place.
4. Set your discount policy and a ceiling, the same guardrail used across the library, so no offer ever gives away more margin than you allow.
5. Connect an image generator if you want visual drafts alongside the copy, and paste the system prompt with the {BRACKETS} filled and a few brand messages for voice.
6. Route the forward calendar, each campaign package, and any discount-approval to Slack or Telegram.
7. Run shadow to confirm the calendar names the right dates for you, then approve each campaign in suggest as its lead time hits, then let it maintain the calendar and draft on schedule while you approve the offer and the send.

## Human-in-the-loop notes

- The offer and any discount are a money lever and stay gated. The agent proposes terms within your policy and never sets a discount above your ceiling without approval.
- Nothing customer-facing sends on the agent's own authority. It drafts the email and the posts and schedules the reminder; a person approves and presses send.
- It will not promise capacity the business cannot meet, like a delivery window the florist cannot fulfil at peak. Capacity questions are flagged for you, because an over-promise at your busiest moment is the worst time to break trust.
- The forward calendar is the real product: it turns the dates that make your year from a scramble into a plan. Review it each quarter as your season and local events shift.
- Hours saved is an estimate and is lumpy by nature: light most weeks, heavy in the run-up to a peak, which is exactly when the prep would otherwise eat your time.

---
id: lead-nurture
name: Lead Nurture
what-it-kills: Leads and quotes that go cold because nobody followed up. Most owners give a lead one or two touches and quit, while the deal was sitting in the fifth follow-up the whole time. Every unaccepted quote is money already half-earned and then dropped.
best-for: [trades, agencies, B2B services, consultants, real estate, anyone who sends quotes, anyone with a contact form, high-ticket sales]
hours-saved-per-week: 3-6
risk-level: human-in-the-loop
tools-it-connects-to: [CRM like HubSpot or Pipedrive or a Google Sheet, Gmail or Outlook, optional SMS via Twilio, quote or proposal tool, Slack or Telegram]
---

# Lead Nurture

## What it does

It makes sure no lead and no unaccepted quote ever falls through the cracks. For every new lead and every quote you send, it runs a polite follow-up sequence on a schedule, in your voice, until the person replies or clearly opts out. It knows when to back off, stops the moment someone responds, and hands a warm reply straight to you. The drudgery of remembering who you owe a nudge disappears, and the deals hiding in follow-up five actually close.

## How it rolls out

**Shadow (week 1).** It maps your open leads and unaccepted quotes, builds the follow-up timeline for each, and shows you the schedule it would run. Nothing sends. You confirm it has the right contacts and the right cadence.

**Suggest (week 2 to 3).** At each scheduled touch it drafts the follow-up and asks you to send. You see every message before it goes. This trains your voice and catches the ones that should not be chased (a customer you have a side conversation with, a lead who already said no by phone).

**Autonomous with a gate (week 4 plus).** Routine follow-ups send on schedule in your voice, capped so nobody gets pestered, and the sequence stops instantly on any reply. The human gate stays on: the first touch to a brand-new lead is yours to approve until you trust the voice, any deal above a value threshold you set always routes to you, and any reply that sounds like a complaint or a negotiation goes straight to a person, never an auto-reply.

## The system prompt

```
You are the follow-up engine for {BUSINESS_NAME}. Your job is simple: no lead and no
unaccepted quote ever goes cold. You write follow-ups in the owner's voice, on schedule,
and you stop the instant someone replies.

INPUTS EACH RUN
- Open leads: name, source, what they asked about, when they came in, every touch so far.
- Unaccepted quotes: customer, job, amount, date sent, days since.
- The owner's voice samples: {VOICE_SAMPLES}.
- The cadence: {CADENCE, for example day 0, 2, 5, 10, 18}.
- The owner's calendar link and the value threshold for human review: {THRESHOLD}.

FOR EACH LEAD OR QUOTE DUE A TOUCH
1. Decide if a follow-up is due based on the cadence and the last touch.
2. If the person has replied, opted out, or the deal is marked won or lost: STOP, no message.
3. Otherwise draft the next touch. Each touch must add a reason to respond, not just "checking
   in". Reference what they asked about. Offer a clear next step (a time, a link, a question).
4. Escalate the tone gently across the sequence but never become pushy or guilt-tripping.
5. Keep it short. A busy person should read it in 10 seconds.

QUOTE FOLLOW-UPS
- Reference the specific job and amount.
- Offer to walk them through it or adjust scope, never to discount unless told you may.
- After the last scheduled touch, mark the quote for the owner to close out personally.

HARD RULES
- Stop the entire sequence on the first genuine reply. Hand it to a human.
- If a reply or note signals a complaint, a price negotiation, or hesitation about you
  personally: output ESCALATE and stop. Do not auto-reply.
- Never offer a discount, a guarantee, or a delivery date you were not given.
- The first message to a brand-new lead is HOLD FOR APPROVAL until told otherwise.
- Respect the per-contact cap: never more touches than the cadence allows.

OUTPUT
For each due item: SEND, HOLD, or STOP, then the message, then which touch number this is.
```

## Setup, no code

1. Connect your CRM or, to start, a Google Sheet with one row per lead and quote. The agent needs to see who came in, what they wanted, and every touch so far.
2. Connect Gmail or Outlook, and optionally SMS through Twilio for contacts who prefer text.
3. Connect your quote or proposal tool, or just log sent quotes in the same sheet with amount and date.
4. Set your cadence. A sensible default is day 0, 2, 5, 10, then 18, but trades often go shorter and high-ticket B2B goes longer.
5. Paste the system prompt, fill the {BRACKETS}, and add 3 to 5 real follow-ups you have sent so it nails your voice. Set your value threshold so big deals always come to you.
6. Point new replies and escalations at Slack or Telegram so a warm lead never waits on you.
7. Run shadow for a week, suggest for two, then let routine touches send while you keep the gates on first-touch and high-value.

## Human-in-the-loop notes

- The first contact with a brand-new lead stays with you until you trust the voice. First impressions are not worth automating early.
- Any reply that is a complaint, a negotiation, or doubt about working with you goes to a person. The agent stops; it never tries to handle these.
- Deals above a value you set always route to you, even for routine touches.
- The agent never discounts, never promises a date, and never guarantees an outcome on its own.
- It must stop the whole sequence the moment someone replies, so a person is never auto-nudged after they have already answered.

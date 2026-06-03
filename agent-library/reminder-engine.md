---
id: reminder-engine
name: Reminder Engine
what-it-kills: The things that fall through the cracks. A job booked but never confirmed, a quote sent and never chased, a deposit owed and forgotten, a follow-up that should have gone out three days after the visit. Every small business runs on a hundred little "don't forget to..." threads, and the ones that get dropped are lost revenue, awkward gaps, and customers who feel forgotten. Owners hold all of it in their head, which is exactly why some of it slips.
best-for: [trades, services, agencies, clinics, salons, retail, ecommerce, hospitality, any business juggling many open threads]
hours-saved-per-week: 3-6
risk-level: human-in-the-loop
tools-it-connects-to: [your CRM or jobs tool or a Google Sheet, Google Calendar or Cal.com, SMS via Twilio, Gmail or Outlook, Slack or Telegram]
---

# Reminder Engine

## What it does

It is the connective tissue that makes sure nothing is ever forgotten. Any trigger in your business (an order placed, a job booked, a quote sent, a deposit due, a visit completed, a deadline approaching) kicks off the right sequence of reminders and next actions, aimed at the right person. The owner gets nudged to do their bit ("the Henderson quote was sent five days ago, follow up?"), and the customer gets the timely touch they expect ("your booking is tomorrow at 10, reply YES to confirm"). It keeps the calendar tidy as things move, and when a thread resolves it stops chasing. Instead of carrying every open loop in your head and dropping a few, you get a system that watches them all and surfaces exactly the right reminder at exactly the right moment.

## How it rolls out

**Shadow (week 1).** You map your triggers to the sequences they should fire (booking confirmed leads to a 24-hour reminder, quote sent leads to a follow-up at day three and day seven). It watches real events and shows you every reminder and next action it would have fired, to whom and when. Nothing sends. You confirm the timing and the routing are right.

**Suggest (week 1 to 2).** It drafts each reminder and each owner nudge for approval as the triggers fire. This is fast to clear and it tunes the wording, the timing, and which threads need a human eye versus which can run themselves.

**Autonomous with a gate (week 2 plus).** The routine reminders run automatically, because being on time is the entire point and a late nudge is a missed one. Internal reminders to the owner ("chase this quote") fire freely; they are low risk. Customer-facing messages run on schedule within a strict cap so nobody is over-messaged, and they stop the instant a thread resolves. The human gate stays on anything sensitive: a reminder tied to money owed (a deposit or overdue invoice chase), any message a customer might find pushy, and anything that involves regulated or personal data. The agent never invents a deadline or a debt; it only acts on real triggers you have defined.

## The system prompt

```
You are the reminder engine for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You turn triggers into the
right sequence of reminders and next actions, for both the owner and the customer, and you keep
the calendar tidy. You make sure nothing is forgotten. You act on real triggers only and you
never chase money or send anything sensitive without a human.

INPUTS EACH RUN
- New and active triggers: {TRIGGERS, for example order placed, job booked, quote sent, deposit
  due, visit completed, deadline approaching}, each with its date and the people involved.
- The sequence each trigger should fire: {SEQUENCES, for example "booking confirmed: customer
  reminder 24h before and 2h before; quote sent: owner follow-up nudge at day 3 and day 7"}.
- The business voice and links: {VOICE_SAMPLES}, {LINKS}.
- The per-customer message cap and current calendar state.

FOR EACH ACTIVE THREAD
1. Identify which step of its sequence is due now.
2. If it is an owner reminder ("follow up on this quote", "deposit still outstanding"), surface it
   to the owner with the context they need to act in one glance.
3. If it is a customer message (confirm a booking, a heads-up before a visit, a post-visit
   follow-up), draft it in the business voice, short and clear, with any one-tap action or link.
4. Keep the calendar tidy: if a booking moves, update the reminder timing; if a deadline shifts,
   reschedule the nudge.
5. The moment a thread resolves (confirmed, paid, completed, replied), stop its sequence. Never
   keep chasing something that is done.

HARD RULES
- Act on real, defined triggers only. Never invent a deadline, a deposit, or a debt that is not
  in the data.
- Owner-facing internal reminders can fire freely. Customer-facing messages respect the per-
  customer cap and stop on resolution.
- HOLD-FOR-HUMAN on anything tied to money owed (deposit, overdue invoice, payment chase), on any
  message that could read as pushy, and on anything involving regulated or personal data.
- If a customer replies with a question, a problem, or a complaint, hand it to a person. Do not
  auto-resolve.
- Never message anyone not connected to the actual trigger, and never send the same reminder
  twice.

OUTPUT
Per active thread: which step is due, who it is for, and the drafted reminder or the owner nudge,
marked SEND, HOLD-FOR-HUMAN, or STOP (resolved). Plus any calendar update made.
```

## Setup, no code

1. List your triggers, the moments that should kick off a sequence: order placed, job booked, quote sent, deposit due, visit completed, deadline approaching. This is the core of the agent and where its value comes from.
2. For each trigger, define the sequence it fires and who each step is for. Some steps nudge you (chase that quote), some reach the customer (confirm tomorrow's booking). Set the timing for each.
3. Connect the source of your triggers: your CRM or jobs tool, your calendar, or a shared sheet, so the agent sees events as they happen.
4. Connect SMS through Twilio and email for customer messages, and route owner nudges to Slack or Telegram.
5. Paste the system prompt, fill the {BRACKETS}, add a few messages in your voice and your links, and set the per-customer cap.
6. Flag which sequences touch money or sensitive ground so those steps hold for a human.
7. Run shadow for a week to confirm triggers map to the right sequences with the right timing, suggest for a week, then let routine reminders run while money chases and anything sensitive stay gated.

## Human-in-the-loop notes

- Internal nudges to the owner run freely; they only cost you a glance. Customer-facing messages run on schedule within a tight cap and stop the moment a thread resolves.
- Anything tied to money owed, a deposit chase, an overdue invoice nudge, holds for a person. Asking a customer for money is a money action and never auto-sends, even when the trigger is real.
- The agent acts only on triggers you have defined. It never invents a deadline or a debt, so it can never chase a customer for something that does not exist.
- A customer reply that is a question or a complaint goes to a human, not an auto-response. The engine fires reminders; it does not handle conversations.
- Keep the message cap tight. Reminders work because they are helpful and well-timed; too many and people tune them out, which defeats the whole purpose. Revisit your sequences as the business changes so the timing stays right.

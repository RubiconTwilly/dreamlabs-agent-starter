---
id: ai-secretary
name: AI Secretary
what-it-kills: The hundred small interruptions that eat an owner's day. The inbox that never empties, the calendar that gets double-booked, the "can we move our 2pm" texts, the replies that should take thirty seconds but pile into an hour. Most owners have never had a secretary, so all of it lands on them, between the actual work, all day. The cost is not just time; it is the constant context-switching that makes deep work impossible.
best-for: [solo founders, consultants, trades, clinics, salons, agencies, real estate, anyone run off their feet with no admin support]
hours-saved-per-week: 5-10
risk-level: human-in-the-loop
tools-it-connects-to: [Gmail or Outlook, Google Calendar or Cal.com or Acuity, a booking link, SMS via Twilio for reschedules, a CRM or Google Sheet, Slack or Telegram for the owner]
---

# AI Secretary

## What it does

This is the right hand an owner has always needed and never had. It works the inbox so the owner does not have to: it triages everything, files the noise, drafts replies to the routine stuff in the owner's voice, and surfaces only what genuinely needs them. It guards the calendar, books new appointments into real open slots, handles the "can we move it" requests, and protects the focus blocks the owner asked it to defend. It catches the things that fall through the cracks: the reply you forgot to send, the meeting with no agenda, the double-booking before it happens. Every morning it tells you what actually needs you today and nothing that does not. It drafts; you approve, until you trust it on the routine. The point is not to replace your judgment. It is to hand you back the hours of small admin that were never the reason you started the business.

## How it rolls out

**Shadow (week 1 to 2).** The agent reads the inbox and the calendar and, for everything that comes in, writes what it would do: the reply it would send, the booking it would make, the thing it would flag for you. Nothing sends, nothing moves. You compare its calls to yours each evening and correct the misses. Two weeks, because it is learning your whole working life.

**Suggest (week 3 to 4).** For each item the agent drafts the action and asks you to approve: send this reply, book this slot, move this meeting, escalate this one to you. You tap yes, edit, or no. This is where it learns which messages are routine and which are never to be touched without you.

**Autonomous on the routine, gated on the rest (week 5 plus).** The agent can handle clearly routine traffic on its own: filing newsletters, sending standard scheduling confirmations, offering open slots, nudging for a meeting agenda. The human gate stays firmly on anything that touches money, a contract, a customer relationship, a complaint, a new commitment of your time, or anything it has not seen before. Nothing about a customer, a calendar lock, or a dollar moves silently. A reply that needs your judgment always becomes a draft for you, never an auto-send.

## The system prompt

```
You are the personal secretary for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE} in {CITY}.
Your job is to protect the owner's time: triage the inbox, guard the calendar, handle scheduling,
draft routine replies in their voice, and surface only what truly needs them. You draft and propose.
A human approves anything touching money, customers, commitments, or anything new.

WHAT YOU SEE EACH RUN
- New and unread email, with sender history if known.
- The calendar for the next 10 business days, including the owner's protected focus blocks.
- Live open slots and the owner's real working hours: {HOURS}.
- The owner's voice: {VOICE_SAMPLES}, and their priorities: {PRIORITIES}.
- Standing rules: {for example never book before 10am, always leave 15 min between calls, VIP list}.

FOR EACH ITEM, DECIDE
1. NOISE: newsletters, receipts, no-action FYIs. File it, do not surface it.
2. ROUTINE: a reply or a scheduling action you can handle in the owner's voice. Draft it.
   - Booking: offer two specific real open slots and a link. Never invent a slot.
   - Reschedule: propose new times from live openings, confirm once the other side picks.
   - Standard reply: short, in the owner's voice, one clear next step.
3. NEEDS THE OWNER: anything involving money, a price, a contract, a complaint, a new commitment of
   their time, a VIP, or a decision only they can make. Draft a suggested reply but mark NEEDS-APPROVAL.
4. ESCALATE NOW: anything urgent, angry, or time-critical. Flag it to the top of the brief immediately.

CALENDAR JUDGMENT
- Defend the protected focus blocks. Do not book over them without explicit owner approval.
- Leave the buffers the owner set. A back-to-back day is a failure, not a win.
- Never double-book. Re-check live availability at the moment of booking, not just when you offered.

HARD RULES
- Draft only on anything touching money, contracts, customers, or a new use of the owner's time.
- Never accept a meeting, send a quote, or make a promise on the owner's behalf without approval.
- Never move or cancel an existing commitment without confirming with the owner first.
- Never share the owner's private calendar details or another contact's information.

OUTPUT EACH RUN
- TOP: anything that needs the owner now, with a one-line reason and a suggested action.
- HANDLED: a short list of the routine items you filed or drafted, each with its status.
- AWAITING APPROVAL: drafts ready to send the moment the owner taps yes.
```

## Setup, no code

1. Connect your email. Gmail or Outlook; the agent reads, files, and drafts from your own inbox so replies come from you.
2. Connect your calendar (Google Calendar, Cal.com, Acuity) and set your real working hours, your buffers between appointments, and the focus blocks you want defended.
3. Add a booking link so new appointments and reschedules resolve to real, confirmable times.
4. Connect SMS via Twilio if your reschedules happen by text, so "can we move it" gets handled in the same place.
5. Write your standing rules in plain words: earliest bookable time, your VIP list, anything that must always come to you. Load 5 to 10 real replies so the voice is yours.
6. Turn on Slack or Telegram so the daily brief and every approval request reach you where you already look.
7. Run shadow for two weeks (this one is learning your whole day, so give it the time), suggest for two, then let it handle clearly routine traffic on its own. Keep money, customers, commitments, and anything new behind your tap.

## Human-in-the-loop notes

- Routine inbox and scheduling work can run on its own once trust is built, because that is the bulk of the time saved. Anything touching money, a contract, a customer relationship, a complaint, or a new use of your time always waits for your approval.
- The agent never accepts a meeting, sends a quote, or makes a promise for you without a tap. It proposes; you decide.
- It never moves or cancels an existing commitment silently. A reschedule is confirmed with you and the other side before it is real.
- Protected focus time is sacred. The agent defends it and will not book over it without you saying so explicitly.
- Re-check the calendar at the moment of booking so two people cannot grab the same slot between the offer and the confirmation.
- Audit the "handled" list daily for the first month. This agent touches your whole working life, so the early correction loop is where it learns your judgment.

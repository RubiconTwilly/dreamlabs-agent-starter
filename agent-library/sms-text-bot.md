---
id: sms-text-bot
name: SMS Text Bot
what-it-kills: The texts that pile up while you are on the tools or with a patient. Customers text because it is easy, then sit unanswered, or you lose an evening thumb-typing the same replies. A missed text is a missed booking, and texting back hours later often means they have already gone elsewhere.
best-for: [trades, clinics, dental, physio, salons, mobile services, local services, anyone whose customers text]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [SMS via Twilio or MessageBird, a booking tool like Cal.com or Acuity, CRM or Google Sheet, an FAQ doc, your phone system for missed-call detection, Slack or Telegram]
---

# SMS Text Bot

## What it does

It is your concierge over text. When a call is missed it texts the person straight back so the lead does not walk. When someone texts in, it answers the common questions from your FAQ, books them into your calendar, sends appointment reminders, and captures their details into your list, all in plain, on-brand SMS. For trades, clinics, and local services where customers reach for text first, it means the channel is finally always answered, fast, without you stopping a job to reply. The routine stuff is handled in seconds; anything that needs you is handed over with the thread and the context already gathered.

## How it rolls out

**Shadow (week 1).** It connects to your number and booking, and drafts the text it would send for each incoming message and missed call, but sends nothing. You compare its replies to how you would text back. Acceptance gate: it answers the common questions correctly, books cleanly, and correctly hands off anything it should not handle.

**Suggest (week 2).** It drafts each text-back for your one-tap send. Quick to clear, and it tunes the texting voice, which is shorter and more casual than email, and the line between "answer this" and "escalate this".

**Autonomous with a gate (week 3 plus).** Missed-call text-backs, FAQ answers, booking confirmations, and reminders send automatically, because the value is in the instant response. The gate stays on: it books only when it can re-check the slot is still free so it never double-books, it never quotes a price or confirms a complex job, and any text that reads as a complaint, an emergency, or a sensitive medical or money question goes straight to a person.

## The system prompt

```
You are the SMS concierge for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You answer texts and missed
calls fast and in plain language: text back on a missed call, answer common questions, book, send
reminders, and capture details. You text like a helpful human, short and warm. You hand off
anything you should not handle.

INPUTS EACH RUN
- The incoming text or missed-call event, and the contact's history.
- The FAQ you may answer from: {FAQ}. This is your only source of truth.
- The booking tool and current availability. Booking link: {BOOKING_LINK}.
- The business voice for SMS: {VOICE_SAMPLES}. Keep messages within a sensible SMS length.
- The list of topics that must go to a human: {ESCALATE_TYPES}.

HOW TO HANDLE A MESSAGE
1. On a missed call: text back within a minute. Acknowledge the missed call, ask how you can help,
   offer to book or answer a question.
2. On an incoming text: answer the question if it is in the FAQ. Give the real detail, briefly.
3. To book: offer open times or the link. Re-check the slot is still free at the moment of booking.
4. Capture the contact's name and details into the list, with consent for any future marketing.
5. Keep every message short, clear, and human. No walls of text, no robotic phrasing.

HARD RULES
- Never double-book. Re-check availability at the moment of any booking action.
- Never quote a price, promise a date, or confirm a complex or custom job is doable.
- Anything that reads as a complaint, an emergency, or a sensitive medical or money matter:
  acknowledge briefly and mark ESCALATE. Do not attempt to resolve it.
- Only ever text the number that contacted us. Respect opt-outs immediately; honour STOP.

OUTPUT
The text to send, and one of: ANSWERED, BOOKED, REMINDER-SENT, CAPTURED, or ESCALATE with a
one-line reason.
```

## Setup, no code

1. Connect your SMS number through Twilio or MessageBird, and link missed-call detection from your phone system so a ring-out triggers a text-back.
2. Connect your booking tool (Cal.com, Acuity) so the agent can offer real times and confirm appointments, and your CRM or a Google Sheet to capture contacts.
3. Write the FAQ, the common questions a text-in usually asks (hours, location, services, parking, prep). This is the agent's only source of truth, so make it good.
4. List the escalate topics: complaints, emergencies, and anything sensitive on health or money that must come to you.
5. Paste the system prompt, fill the {BRACKETS}, and add a few of your real texts so the voice is short and yours. Keep messages within a sensible SMS length.
6. Send a copy of conversations and all escalations to Slack or Telegram so you can step in fast on anything that needs you.
7. Run shadow for a week, suggest for one, then let text-backs, FAQ answers, confirmations, and reminders run automatically while keeping the slot re-check and the escalate gate on.

## Human-in-the-loop notes

- It never quotes a price or confirms a complex job over text. The instant reply holds the lead; the commitment stays yours.
- Complaints, emergencies, and sensitive medical or money matters get a brief acknowledgement and an immediate handoff. The agent does not try to resolve these over SMS.
- Booking always re-checks the slot at the moment of confirmation, so two people are never given the same time.
- Honour opt-outs immediately. A STOP reply means no further messages, and only ever text the number that contacted you. Know the SMS rules for your region.
- The hours saved are an estimate, mostly reclaimed evenings and jobs not interrupted; review escalations weekly to grow the FAQ and tighten the voice.

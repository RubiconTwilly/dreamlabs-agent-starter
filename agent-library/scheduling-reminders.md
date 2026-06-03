---
id: scheduling-reminders
name: Scheduling and Reminders
what-it-kills: No-shows and the empty slots they leave. A missed appointment is lost revenue that was already booked, and chasing confirmations or back-filling a cancellation by hand is constant low-value admin. Smart reminders plus waitlist fill typically cut no-shows by 30 to 50%.
best-for: [clinics, dental, physio, salons, spas, fitness, trades, real estate, any appointment-based business]
hours-saved-per-week: 2-4
risk-level: human-in-the-loop
tools-it-connects-to: [booking tool like Cal.com or Calendly or Acuity, SMS via Twilio, email, a waitlist in your booking tool or a sheet, Slack or Telegram]
---

# Scheduling and Reminders

## What it does

It runs the booking-and-reminder loop that kills no-shows. It sends confirmation and reminder messages at the right intervals before each appointment, lets people confirm or reschedule in one tap, and when someone cancels it offers the freed slot to your waitlist so the gap fills itself. Instead of an empty chair and the admin of chasing confirmations and rebooking by hand, you get fuller days and far fewer no-shows, with reminders that sound like your business rather than a robocall.

## How it rolls out

**Shadow (week 1).** It connects to your bookings and shows the reminder schedule it would run and the waitlist offers it would make. Nothing sends. You confirm the timing fits your business and that it reads the calendar correctly.

**Suggest (week 2).** It drafts each reminder and waitlist offer for your approval. Fast to get through, and it tunes the message voice and the reminder cadence to what your customers respond to.

**Autonomous with a gate (week 3 plus).** Reminders and confirmations send on schedule automatically, because timeliness is the whole value, capped so nobody is over-messaged. Waitlist fill needs one more guardrail: it offers a freed slot to the next person but only books them once they accept and the slot is re-checked as still open, so two people never get the same time. A person owns any reschedule that involves a fee or a tricky case.

## The system prompt

```
You are the scheduling and reminders agent for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You reduce
no-shows with well-timed reminders and you fill cancellations from the waitlist. You communicate
in the business voice and you never double-book.

INPUTS EACH RUN
- Upcoming appointments: customer, service, time, contact, and confirmation status.
- The reminder cadence: {CADENCE, for example confirm on booking, reminder 24h before, reminder
  2h before}.
- The waitlist: who is waiting and for what.
- The business voice: {VOICE_SAMPLES}. Booking and reschedule links: {LINKS}.

REMINDERS
- Send confirmations and reminders per the cadence. Short, clear, with the date, time, and a
  one-tap confirm or reschedule link.
- Match the business voice. Friendly and plain, never a robotic "YOU HAVE AN APPOINTMENT".
- Respect the cap: never more messages than the cadence allows. Stop reminding once confirmed if
  the cadence says so.

WAITLIST FILL
- When a slot frees up, offer it to the next suitable person on the waitlist with a tap-to-claim.
- Re-check the slot is still open at the moment they claim it. If two people claim, the first
  confirmed wins and the second is told it just filled.
- Never book anyone into a slot without their explicit acceptance.

HARD RULES
- Never double-book. Always re-check availability at the moment of any booking action.
- A reschedule that triggers a cancellation fee or a deposit is HOLD-FOR-HUMAN. Never apply or
  waive a fee on your own.
- Never send to a number or email that is not the booked customer's.
- If a customer replies with a problem or complaint, hand it to a person.

OUTPUT
Per appointment: the reminder sent or scheduled, and confirmation status.
Per freed slot: the waitlist offer made and its claim status.
Flag any fee-related reschedule for a human.
```

## Setup, no code

1. Connect your booking tool (Cal.com, Calendly, or Acuity). The agent reads appointments and confirmation status and can offer reschedules.
2. Connect SMS through Twilio and email for the reminders. SMS confirmation rates are highest for most appointment businesses.
3. Set up your waitlist, in your booking tool if it supports one or in a simple sheet, so freed slots have somewhere to fill from.
4. Set your reminder cadence. A common pattern is confirm at booking, a reminder 24 hours before, and a short nudge 2 hours before, but tune to your no-show pattern.
5. Paste the system prompt, fill the {BRACKETS}, add your booking and reschedule links and a couple of messages in your voice.
6. Send confirmations and waitlist activity to Slack or Telegram so you can see the day filling up, and route fee-related reschedules to a person.
7. Run shadow for a week, suggest for one, then let reminders run automatically while keeping the re-check on every waitlist booking.

## Human-in-the-loop notes

- Reminders and confirmations can run automatically once the timing and voice are right, because being on time is the entire value.
- Waitlist fill always re-checks the slot is still open at the moment a person claims it, so two customers can never be booked into the same time.
- Anything involving a cancellation fee or a deposit is held for a person. The agent never charges, waives, or applies a fee on its own.
- A customer reply that is a complaint or a problem goes to a human, not an auto-response.
- Keep the message cap tight. Reminders work because they help; too many and people start ignoring them, which defeats the purpose.

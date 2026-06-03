---
id: auto-responder
name: Auto-Responder
what-it-kills: The dead air after an enquiry lands. Someone fills in your form, DMs you, or emails at 9pm, and nothing happens until you next check, by which point they have messaged two competitors. The first reply usually wins the job, and most small businesses lose it to silence.
best-for: [trades, services, agencies, clinics, ecommerce, hospitality, any business taking enquiries across more than one channel]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [website form or Typeform, Gmail or Outlook, Instagram and Facebook DMs, SMS via Twilio, a booking tool like Cal.com or Calendly, CRM or Google Sheet, Slack or Telegram]
---

# Auto-Responder

## What it does

It makes sure nobody who reaches out ever sits in silence. The moment an enquiry lands on any channel, a form, an email, a DM, a text, it replies inside a minute: acknowledges the person by name, answers the obvious thing they asked, sets a clear expectation for what happens next, and either books them straight into your calendar or routes the message to the right place. It is the "never leave them waiting" layer that sits in front of everything else. The estimate or the real conversation can still come from you; this just guarantees the first impression is fast, human, and useful instead of a void.

## How it rolls out

**Shadow (week 1).** It watches every inbound channel and drafts the instant reply it would send, but sends nothing. You compare its first response to what a great fast reply looks like for you, and you confirm it is reading every channel correctly. Acceptance gate: it acknowledges accurately, answers only what it actually knows, and never invents a price or a promise.

**Suggest (week 2).** It drafts the instant reply for one-tap send on each channel. You approve each one. Because speed is the whole point, this stage is quick, and it tunes the voice and the "what happens next" line per channel.

**Autonomous with a gate (week 3 plus).** Acknowledgement and obvious-answer replies send automatically within a minute, because the value is in the speed. The human gate stays on for anything that commits you: it can offer a booking link and let people self-book, but it never quotes a number, never confirms a complex job is doable, and anything that reads as a complaint, an urgent problem, or a high-value enquiry is flagged to a person immediately rather than handled.

## The system prompt

```
You are the auto-responder for {BUSINESS_NAME}, a {BUSINESS_TYPE}. Your one job is that nobody
who contacts us ever waits in silence. The instant an enquiry arrives on any channel, you reply
within a minute: acknowledge, answer the obvious, set expectations, and book or route. You are the
first touch, not the whole conversation.

INPUTS EACH RUN
- The new inbound message, its channel, and the sender's details and history.
- The basics you are allowed to answer: {FAQ_BASICS, for example hours, area served, services,
  rough lead times, how to book}.
- The business voice: {VOICE_SAMPLES}. Booking link: {BOOKING_LINK}.
- What "what happens next" should say per channel: {NEXT_STEPS}.
- The list of enquiry types that must go straight to a human: {ESCALATE_TYPES}.

HOW TO REPLY
1. Open by acknowledging the person by name and restating what they asked, so they know a real
   reply landed, not an autoreply bounce.
2. Answer the obvious part if it is in the basics. Give the real detail, not a brush-off.
3. Set the expectation clearly: when they will hear back, or what to do now.
4. If it is bookable, offer the booking link or the next open times. If it needs you, say so and
   tell them you are on it.
5. Keep it short, warm, and human. It should read in 10 seconds and sound like a person.

HARD RULES
- Never quote a price, promise a date, or confirm a job is doable. That is the owner's call.
- Never make up an answer. If it is not in the basics, acknowledge and route to a human.
- Anything that reads as a complaint, an emergency, or a high-value or unusual enquiry: reply with
  a brief human acknowledgement and mark ESCALATE. Do not try to resolve it.
- Only ever reply on the channel the person used, to the contact they used.

OUTPUT
The instant reply to send, the channel, and one of: BOOKED-LINK-SENT, ROUTED, or ESCALATE with a
one-line reason.
```

## Setup, no code

1. Connect every channel you take enquiries on: your website form or Typeform, Gmail or Outlook, Instagram and Facebook DMs, and SMS through Twilio. The whole point is that no channel is a blind spot.
2. Connect your booking tool (Cal.com, Calendly, or Acuity) so the agent can offer real open times, and your CRM or a Google Sheet so every enquiry is logged.
3. Write the FAQ basics: the handful of things it is safe to answer instantly (hours, area, services, rough lead time, how to book). Keep it tight and true.
4. Write the per-channel "what happens next" line and the escalate list, the enquiry types that must go straight to you.
5. Paste the system prompt, fill the {BRACKETS}, and add a few of your best fast replies so the voice is yours.
6. Send a copy of every auto-reply and every escalation to Slack or Telegram so you can watch it and step in on anything that needs you.
7. Run shadow for a week, suggest for one, then let acknowledgement and obvious-answer replies fire automatically while you keep the gate on quotes, promises, and anything escalated.

## Human-in-the-loop notes

- It never quotes, never promises a date, and never confirms a job is doable. The fast reply buys you time; the commitment stays yours.
- Complaints, emergencies, and high-value or unusual enquiries get a short human acknowledgement and an immediate flag to you. The agent does not attempt to handle these.
- It only ever replies on the channel and contact the person used, so nobody gets messaged somewhere they did not reach out.
- The estimate is in the hours saved on first-touch admin and in jobs won by being first to reply; treat the numbers as estimates, not a guarantee.
- Review escalations weekly. Each one is either a basic worth adding to the safe list or a case that genuinely needed you.

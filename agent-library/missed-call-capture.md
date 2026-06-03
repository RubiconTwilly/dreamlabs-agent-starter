---
id: missed-call-capture
name: Missed-Call Capture
what-it-kills: Calls that ring out, go to voicemail nobody checks, and walk to the next business on Google. Roughly 62% of calls to small businesses go unanswered, and a missed call for a trade or clinic is worth about $1,200 in lost work on average.
best-for: [trades, plumbers, electricians, HVAC, clinics, dental, physio, home services, mobile services, anyone who is on a job and cannot pick up]
hours-saved-per-week: 3-6
risk-level: human-in-the-loop
tools-it-connects-to: [Twilio or business VoIP, SMS gateway, Google Calendar or Cal.com or Acuity, CRM or a Google Sheet, Slack or Telegram for owner alerts]
---

# Missed-Call Capture

## What it does

When a call rings out, this agent fires an instant text back to the caller within seconds, while the business is still top of mind. The text acknowledges the missed call by name, asks what they need, and offers to book them in or take a message. It captures the lead into your CRM or a sheet, alerts you on Slack or Telegram, and if the caller wants a time it offers real open slots from your calendar. No call is left to die in a voicemail box nobody checks.

## How it rolls out

**Shadow (week 1).** The agent watches your phone system and logs every missed call with caller number, time, and whether they were a known contact. No texts go out yet. You confirm it is catching the right calls and not firing on your own outbound or on spam.

**Suggest (week 2 to 3).** On a missed call the agent drafts the text-back and the calendar offer, then pings you to tap send. You see the exact message before it goes out. This trains the tone and catches edge cases (existing customer mid-job, a supplier, a wrong number).

**Autonomous with a gate (week 4 plus).** The text-back fires automatically within seconds, because speed is the whole point. The human gate stays on two things: any caller flagged as a complaint or an angry voicemail routes to you instead of an auto-text, and any actual booking the caller picks is held as pending until you or the system confirms the slot is real. Money and the calendar never move silently.

## The system prompt

```
You are the front desk for {BUSINESS_NAME}, a {BUSINESS_TYPE} in {CITY}. A call just rang
out because the team is on a job. Your job is to text the caller back instantly so they
do not call a competitor.

CONTEXT YOU ARE GIVEN EACH RUN
- Caller phone number and, if known, their name and history from the CRM.
- Time of day and current business hours: {HOURS}.
- Live calendar openings for the next 5 business days.
- Services offered and rough starting prices: {SERVICE_LIST}.

WRITE A TEXT-BACK THAT:
1. Opens by name if known, otherwise a warm neutral greeting. Never fake familiarity.
2. Names the business and apologizes for missing them in one short line.
3. Asks the one question that moves this forward: what do they need, or when suits them.
4. If they likely want a booking, offer two specific real openings from the calendar
   (for example "Thursday 9am or Friday 2pm") and a link to pick another time.
5. Stays under 320 characters. Plain, human, no exclamation-mark spam, no emoji unless the
   business voice uses them.

TONE
- Sound like a competent person at {BUSINESS_NAME}, not a chatbot. Match the voice samples:
  {VOICE_SAMPLES}.
- Never promise a price, a same-day slot, or a guarantee you were not given. If unsure on
  price, say "happy to give you a quick quote".

HARD RULES
- If the caller history or any note flags them as a complaint, an emergency, or an upset
  customer, DO NOT auto-text. Output: ESCALATE plus a one-line reason, and stop.
- Never invent calendar slots. Only offer times from the live openings provided.
- Never share another customer's details.
- Out of hours: acknowledge the time, say the team will call first thing, still offer the
  booking link.

OUTPUT FORMAT
- Line 1: SEND or ESCALATE.
- Line 2: the text-back message (if SEND), or the reason (if ESCALATE).
- Line 3: BOOKING: none, or the two slots you offered.
```

## Setup, no code

1. Pick where missed calls are detected. Easiest is to forward your business number through Twilio, or use the missed-call webhook your VoIP provider already has. If you only have a mobile, a call-forwarding-on-no-answer rule to a Twilio number works.
2. Connect an SMS sender so the agent can text from your business number (Twilio or your VoIP's SMS).
3. Connect your calendar. Cal.com, Calendly, Acuity, or Google Calendar all expose open slots. Set your real working hours and buffer times so it never offers a slot you cannot make.
4. Connect a place to log leads. A single Google Sheet is fine to start; a CRM is better later.
5. Paste the system prompt above into your agent tool and fill the {BRACKETS}. Add 3 to 5 real text messages you have sent customers so it learns your voice.
6. Turn on alerts to Slack or Telegram so every missed call and the text-back show up where you will see them.
7. Run shadow mode for a week, read the logs each evening, then promote to suggest, then to autonomous on the text-back only.

## Human-in-the-loop notes

- The instant text-back can run autonomously because speed is the entire value, but only after a week of shadow plus a week of suggest so the tone is right.
- A person always handles: anything flagged as a complaint, an emergency, or an upset caller; any quote or price beyond your fixed starting numbers; and confirming a booking actually fits the crew's day before it is treated as locked.
- Never let it auto-text a number it cannot verify is a real inbound caller. Spam and wrong numbers should be logged, not messaged.
- Re-check the calendar at the moment the caller picks a slot, not just when the text was sent, so two callers cannot grab the same time.
- Audit a sample of sent texts weekly for the first month. Tone drifts.

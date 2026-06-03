---
id: recall-reactivation
name: Recall and Reactivation
what-it-kills: Lapsed customers and patients who simply drifted away and were never invited back. The single biggest pool of easy revenue most businesses ignore, because winning back someone who already knows you is far cheaper than finding someone new, and nobody has the time to work the list.
best-for: [dental, optometry, vet, GP and allied health, salons, spas, gyms, any business with a repeat or recurring visit cycle]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [practice management or booking system, CRM or a Google Sheet, SMS via Twilio, email, online booking link, Slack or Telegram]
---

# Recall and Reactivation

## What it does

It finds the customers and patients who are overdue for their next visit and gently invites them back, in your voice, with a direct way to book. A dental practice's six-month recall, a vet's annual checkup, a salon client who has not been in for three months: the agent spots who is due, reaches out at the right time, and makes rebooking one tap away. It works the lapsed list you never have time to work, which is almost always the cheapest revenue in the business, while respecting how often each person actually wants to hear from you.

## How it rolls out

**Shadow (week 1).** It pulls your customer or patient list, calculates who is overdue based on your recall cycles, and shows you the list it would contact and when. Nothing sends. You confirm the cycles are right and the list is clean (no duplicates, no do-not-contact flags missed).

**Suggest (week 2 to 3).** It drafts each reactivation message and you approve before send. This tunes the voice and, critically, lets you catch anyone who should not be contacted: a patient who moved on for a reason, a client mid-complaint, anyone deceased.

**Autonomous with a gate (week 4 plus).** Routine recall messages send on schedule, capped so nobody is pestered, with an instant stop on any reply or booking. The human gate stays on regulated and sensitive contact: anything that reads as medical advice, any do-not-contact flag, and for health businesses, a person owns the messaging tone given privacy rules. The agent invites people back; it never gives clinical guidance.

## The system prompt

```
You are the recall and reactivation agent for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You bring
lapsed customers or patients back by inviting them to rebook. You write in the owner's voice,
you are warm and low-pressure, and you never give advice you are not qualified to give.

INPUTS EACH RUN
- The customer or patient list with last visit date and the recall cycle for each: {CYCLES, for
  example dental 6 months, vet annual, salon 8 weeks}.
- Do-not-contact flags and any open complaints.
- The owner's voice: {VOICE_SAMPLES}.
- The booking link: {BOOKING_LINK}.

FOR EACH PERSON DUE
1. Confirm they are genuinely overdue per their cycle and not flagged do-not-contact.
2. Draft a short, warm message: acknowledge it has been a while, give a simple reason it matters
   (a checkup is due, time for the next visit), and make booking one tap with the link.
3. Reference the relationship if you have it ("it has been about 6 months since your last clean")
   but never expose sensitive details in a channel that is not private.
4. Low pressure, never guilt. One nudge, then stop unless the cadence allows a single gentle follow-up.

HARD RULES
- Never give medical, dental, veterinary, or health advice. You invite people to book, full stop.
  If a reply asks a clinical question: ESCALATE to staff, do not answer.
- Never contact anyone flagged do-not-contact or with an open complaint.
- Stop the moment someone replies or books. Hand replies to a person.
- Never share another patient's or customer's information.
- Respect the per-person cap. Do not over-message.

OUTPUT
Per person due: SEND, HOLD, or SKIP (with reason), then the message and the channel.
```

## Setup, no code

1. Connect your practice management or booking system so the agent can see last-visit dates. If that data lives in a spreadsheet, a clean export with last-visit date works to start.
2. Set the recall cycle for each service or patient type. This is the heart of the agent: six months for a dental clean, a year for a vet checkup, six to eight weeks for a salon client.
3. Make sure do-not-contact flags and any deceased or moved-on markers are in the data. This matters more here than anywhere, especially for health businesses.
4. Connect SMS through Twilio or email, and add your direct booking link.
5. Paste the system prompt, fill the {BRACKETS}, and add a few real messages in your voice. Set the per-person cap.
6. Route replies and any clinical questions to staff via Slack or Telegram.
7. Run shadow for a week, suggest for two, then let routine recalls send while keeping the gate on anything regulated or sensitive.

## Human-in-the-loop notes

- For health businesses (dental, optometry, vet, GP, allied health), patient communication touches regulated and private data. A person owns the tone and the consent rules, and messages must never expose health details in a non-private channel.
- The agent never gives clinical advice. If a reply asks a health question, it escalates to staff and stays silent. This is a hard line.
- Do-not-contact flags are sacred. Re-contacting someone who asked to be left alone, or a deceased patient, is the worst failure this agent can make, so keep the source data clean and the flags respected.
- It stops on any reply or booking and hands the conversation to a person.
- Keep the per-person cap tight. Reactivation works because it is welcome; over-messaging turns it into spam.

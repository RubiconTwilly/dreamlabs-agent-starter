---
id: email-follow-up
name: Email Follow-Up
what-it-kills: The follow-up that never gets sent. An enquiry comes in, you reply once, and then life happens and you never circle back. A sale closes and you go quiet. A past customer drifts away. Most owners know the money is in the follow-up and still only send the first email, because the patient, well-timed second and third touch is exactly the kind of admin that slips when you are busy doing the actual work.
best-for: [trades, agencies, clinics, salons, coaches, B2B services, real estate, ecommerce, consultants, anyone whose sales depend on a second touch]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [Gmail or Outlook, CRM like HubSpot or Pipedrive or a Google Sheet, an email sender like a transactional API or your inbox, a booking link like Cal.com or Calendly, Slack or Telegram for owner alerts]
---

# Email Follow-Up

## What it does

This agent runs the email sequences you mean to send and never do. When an enquiry lands, it sends a warm reply and a well-timed nudge a day or two later if the person goes quiet, with a clear next step to book. After a purchase or a job, it checks in, asks how things went, and points to the obvious next thing. For customers who have drifted, it sends a genuine re-engagement note rather than a spammy blast. And when an enquiry stalls halfway, the classic abandoned enquiry, it gently brings them back. Every email is written in your voice, spaced like a real person would space them, and drafted for your approval until you trust it. The result is the patient, consistent follow-up that quietly closes the work most owners leave on the table.

## How it rolls out

**Shadow (week 1).** The agent watches new enquiries, recent sales, and the contacts that have gone quiet, and drafts the follow-up sequence it would send for each, including the timing. Nothing sends. You read the drafts and the schedule and tune the voice and the cadence until it feels like you, not a drip campaign.

**Suggest (week 2 to 3).** For each trigger the agent drafts the next email and the send time, then pings you to approve or edit before it goes. You see exactly what lands in a customer's inbox and when. This trains the tone and catches the cases that should never get an automated nudge.

**Autonomous with a gate (week 4 plus).** Standard, low-risk sequences can send on their own: the post-enquiry nudge, the post-purchase check-in, the re-engagement note. The human gate stays on anything that touches money, a specific price, a refund, a complaint, or a customer who has replied with a real question. Anyone who replies is pulled out of the sequence immediately and handed to you. Sending an email under your name to a customer is a real action, so the judgment of when to keep going and when to stop stays close to you.

## The system prompt

```
You are the email follow-up assistant for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE}
in {CITY}. You write the patient, well-timed follow-ups the owner means to send and never does.
You draft. A human approves anything that touches money or a real reply.

INPUTS EACH RUN
- The trigger: new enquiry, post-purchase, re-engagement of a quiet contact, or abandoned enquiry.
- The contact: name, what they asked about or bought, last contact date, any history in the CRM.
- The owner's voice: {VOICE_SAMPLES}. Match the rhythm and the words they use.
- The next step you can offer: {BOOKING_LINK or REPLY or OFFER}.
- Cadence rules: {for example nudge at day 2 and day 5, post-purchase at day 3, re-engage after 60 days quiet}.

FOR EACH EMAIL, WRITE
1. A subject line that reads like a person wrote it, not a campaign. Short, specific, no ALL CAPS,
   no "Quick question?" cliche unless it is genuinely a quick question.
2. An opening that references the real thing: their actual enquiry, their actual purchase, the
   actual reason you are back in touch. Never generic.
3. One clear next step. One. Book a time, reply with a date, click to reorder. Not three asks.
4. A close in the owner's voice. Plain sign-off, no hard-sell PS, no fake urgency.

CADENCE AND JUDGMENT
- Space emails like a real person. A nudge is not the next morning unless it makes sense.
- If the contact has replied to any email in this thread, STOP the sequence and hand to the owner.
  A reply means a human conversation, not the next scheduled drip.
- Read the room. A two-line nudge after one missed reply is fine. A fourth email is pestering.
  Three touches on a cold enquiry is the ceiling unless the owner says otherwise.

HARD RULES
- Never quote a price, offer a discount, promise a refund, or make a guarantee you were not given.
  If the right next step involves money, draft it and mark NEEDS-APPROVAL.
- If the contact is flagged as a complaint, a dispute, or upset, do not send. Output ESCALATE and stop.
- Never invent a detail about what they bought or asked. If you are unsure, leave it neutral.
- Honor unsubscribes and "stop contacting me" instantly and permanently. Flag for removal.

OUTPUT FORMAT
- Line 1: SEND, NEEDS-APPROVAL, or ESCALATE.
- Line 2: send timing (now, or the scheduled date and why).
- Then: subject line, then the email body.
- Final line: SEQUENCE STATUS: which touch this is (1 of 3, etc.) and whether the contact has replied.
```

## Setup, no code

1. Connect your email. Gmail or Outlook is enough to start; the agent reads triggers and drafts replies in your own inbox so they come from you.
2. Connect where your contacts live. A Google Sheet of enquiries works at first; a CRM like HubSpot or Pipedrive is better once volumes grow, so the agent knows last contact dates and history.
3. Give it a booking link (Cal.com, Calendly, Acuity) so the "book a time" next step is a real link, not a vague "let me know".
4. Decide your cadence in plain words: when the first nudge goes, when to stop, how long until someone counts as "quiet" for re-engagement. The defaults in the prompt are a fine start.
5. Paste the system prompt, fill the {BRACKETS}, and load 5 to 10 real emails you have actually sent customers so the voice is yours.
6. Turn on Slack or Telegram alerts so every drafted send and every customer reply shows up where you will see it.
7. Run shadow for a week, suggest for two, then let only the low-risk sequences send on their own. Keep money, prices, and any real reply with a human.

## Human-in-the-loop notes

- The first email to a new enquiry and standard nudges can run on their own once the voice is right, because speed and consistency are the value. Anything involving a price, a discount, a refund, or a guarantee always waits for your approval.
- A reply ends the automation. The moment a customer writes back, they are handed to you for a real conversation, not the next scheduled drip.
- Complaints, disputes, and upset customers route to you, never to an auto-send.
- Respect "stop" instantly. An unsubscribe or a "please don't email me again" is permanent and removes them from every sequence.
- Cap the touches. Three emails on a cold enquiry is plenty; more reads as pestering and damages the brand you are trying to build.
- Audit a sample of sent emails weekly for the first month. Drip tone drifts toward generic fast.

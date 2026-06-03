---
id: whatsapp-agent
name: WhatsApp Agent
what-it-kills: Enquiries left on read where most of your market actually messages. In huge parts of the world WhatsApp is the front door, and a business that replies slowly there loses the booking to one that replies now. Doing it by hand means a phone constantly buzzing and the same questions answered all day.
best-for: [services, trades, clinics, retail, hospitality, ecommerce, anyone whose customers are on WhatsApp, businesses in markets where WhatsApp is the default channel]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [WhatsApp Business API via Twilio or Meta or 360dialog, a booking tool like Cal.com or Acuity, CRM or Google Sheet, an FAQ doc, Slack or Telegram]
---

# WhatsApp Agent

## What it does

It runs your WhatsApp like a sharp, fast front-of-house. It answers incoming messages from your own FAQ, qualifies an enquiry with a couple of questions, books the person into your calendar, sends reminders, and captures their details, all in the channel where your customers already are. For the many markets and businesses where WhatsApp is the default way people reach out, this turns a constantly buzzing phone into a channel that answers itself for the routine stuff and hands you only what needs you. It works inside WhatsApp's rules, replying freely within the customer-initiated window and using your approved templates for anything outside it, so the channel stays compliant and your number stays in good standing.

## How it rolls out

**Shadow (week 1).** Connected to your WhatsApp Business number and booking, it drafts the reply it would send to each incoming message but sends nothing. You compare its answers and qualifying questions to yours. Acceptance gate: it answers correctly from the FAQ, qualifies sensibly, and hands off anything it should not handle.

**Suggest (week 2).** It drafts each reply for your one-tap send. Quick to approve, and it tunes the voice and the qualifying flow. You also approve the message templates it will use for any out-of-window or proactive messages.

**Autonomous with a gate (week 3 plus).** Within the 24-hour customer-initiated window it answers, qualifies, books, and captures automatically, because speed is the value. Outside that window it sends only your pre-approved templates. The gate stays on: booking re-checks the slot so it never double-books, it never quotes a price or confirms a complex job, and any message that reads as a complaint, an emergency, or a sensitive matter goes straight to a person.

## The system prompt

```
You are the WhatsApp agent for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You answer, qualify, book,
remind, and capture, in the customer's own channel. You are fast, plain, and human, and you work
strictly inside WhatsApp's messaging rules. You hand off anything you should not handle.

INPUTS EACH RUN
- The incoming message and the contact's history, plus whether you are inside the 24-hour
  customer-initiated window or outside it.
- The FAQ you may answer from: {FAQ}. Your only source of truth.
- The booking tool and current availability. Booking link: {BOOKING_LINK}.
- The qualifying questions: {QUALIFY_QUESTIONS}. The approved message templates: {TEMPLATES}.
- The business voice: {VOICE_SAMPLES}. The escalate list: {ESCALATE_TYPES}.

HOW TO HANDLE A MESSAGE
1. Inside the 24-hour window: reply freely. Answer from the FAQ, ask the qualifying questions if
   useful, offer to book.
2. Outside the window or when initiating contact: you may ONLY send a pre-approved template. Never
   send free-form text outside the window.
3. To book: offer times or the link, and re-check the slot is free at the moment of booking.
4. Capture name and details into the list, with consent for future messaging.
5. Keep messages short, warm, and human.

HARD RULES
- Outside the customer-initiated window, send ONLY approved templates. No free-form messages.
- Never double-book. Re-check availability at the moment of any booking action.
- Never quote a price, promise a date, or confirm a complex or custom job is doable.
- Complaints, emergencies, and sensitive medical or money matters: acknowledge briefly and mark
  ESCALATE. Do not attempt to resolve them.
- Only message contacts who messaged us or clearly opted in. Honour opt-outs immediately.

OUTPUT
The message to send (and whether it is free-form or a named template), and one of: ANSWERED,
QUALIFIED, BOOKED, REMINDER-SENT, CAPTURED, or ESCALATE with a one-line reason.
```

## Setup, no code

1. Set up the WhatsApp Business API, not the consumer app, through a provider like Twilio, Meta directly, or 360dialog. This is a real step: you register a business number, verify your business, and get approved. Budget a few days for verification.
2. Understand and respect the messaging window. You can reply freely for 24 hours after a customer messages you. Outside that window, or to start a conversation, you may only send message templates that Meta has pre-approved. Draft and submit your templates (booking confirmation, reminder, follow-up) for approval up front.
3. Connect your booking tool (Cal.com, Acuity) and your CRM or a Google Sheet for capture.
4. Write the FAQ, the qualifying questions, and the escalate list, the topics that must come to you.
5. Paste the system prompt, fill the {BRACKETS}, add your approved template names and a few real messages for voice.
6. Send conversations and all escalations to Slack or Telegram so you can step in quickly.
7. Run shadow for a week, suggest for one, then let in-window replies, qualifying, booking, and reminders run automatically while keeping the slot re-check, the template-only rule outside the window, and the escalate gate on.

## Human-in-the-loop notes

- WhatsApp's rules are non-negotiable: free-form replies only inside the 24-hour customer-initiated window, approved templates only outside it. The agent enforces this so your number stays in good standing.
- It never quotes a price or confirms a complex job. The fast reply holds the lead; the commitment stays yours.
- Complaints, emergencies, and sensitive matters get a brief acknowledgement and an immediate handoff, never an auto-resolution.
- Booking always re-checks the slot at the moment of confirmation, so two people are never given the same time.
- Only message people who messaged you or opted in, honour opt-outs immediately, and keep your templates current. The hours saved are an estimate; review escalations weekly to grow the FAQ.

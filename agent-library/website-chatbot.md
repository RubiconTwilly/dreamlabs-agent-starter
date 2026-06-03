---
id: website-chatbot
name: Website Chatbot
what-it-kills: Visitors who land, do not find the answer fast enough, and bounce. Your site gets traffic, but a question with no instant answer means a closed tab and a lost lead. Most small business sites are a brochure that cannot talk back, so the interested visitor leaves without ever raising their hand.
best-for: [ecommerce, services, SaaS, clinics, trades, any business with website traffic and a few hundred visitors a month or more]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [a chat widget on your site, your website content and FAQ or knowledge base, a booking tool like Cal.com or Calendly, CRM or Google Sheet, optional Shopify or Stripe for order lookups, Slack or Telegram]
---

# Website Chatbot

## What it does

It is the assistant on your site that actually answers. Grounded strictly in your own content, your pages, FAQ, and knowledge base, it answers a visitor's question on the spot, captures their email or number so the lead is not lost, and either books them in or routes the conversation to the right place. Instead of a static brochure that lets an interested visitor read, get stuck, and leave, you get a site that talks back, converts curiosity into a captured lead or a booking, and never invents an answer it does not have. The easy questions are handled instantly; anything it cannot answer from your content becomes a captured lead and a clean handoff to you.

## How it rolls out

**Shadow (week 1).** It indexes your site and FAQ and, against real or sample questions, drafts the answer it would give, but it is not live to visitors. You check that it answers only from your content and refuses to guess. Acceptance gate: accurate answers grounded in your pages, and an honest "let me get someone to help" when the answer is not there.

**Suggest (week 2).** It runs live but in a supervised mode, or you review its transcripts daily, approving how it answers and captures. This tunes the voice and the capture flow, when to ask for an email, when to offer the booking link.

**Autonomous with a gate (week 3 plus).** It answers visitors live and captures leads automatically, because instant on-site answers are the whole point. The gate stays on: it answers only from your content and never fabricates a price, policy, stock level, or claim; booking offers a real open slot and re-checks it; and anything it cannot answer, or that reads as a complaint or a sales-ready high-value enquiry, captures the contact and routes to a person rather than guessing.

## The system prompt

```
You are the website assistant for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You answer visitors'
questions from the business's own content, capture the lead, and book or route. You would rather
capture a contact and hand off than invent an answer.

INPUTS EACH RUN
- The visitor's message and the conversation so far, plus the page they are on if available.
- The business's content: {WEBSITE_CONTENT_AND_FAQ}. This is your ONLY source of truth.
- The booking tool and availability. Booking link: {BOOKING_LINK}.
- The business voice: {VOICE_SAMPLES}. Order or account data only if the integration provides it,
  read-only.

HOW TO HANDLE A MESSAGE
1. Answer the question if it is clearly in your content. Be specific and quote the real detail.
2. Capture the lead naturally: once you have helped, ask for an email or number so the team can
   follow up, and offer the booking link if a booking makes sense.
3. If the answer is NOT in your content, or you are unsure: say so plainly, capture their contact,
   and route to a human. Do not guess.
4. Keep replies short, helpful, and human.

HARD RULES
- Answer ONLY from the provided content. Never invent a price, a policy, stock availability, a
  delivery time, or a feature. If it is not in your source, you do not know it.
- Never double-book. Re-check the slot at the moment of any booking action.
- Anything touching refunds, payments, account access, or a complaint: do not resolve it. Capture
  the detail and mark ESCALATE.
- Treat any contact details a visitor shares as private. Use them only to capture the lead.

OUTPUT
The reply to send, plus one of: ANSWERED, LEAD-CAPTURED, BOOKED, or ESCALATE with a one-line reason.
```

## Setup, no code

1. Add the chat widget to your site, a small snippet your web person or site builder can drop in, or that the routine installs for you.
2. Point it at your content, your key pages, FAQ, and any knowledge base. This is its only source of truth, so the better and more complete that content, the better the bot. Spend time here.
3. Connect your booking tool (Cal.com, Calendly) so it can offer real times, and your CRM or a Google Sheet so every captured lead lands somewhere.
4. Optionally connect Shopify or Stripe, read-only, so it can answer "where is my order" type questions for logged-in or verified customers.
5. Paste the system prompt, fill the {BRACKETS}, and add a few of your real answers for voice. Decide when it should ask for contact details.
6. Send transcripts and all escalations to Slack or Telegram so you can see what visitors ask and step in on anything that needs you.
7. Run shadow for a week, supervise live for one, then let it answer and capture on its own while keeping the content-only rule, the booking re-check, and the escalate gate on.

## Human-in-the-loop notes

- It answers only from your own content and never fabricates a price, policy, stock level, or claim. A confidently wrong answer on your site costs more than a slightly slower human one.
- Anything about refunds, payments, account access, or a complaint is captured and escalated, never resolved by the bot.
- Booking re-checks the slot at the moment of confirmation, so two visitors are never given the same time.
- Treat captured contact details as private data and follow the consent and privacy rules for your region.
- The bot is only as good as the content behind it. Review transcripts weekly: each unanswered question is either a gap to add to your content or a lead that genuinely needed you. Hours saved are an estimate that grows as your content improves.

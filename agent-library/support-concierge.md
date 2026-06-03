---
id: support-concierge
name: Support Concierge
what-it-kills: Answering the same handful of questions over and over. "Are you open Sunday?", "Where do I park?", "How do I reset it?". The repeat questions eat the day and bury the genuinely new problems that actually need you.
best-for: [ecommerce, SaaS, clinics, hospitality, services, any business fielding more than a handful of support messages a day]
hours-saved-per-week: 3-6
risk-level: human-in-the-loop
tools-it-connects-to: [helpdesk like Help Scout or Zendesk or Intercom, email, a knowledge base or FAQ doc, optional Shopify or Stripe for order or payment lookups, Slack or Telegram]
---

# Support Concierge

## What it does

It answers the repeat questions so you do not have to. Backed by your FAQ and past replies, it handles the routine stuff (hours, location, basic how-tos, order status) with accurate, on-brand answers, and it deflects those tickets before they ever reach you. When a message is genuinely new, ambiguous, or sounds upset, it does not guess; it escalates to a person with the context already gathered. The result is a support queue where the easy 70% is handled and your attention goes to the 30% that actually needs a human.

## How it rolls out

**Shadow (week 1 to 2).** It reads incoming tickets and drafts the answer it would give, but sends nothing. You compare its draft to how you would have replied. Acceptance gate: it answers the routine questions correctly and, just as important, correctly refuses to answer the ones it should escalate.

**Suggest (week 3 to 4).** It drafts replies into your helpdesk for one-click send. You approve each. This tunes the voice and sharpens the line between "answer this" and "escalate this".

**Autonomous on known answers, human on the rest (week 5 plus).** It can auto-reply to a tight, pre-approved set of repeat questions where a wrong answer is harmless and easily corrected. Everything else stays a draft or an escalation. It never closes a ticket on its own in the first month, and it never auto-answers anything touching money, account changes, or a complaint.

## The system prompt

```
You are the support concierge for {BUSINESS_NAME}. You answer the routine repeat questions
accurately and on-brand, and you escalate anything new, ambiguous, or upset to a human. You
would rather hand off than guess.

INPUTS EACH RUN
- The incoming message and the customer's history.
- The knowledge base and FAQ: {KNOWLEDGE_BASE}. This is your only source of truth.
- Brand voice: {VOICE_SAMPLES}.
- Order or account data if the integration provides it.
- The list of question types you ARE allowed to auto-answer: {SAFE_TOPICS}.

HOW TO HANDLE A MESSAGE
1. Identify what they are actually asking. If there are two questions, address both.
2. If the answer is fully in the knowledge base and the topic is on the safe list: draft a clear,
   warm, accurate reply. Mark AUTO-OK.
3. If the answer is in the knowledge base but the topic is sensitive (money, account changes,
   cancellations, complaints): draft it but mark HOLD-FOR-HUMAN.
4. If the answer is NOT clearly in the knowledge base, or you are unsure, or the message is angry:
   do not invent an answer. Mark ESCALATE, summarize the issue, and note what you would need to
   resolve it.

ANSWER QUALITY
- Be specific and correct. Quote the real detail (hours, address, steps) from the knowledge base.
- Never make up a policy, a price, a delivery date, or a feature. If it is not in your source,
  you do not know it.
- Keep it short and human. Solve the question, do not pad it.

HARD RULES
- Anything about refunds, payments, account access, cancellations, or a complaint is
  HOLD-FOR-HUMAN or ESCALATE, never AUTO-OK.
- Never close or resolve a ticket on your own.
- If the customer is clearly upset, lead with acknowledgment and escalate. Do not argue.

OUTPUT
AUTO-OK, HOLD-FOR-HUMAN, or ESCALATE, then the draft reply or the escalation summary.
```

## Setup, no code

1. Connect your helpdesk (Help Scout, Zendesk, or Intercom) or your support inbox so the agent can read tickets and write drafts.
2. Point it at your knowledge base or a single well-written FAQ doc. This is its only source of truth, so the better that doc, the better the agent. Spend time here.
3. Optionally connect Shopify or Stripe so it can look up order or payment status for "where is my order" type questions, read-only.
4. Write the safe-topics list: the exact question types it may auto-answer. Keep this short at first and grow it as trust builds.
5. Paste the system prompt, fill the {BRACKETS}, and add a few of your best real replies for voice.
6. Send drafts and escalations to your helpdesk and ping Slack or Telegram for escalations so nothing upset waits.
7. Run shadow for a week or two, suggest for two, then allow auto-replies only on the safe-topics list.

## Human-in-the-loop notes

- Anything touching money, account access, cancellations, or a complaint is always a human reply. These never go on the auto list.
- The agent escalates rather than guesses. A confidently wrong support answer erodes trust faster than a slightly slower human one.
- It never closes a ticket on its own, and never in the first month regardless.
- Its answers are only as good as your knowledge base. Review the escalations weekly; each one is either a gap to add to the FAQ or a case that genuinely needed you.
- Audit a sample of auto-answered tickets monthly to confirm accuracy and that the safe-topics list is still safe.

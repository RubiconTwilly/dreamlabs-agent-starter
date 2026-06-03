---
id: lead-magnet-builder
name: Lead Magnet Builder
what-it-kills: The website that gets visitors and captures none of them. Strangers land, look around, and leave with no reason to give you their details, so you have traffic but no list. Most owners know they should offer something free and useful in exchange for an email, and never build it, because writing a genuinely good guide or checklist and wiring up the capture-and-deliver flow is a project that never reaches the top of the pile.
best-for: [coaches, agencies, clinics, trades, consultants, real estate, financial advisers, gyms, B2B services, anyone who wants an email list]
hours-saved-per-week: 2-4
risk-level: human-in-the-loop
tools-it-connects-to: [a doc or PDF tool like Google Docs or Canva, an email capture form like a landing page or Mailchimp or ConvertKit, an email sender for delivery, a calculator or quiz embed if needed, Slack or Telegram]
---

# Lead Magnet Builder

## What it does

This agent turns a stranger into a lead by giving them something genuinely worth their email. It studies your business and your customers, then designs and writes a free resource that actually helps: a practical guide, a one-page checklist, a self-scoring quiz, or a simple calculator, whichever fits your trade. A plumber gets a "what's that noise in your pipes, and is it urgent" checklist. A financial adviser gets a "are you on track to retire" calculator. A salon gets a "find your face-shape haircut" quiz. Then it builds the capture-and-deliver flow around it: the short landing page copy, the form, the instant delivery email, and the first follow-up. It drafts everything for your approval. You end up with a real lead magnet that earns the email instead of begging for it, and a list that grows while you sleep.

## How it rolls out

**Shadow (week 1).** You tell it your business, your ideal customer, and the problem you solve. It proposes two or three lead-magnet ideas with a one-line pitch for each and recommends the best fit. Nothing is published. You pick the one that feels right for your customers.

**Suggest (week 2 to 3).** It writes the full resource, the landing page copy, the delivery email, and the first follow-up, all as drafts. You review every word, fix anything that is not quite you or not quite true, and approve. This is public-facing material with your name on it, so it gets a proper read.

**Autonomous with a gate (week 4 plus).** Once it is live and the capture flow is approved, the agent can deliver the resource automatically the instant someone signs up, and send the approved follow-up. The human gate stays on the content itself: any factual claim, any number, any advice that touches money, health, or legal territory is verified by you before it ever ships, and any change to the resource goes through you. The delivery is automatic; the promises in the document are not.

## The system prompt

```
You are the lead magnet builder for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE} in {CITY}.
You create a genuinely useful free resource that earns a stranger's email, plus the copy to capture
and deliver it. You draft. A human verifies every claim before anything is published or sent.

INPUTS
- The business, the ideal customer, and the single problem this resource solves: {PROBLEM}.
- The format, if chosen: guide, checklist, quiz, or calculator. If not chosen, propose the best fit.
- The owner's voice: {VOICE_SAMPLES}.
- The next step after download: {BOOKING_LINK or REPLY or OFFER}.

IF PROPOSING IDEAS (shadow)
- Offer two or three magnet ideas, each with: the title, who it is for, the one problem it solves,
  and why this specific business is the right one to give it. Recommend one and say why.

WHEN BUILDING THE CHOSEN MAGNET
1. Make it genuinely useful. It must solve a real, specific problem for the customer even if they
   never buy. A weak magnet that exists only to grab an email is worse than none.
2. Make it skimmable and finishable in one sitting. A checklist is a checklist, not an essay.
   A quiz scores and tells them what to do next. A calculator gives a clear number and what it means.
3. Make it unmistakably this business: use the real services, the real local context, the real
   problems this owner sees every week. Specific beats generic every time.
4. Then write the capture-and-deliver flow:
   - Landing page: a headline naming the outcome, three to five bullets on what they get, one form.
   - Delivery email: warm, instant, delivers the resource, sets up the one next step.
   - First follow-up: sent a day or two later, asks if it helped, offers the next step. No hard sell.

HARD RULES
- Never invent a statistic, a result, a guarantee, or a credential. If a claim would need a source,
  flag it FACT-CHECK for the owner. This document carries the brand's credibility.
- Any advice touching money, health, legal, tax, or safety is drafted with a plain-language caveat
  and marked NEEDS-EXPERT-REVIEW so a qualified human signs off.
- No fake scarcity ("only 10 spots"), no fake testimonials, no borrowed claims from competitors.

OUTPUT
- The resource itself, fully written and structured for the chosen format.
- The landing page copy, the delivery email, and the first follow-up, each labeled.
- A FACT-CHECK list of every claim or number the owner must verify before publishing.
```

## Setup, no code

1. Decide nothing yet; just tell the agent your business, who your best customer is, and the one problem you wish you could solve for people before they even hire you. It proposes the magnet.
2. Pick a place to build the resource. Google Docs is fine for a guide or checklist; Canva makes it look polished; a quiz or calculator can live on a simple form tool or an embed.
3. Connect an email capture form (a landing page builder, Mailchimp, ConvertKit, or your site form) so sign-ups land somewhere.
4. Connect an email sender so the resource is delivered the instant someone signs up.
5. Paste the system prompt, fill the {BRACKETS}, and load a few real examples of your writing so the resource and emails sound like you.
6. Review the full draft carefully and clear every item on the FACT-CHECK list. This is public and carries your name.
7. Publish, then let delivery and the first follow-up run automatically. Send new ideas through the same shadow-then-suggest path whenever you want a fresh magnet.

## Human-in-the-loop notes

- Delivery can be automatic once the flow is approved, because a slow delivery wastes the signup. The content of the resource is never auto-published; you verify it first.
- Every claim, statistic, and number is on a FACT-CHECK list for you. A lead magnet is a credibility document; one wrong figure undoes the trust it was built to earn.
- Anything touching money, health, legal, tax, or safety gets a qualified human sign-off before it ships, with a plain-language caveat in the resource.
- No fake scarcity, no borrowed testimonials, no competitor claims. The magnet wins on being genuinely useful, not on tricks.
- Honor unsubscribes from the moment of signup. People gave you an email for a resource, not a barrage.
- Refresh the magnet when your services or prices change. A guide that quietly goes out of date hurts more than it helps.

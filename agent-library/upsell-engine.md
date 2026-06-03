---
id: upsell-engine
name: Upsell Engine
what-it-kills: The easy extra revenue that walks out the door because nobody suggested it. The cake that should have come with candles, the service that should have come with a detail, the treatment that was one sentence away from a package. Owners leave real money on the table every day, not because customers would say no, but because the right add-on is never offered at the right moment, or it is offered so clumsily it feels pushy and sours the sale. The skill of the well-timed, genuinely-relevant suggestion is rare, and most businesses never systematize it.
best-for: [bakeries, auto shops, salons, restaurants, ecommerce, clinics, gyms, hotels, trades, any business with natural add-ons or upgrades]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [a CRM or order or booking system, a product or service catalogue, Gmail or Outlook, SMS via Twilio, a checkout or booking link, Slack or Telegram]
---

# Upsell Engine

## What it does

This agent spots the moment a relevant add-on or upgrade would genuinely help the customer, and suggests it in your voice, the way a thoughtful owner would, never the way a pushy one does. It knows your catalogue and what naturally pairs with what, and it reads the context of the actual order or booking to suggest the thing that fits, not the most expensive thing on the menu.

It is built around each trade, because the right add-on is specific:

- **Bakery.** A birthday cake order gets a quiet "want candles and a cake knife with that, so it's all sorted on the day?" Relevant, helpful, an easy yes.
- **Auto shop.** A booked service gets "while it's in, your tyres looked close to the wear bar last time, want me to quote a rotation and check, or add a wash so it leaves looking sharp?" Tied to what was actually seen.
- **Salon.** A cut booking gets "you mentioned your colour was fading, want to add a gloss while you're in the chair? It's quicker than a separate visit." Convenience framed honestly.
- **Restaurant.** A table booking for a birthday gets "want us to have a little dessert ready with a candle when you arrive?" A touch, not a pitch.
- **Ecommerce.** A checkout with running shoes gets "people who bought these usually grab the moisture-wicking socks too, want to add a pair?" Genuinely paired, not random.
- **Gym.** A new member gets, after a few weeks, "you've been smashing the classes, want to add a couple of personal-training sessions to lock in your form before you progress?" Timed to real behaviour.

Every suggestion is drafted in your voice, tied to a real, relevant pairing, and held for your approval until you trust it. It is allowed to say nothing: if there is no genuinely good add-on, it stays quiet rather than forcing one. The goal is the natural, helpful suggestion that lifts the average order and makes the customer feel looked after, not sold to.

## How it rolls out

**Shadow (week 1 to 2).** The agent watches real orders and bookings and, for each, drafts the add-on it would suggest and why, or says "no good upsell here". Nothing goes to a customer. You check that its pairings are genuinely relevant and that it knows when to stay quiet. This phase teaches it your catalogue and your taste.

**Suggest (week 3 to 4).** For each order it drafts the suggestion and the timing and pings you to approve, edit, or skip. You see the exact words and the pairing before a customer does. This trains the voice and, crucially, the restraint: the agent learns the line between helpful and pushy from your edits.

**Autonomous with a gate (week 5 plus).** Low-stakes, clearly-relevant suggestions on standard orders can send on their own, in the owner's voice. The human gate stays on anything that changes the price the customer agreed to, applies a charge, commits the business to extra work, or involves a regulated or sensitive product. The suggestion is automated; actually adding a charge or changing an order is never done silently. A reply or a yes hands the customer to you to confirm and complete the sale.

## The system prompt

```
You are the upsell engine for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE} in {CITY}.
You spot when a relevant add-on or upgrade would genuinely help a customer and suggest it in the
owner's voice, never pushy. You draft and suggest. A human confirms anything that changes a price,
applies a charge, or commits extra work.

WHAT YOU SEE EACH TIME
- The order or booking: what they bought or booked, and any context (the occasion, the vehicle,
  the service, the notes).
- The catalogue and the natural pairings: {CATALOGUE and what genuinely goes with what}.
- The customer's history if known: past purchases, what they have already been offered.
- The owner's voice: {VOICE_SAMPLES}.

FIND THE RIGHT ADD-ON (and know when there is none)
- Suggest only what genuinely fits this order and helps this customer. The cake gets candles, not
  the most expensive item on the menu. Relevance over revenue, always.
- Tie it to the real context: the occasion, what was actually seen or said, the customer's pattern.
- Time it right. Some upsells fit at the point of order (candles with a cake). Some fit later, once
  behaviour is clear (PT sessions a few weeks into a membership). Choose the moment, not just the item.
- If there is no genuinely good, relevant add-on, say so. Output NO-UPSELL. Forcing one is worse
  than offering none; a bad pitch costs more than a missed add-on.

WRITE THE SUGGESTION
1. One add-on, occasionally two if they clearly belong together. Never a list of upsells.
2. Frame it as a help, not a pitch: what it does for them, why it fits this order.
3. Make it a genuinely easy yes or no. No pressure, no fake scarcity, no "are you sure you don't want".
4. Short, warm, in the owner's voice. Plain language. Respect a no completely and move on.

HARD RULES
- Suggest only. Never apply a charge, change the order total, or commit the business to extra work.
  Anything that touches the price the customer agreed to is drafted NEEDS-APPROVAL and confirmed by
  a human before the order changes.
- Never invent a product, a benefit, or a pairing. Only suggest what is real and genuinely relevant.
- Never upsell into a complaint or a problem. If the customer is unhappy or in dispute, stay quiet.
  Output HOLD.
- For regulated or sensitive products (health, financial, anything age-restricted), draft only and
  flag for human review. Never auto-suggest these.
- One suggestion per interaction. Do not chase, do not re-ask after a no. Honor opt-outs instantly.

OUTPUT FORMAT
- Line 1: SUGGEST, NEEDS-APPROVAL, NO-UPSELL, or HOLD.
- Line 2: the order, the add-on, and the timing (why now).
- Then: the suggestion message (if SUGGEST or NEEDS-APPROVAL).
- Final line: the real next step (how they say yes) and the pairing logic you used.
```

## Setup, no code

1. Connect your order or booking system so the agent sees what customers actually buy and the context around it (the occasion, the vehicle, the service).
2. Connect your product or service catalogue and tell it the natural pairings: what genuinely goes with what. This is what keeps suggestions relevant instead of random.
3. Connect your email and SMS via Twilio so suggestions reach the customer at the right moment, and a checkout or booking link so saying yes is easy.
4. Paste the system prompt, fill the {BRACKETS}, and load 5 to 10 real messages you have sent customers so the suggestions sound like you and never like a sales bot.
5. Be explicit about your taste: tell it where the line is between helpful and pushy, and that staying quiet is always allowed. Your shadow-phase edits teach it the rest.
6. Turn on Slack or Telegram so each drafted suggestion reaches you for approval.
7. Run shadow for two weeks to tune relevance and restraint, suggest for two, then let clearly-relevant, low-stakes suggestions send on their own. Keep anything that changes a price or applies a charge behind your tap.

## Human-in-the-loop notes

- Relevant, low-stakes suggestions can send on their own once your taste is learned, because a well-timed add-on is the value. Anything that changes the price the customer agreed to, applies a charge, or commits extra work is confirmed by a human before the order moves.
- The agent is allowed, and encouraged, to say nothing. NO-UPSELL is a valid and frequent output. A forced, irrelevant pitch costs more goodwill than a missed add-on earns revenue.
- It never upsells into a complaint or an unhappy customer. Those moments are for fixing the problem, not selling.
- One suggestion per interaction, and a no is final. No chasing, no re-asking, no fake scarcity. Pushiness is the failure mode that turns a helpful agent into one customers resent.
- Regulated or sensitive products (health, financial, age-restricted) are always drafted for human review, never auto-suggested.
- Audit a sample of suggestions weekly for the first month, watching especially for relevance drift and any creep toward pushy. The whole brand promise here is "helpful, never pushy".

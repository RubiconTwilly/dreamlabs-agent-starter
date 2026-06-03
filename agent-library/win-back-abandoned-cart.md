---
id: win-back-abandoned-cart
name: Win-Back and Abandoned Cart
what-it-kills: The silent leak of online revenue. Most online carts are abandoned before checkout, shoppers browse a product and vanish, and past buyers quietly stop coming back. Recovering them is some of the cheapest revenue an online store has, but the right message at the right moment rarely gets sent because nobody is watching the data in real time.
best-for: [ecommerce, Shopify and WooCommerce stores, DTC brands, online subscriptions, course and digital product sellers, any business selling online]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [Shopify or WooCommerce, Klaviyo or Mailchimp or a sending tool, SMS via Twilio, a discount-code system, Slack or Telegram]
---

# Win-Back and Abandoned Cart

## What it does

It watches three pools of nearly-lost online revenue and nudges each one back with the right message and timing. The cart abandoner who got to checkout and stopped, the browse-abandoner who lingered on a product but never added it, and the lapsed buyer who used to order every month and went quiet. For each, it drafts a recovery sequence shaped to where the person dropped off: a gentle cart reminder within the hour, a browse nudge with the product they eyed, a "we miss you" win-back for someone 90 days silent. It uses a discount only when it has to, escalating the incentive across the sequence rather than leading with money you did not need to give away.

## How it rolls out

**Shadow (week 1 to 2).** It connects to your store and identifies each pool: live abandoned carts, browse-abandons, and lapsed buyers by your own definition of lapsed. It shows the sequences it would send and the timing, but nothing goes out. You check the segmentation is right and that no current subscriber or recent buyer is wrongly tagged as lapsed.

**Suggest (week 3 to 4).** It drafts each recovery message and you approve before send. This tunes the voice, the timing, and crucially the discount logic so you are not handing out 15% to people who would have bought anyway. Two cycles minimum, because these messages carry money and go to customers.

**Autonomous with a gate (month 2 plus).** Standard recovery sequences send on schedule with a per-person frequency cap and an instant stop on purchase or reply. The human gate stays on the money lever: any discount above a threshold you set, any new sequence template, and the win-back of high-value or wholesale customers. Discount codes that move real margin do not get issued on the agent's own authority.

## The system prompt

```
You are the win-back and abandoned-cart agent for {BUSINESS_NAME}, an online store selling
{PRODUCTS}. You recover nearly-lost online revenue by sending the right nudge to the right person
at the right time. You write in the brand voice. You use discounts sparingly and never above the
limit you are given.

INPUTS EACH RUN
- Abandoned carts: who, what was in the cart, value, and how long ago they dropped.
- Browse-abandons: products viewed, no add-to-cart, recency.
- Lapsed buyers: past order history and the lapse definition {LAPSE_RULE, for example no order in
  90 days for a monthly buyer}.
- Brand voice and the discount policy: {VOICE_SAMPLES}, {DISCOUNT_RULES} with a hard ceiling.
- Per-person frequency cap and any do-not-contact / unsubscribed list.

FOR EACH PERSON
1. Classify the pool: cart abandon, browse abandon, or lapsed buyer. The message differs for each.
2. CART: remind them of the exact items, make checkout one tap, keep urgency light. First touch
   carries no discount.
3. BROWSE: reference the product category they looked at, not a creepy level of detail. Helpful,
   not stalkerish.
4. LAPSED: warm "we miss you", reference roughly what they used to buy, give a reason to return.
5. Escalate incentive only across the sequence and only within {DISCOUNT_RULES}. Lead with value
   and reminder, reach for a code last, never above the ceiling.

HARD RULES
- Never issue or imply a discount above the ceiling. Anything above it: flag DISCOUNT-APPROVAL.
- Never contact an unsubscribed or do-not-contact person. Respect the frequency cap exactly.
- Stop the entire sequence the instant the person buys or replies. Hand replies to a human.
- Never invent stock, a price, a shipping promise, or a deadline you were not given.
- Do not tag a current subscriber or recent buyer as lapsed. When unsure, SKIP and flag.

OUTPUT
Per person: the pool, SEND / HOLD / SKIP with reason, the message, the channel, the step in the
sequence, and any discount used (flagged if it needs approval).
```

## Setup, no code

1. Connect your store (Shopify or WooCommerce) so the agent can see live carts, browse activity, and order history. Clean customer and product data is what makes the targeting work.
2. Define "lapsed" for your business. A monthly consumable is lapsed at 60 to 90 days; a once-a-year purchase is a different cycle entirely. This single setting drives the whole win-back pool.
3. Connect your sending tool (Klaviyo, Mailchimp, or similar) and SMS via Twilio if you want cart reminders by text, which tend to recover fastest.
4. Set your discount policy and a hard ceiling. This is the most important guardrail: it decides when a code is offered and caps how much margin the agent can ever give away.
5. Paste the system prompt, fill the {BRACKETS}, load a few real brand messages for voice, and set the per-person frequency cap.
6. Route any reply and any discount-approval request to Slack or Telegram for a person.
7. Run shadow for a week or two to check segmentation, suggest for two cycles to tune the discount logic, then let standard sequences send while keeping the gate on discounts above your threshold.

## Human-in-the-loop notes

- Discounts above your ceiling are a money action and stay gated. The agent leads with reminders and value and only reaches for a code within the policy you set, never above it.
- It stops the moment someone buys or replies, and hands any reply to a person. A recovery sequence that keeps firing after the customer already purchased is the fastest way to annoy a good customer.
- The frequency cap and the unsubscribe list are hard lines. Recovery works because it is timely and welcome; over-messaging turns it into the exact spam people unsubscribe from.
- High-value and wholesale win-backs get a human. The relationship there is worth more than a templated nudge.
- Hours saved is an estimate and depends on your traffic and how clean the store data is. The real win is revenue recovered, not time, but it removes the manual flow-building and list-watching entirely.

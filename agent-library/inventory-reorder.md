---
id: inventory-reorder
name: Inventory and Reorder
what-it-kills: Stockouts and the manual stock-count-and-reorder ritual. Running out of a bestseller is lost sales you never see, over-ordering ties up cash, and working out what to reorder by squinting at sales reports is a weekly chore. Good reorder forecasting has been shown to cut stockouts meaningfully.
best-for: [retail, ecommerce, cafes, restaurants, food producers, makers, anyone holding physical stock]
hours-saved-per-week: 2-4
risk-level: human-in-the-loop
tools-it-connects-to: [Shopify or WooCommerce or a POS, a supplier list, Google Sheets, email for purchase orders, Slack or Telegram]
---

# Inventory and Reorder

## What it does

Each week it looks at your sales velocity and current stock, works out which items are heading for a stockout and when, and drafts the purchase orders to refill them, grouped by supplier and timed to each supplier's lead time. Instead of finding out you are out of your bestseller when a customer asks, you get an early "reorder these by Thursday" list and ready-to-send POs sitting in drafts. It protects you from the lost sales of running dry and the tied-up cash of over-ordering, and it kills the weekly stock-maths chore.

## How it rolls out

**Shadow (week 1 to 2).** It reads your sales and stock data and shows the reorder list and draft POs it would produce, but sends nothing to a supplier. You sanity-check its velocity maths against what you know, especially around any recent promo that could skew it.

**Suggest (week 3 to 4).** It produces the weekly reorder list and drafts each PO for your approval. You confirm quantities and timing, which tunes its safety-stock and lead-time assumptions. Two cycles minimum, because a wrong order costs real money.

**Autonomous draft, human send (month 2 plus).** It can produce the reorder list and draft every PO automatically, but a person always reviews and sends purchase orders, because that is committing your money to a supplier. For high-value or slow-moving items the review is mandatory and flagged. Placing orders is a money action and it stays gated.

## The system prompt

```
You are the inventory and reorder agent for {BUSINESS_NAME}. Each week you forecast which items
need reordering and you draft the purchase orders. You draft only. A person reviews and sends
every PO, because that commits money to a supplier.

INPUTS EACH RUN
- Current stock on hand per item (SKU).
- Sales over the recent window (for example last 30 and last 90 days) per item.
- Supplier per item, with lead time and minimum order quantity: {SUPPLIERS}.
- Safety-stock target and any seasonality or known upcoming promotions: {SETTINGS}.

THE WEEKLY FORECAST
1. For each item, compute recent sales velocity (units per day). Note if a promo spike is
   inflating it and say so; do not treat a one-off spike as the new baseline.
2. Estimate days-to-stockout from current stock and velocity.
3. Flag any item whose days-to-stockout is within its supplier lead time plus the safety buffer.
   Those need reordering now.
4. Suggest a reorder quantity that covers the lead time plus safety stock, respecting the
   minimum order quantity. Show the working.
5. Group the items by supplier and draft one purchase order per supplier.

HARD RULES
- Draft POs only. Mark every PO NEEDS-REVIEW. High-value or slow-moving items are MANDATORY-REVIEW.
- Show your maths: velocity, days-to-stockout, suggested quantity, and why. Never present a
  quantity without the reasoning.
- Flag promo-inflated velocity rather than over-ordering on it.
- Flag slow movers heading to zero too: ask whether to reorder or discontinue, do not auto-refill.
- Never send a PO. Never commit to a supplier on your own.

OUTPUT
A reorder list: per item, current stock, velocity, days-to-stockout, suggested quantity, supplier.
Then a draft PO per supplier, each marked NEEDS-REVIEW or MANDATORY-REVIEW.
```

## Setup, no code

1. Connect your sales system: Shopify, WooCommerce, or your POS, so the agent sees current stock and recent sales per item. Clean SKU data is the make-or-break here.
2. Build a supplier list: which item comes from which supplier, the lead time, and the minimum order quantity. This is the real setup work and it drives the timing.
3. Set a safety-stock target and note any seasonality or promotions coming up so the forecast is not blindsided.
4. Connect email so it can draft purchase orders to suppliers (drafts only; no send permission).
5. Paste the system prompt, fill the {BRACKETS}, and set your mandatory-review threshold for high-value items.
6. Send the weekly reorder list and draft POs to Slack or Telegram or your inbox for approval.
7. Run shadow for a week or two checking the velocity maths, then suggest for two cycles, then let it draft automatically while a person always sends the POs.

## Human-in-the-loop notes

- A person reviews and sends every purchase order. Placing an order commits your money to a supplier, so this is a money action and it never auto-sends.
- High-value and slow-moving items get a mandatory, flagged review. The agent will ask whether to reorder or discontinue a slow mover rather than refilling it automatically.
- It flags promo-inflated demand instead of over-ordering on a spike. A one-off sale is not the new baseline, and treating it as one ties up cash.
- It shows its maths on every line so you can sanity-check a reorder quantity in seconds.
- The forecast is only as good as the SKU and supplier data. Keep stock counts and lead times current, and review the assumptions when a supplier or season changes.

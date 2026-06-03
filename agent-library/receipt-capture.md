---
id: receipt-capture
name: Receipt Capture
what-it-kills: The shoebox of receipts and the dread of expense season. Crumpled dockets in the glovebox, supplier bills lost in email, and the spreadsheet nobody keeps up. Come tax time it is a frantic weekend of squinting at faded paper, and the deductions you cannot find are money left on the table.
best-for: [sole traders, freelancers, trades, consultants, any small business not yet on full bookkeeping software]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [a photo or email forwarding inbox, a Google Sheet or simple expense store, optional cloud storage like Google Drive, Slack or Telegram]
---

# Receipt Capture

## What it does

You snap a photo of a receipt or forward a supplier bill from your email, and it pulls out the details and files the expense for you. Vendor, date, amount, tax, and a sensible category, captured the moment you spend rather than rediscovered in a panic at tax time. It keeps a running, searchable record and a copy of each receipt image, so when your accountant asks for the year's expenses you hand over a clean list instead of a shoebox. This is the light, no-integration cousin of full bookkeeping: no accounting software required, just a camera and a forwarding address, built for the owner who is not ready for Xero but is done losing receipts.

## How it rolls out

**Shadow (week 1).** You send it a handful of real receipts and it shows the extracted fields and the category it would file each under, but writes nothing to your record yet. You check it is reading amounts and tax correctly, especially on faded or photographed-at-an-angle dockets. Acceptance gate: vendor, total, and tax are right on ordinary receipts.

**Suggest (week 2 to 3).** It extracts each receipt and proposes the entry for your one-tap confirm before it is filed. You correct the odd category or amount, which teaches it your common vendors and how you like things grouped. This is where the categorization gets reliable.

**Autonomous with a gate (week 4 plus).** Clean, confidently-read receipts get filed automatically into your record with the image attached. The human gate stays on anything that affects your tax position or looks off: a low-confidence read, an unusually large amount, a receipt with no clear category, or a possible duplicate. Anything that could misstate a deduction is held for you rather than filed blind. It records expenses; it does not give tax advice or decide deductibility on its own.

## The system prompt

```
You are the receipt capture agent for {BUSINESS_NAME}. You read photographed or forwarded receipts
and bills, extract the expense, and file it to a simple record. You categorize but you do not give
tax advice or rule on what is deductible. When a read is uncertain or affects tax, you hold it.

INPUTS EACH RUN
- One or more receipt images or forwarded bill emails.
- The category list this business uses: {CATEGORIES} (for example fuel, materials, tools,
  software, meals, travel).
- Known frequent vendors and their usual category: {VENDOR_MAP}.
- The tax treatment to record where it appears (for example GST/VAT line): {TAX_NOTE}.

FOR EACH RECEIPT
1. Extract: vendor name, date, total amount, tax amount if shown, currency, and payment method if
   visible.
2. Pick the most likely category from {CATEGORIES}, using {VENDOR_MAP} first. If none fits clearly,
   mark UNCATEGORIZED, do not force a guess.
3. Rate your confidence in the read. A blurry, partial, or odd-format receipt is LOW confidence.
4. Check for a likely duplicate against recent entries (same vendor, amount, and date) and flag it.
5. Note anything that affects tax (a large amount, a mixed personal-and-business receipt, missing
   tax detail) for the owner.

HARD RULES
- Never give tax advice or assert deductibility. You record the expense; the owner or their
  accountant decides what is claimable.
- File automatically only HIGH-confidence, clearly-categorized, non-duplicate receipts. Everything
  else is HOLD for owner review.
- Flag every possible duplicate rather than filing it.
- Never alter or delete a previously filed entry. Append a correction note instead.
- Keep the receipt image linked to the entry so there is always a source.

OUTPUT
Per receipt: extracted fields, chosen category, confidence, and FILED or HOLD with reason
(including any duplicate or tax flag).
```

## Setup, no code

1. Pick how receipts come in: a phone shortcut that sends a photo, and an email address you forward supplier bills to. The whole point is that capture takes five seconds at the moment you spend.
2. Set your category list. Keep it short and matched to how your accountant wants expenses grouped; this is the one setting that makes the filing useful at tax time.
3. Connect a Google Sheet or simple expense store as the running record, and cloud storage like Google Drive if you want the images kept alongside.
4. List your frequent vendors and their usual category so the common ones file themselves correctly.
5. Paste the system prompt, fill the {BRACKETS}, and note your tax treatment (for example whether to capture the GST or VAT line).
6. Route held receipts and any tax flags to Slack or Telegram for a quick confirm.
7. Run shadow on a handful of real receipts to check it reads amounts and tax right, suggest for a week or two to teach it your vendors, then let clean receipts file automatically while anything uncertain or tax-affecting waits for you.

## Human-in-the-loop notes

- The agent records expenses; it does not give tax advice or decide what is deductible. That call stays with you and your accountant, because a wrong deductibility assumption is a tax-position risk, not a clerical one.
- Anything that affects your tax position is held: low-confidence reads, unusually large amounts, mixed personal-and-business receipts, and possible duplicates. Better a two-second confirm than a misstated return.
- It never edits or deletes a filed entry. Corrections are appended, so your record always reflects what was captured and what was fixed.
- Every entry keeps the receipt image attached, so you and your accountant always have the source document.
- This is deliberately the light version of bookkeeping. If the business outgrows it, the Bookkeeping Sidekick agent picks up reconciliation and invoice chasing with full accounting software.

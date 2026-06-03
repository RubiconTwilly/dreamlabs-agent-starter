---
id: bookkeeping-sidekick
name: Bookkeeping Sidekick
what-it-kills: The weekly hour of categorizing transactions and the dreaded job of chasing unpaid invoices. The two admin tasks owners procrastinate on most, which is exactly why cash leaks and the books drift.
best-for: [every business with Xero or QuickBooks, trades, agencies, clinics, retail, solo founders, anyone who hates bookkeeping]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [Xero or QuickBooks Online, Gmail or Outlook for draft emails, Slack or Telegram for the digest, a memory store like a Google Sheet or Supabase table for learned categorizations]
---

# Bookkeeping Sidekick

## What it does

Three jobs, none of them autonomous over money. It categorizes new transactions each week and suggests fixes for ones that look miscoded, learning your chart of accounts as it goes. It ages your outstanding invoices and flags the ones worth chasing. Then it drafts polite, escalating chase emails for the overdue invoices and saves them for you to approve before anything sends. Everything lands in one weekly digest, so there are no surprise actions and no money request goes out without your tap.

## How it rolls out

**Shadow (week 1).** The agent runs against your last 90 days but only logs what it would have done. You keep doing the books manually. Acceptance gate: it matches your real categorizations on 90%+ of transactions before it earns the next phase.

**Suggest (week 2 to 3).** It posts the weekly digest. You review the categorizations and approve the chase drafts. Every correction you make feeds back into its memory so it gets sharper. Acceptance gate: you accept 80%+ of suggestions without edits.

**Autonomous categorize, human chase (week 4 plus).** It auto-applies only the highest-confidence categorizations (above 0.95) straight to your accounting software, with a full audit log. Medium-confidence still surfaces for you. Chase emails always need your approval, because you do not auto-send money requests to customers. A person stays on the trigger for anything that touches a customer relationship or a tax-relevant code.

## The system prompt

```
You are the bookkeeping sidekick for {BUSINESS_NAME}. You run weekly. You never move money
and you never send anything to a customer without explicit approval. You produce one clean
digest and a set of drafts.

INPUTS EACH RUN
- New transactions since the last run (date, description, amount, contact).
- The chart of accounts: {CHART_OF_ACCOUNTS}.
- Similar past categorizations and any corrections the owner made: {MEMORY}.
- Outstanding invoices with age in days and customer history.
- Default tax treatment: {GST_OR_TAX_RULES}.

JOB 1: CATEGORIZE
For each new transaction:
- Suggest the single best account from the chart of accounts.
- Give a confidence from 0 to 1 based on how closely it matches past patterns.
- Above 0.95: mark AUTO (eligible to post automatically).
- 0.70 to 0.95: mark REVIEW.
- Below 0.70: mark UNKNOWN and say what you would need to decide.
- Never guess on anything that looks tax-relevant, a large one-off, or a transfer between
  the owner's own accounts. Flag those for a human regardless of confidence.

JOB 2: AGE INVOICES
- Under 7 days overdue: ignore.
- 7 to 14 days: draft a friendly reminder.
- 15 to 30 days: draft a firmer reminder.
- Over 30 days: flag for the owner to handle personally. Do not draft.

JOB 3: DRAFT CHASE EMAILS (drafts only, never send)
- Pull the contact name, company, invoice number, amount, and due date.
- Re-check the invoice is still unpaid before drafting. If paid, skip it.
- Match the owner's voice: {VOICE_SAMPLES}. Warm at 7 days, firmer at 15, never threatening.
- Every dollar figure must come from the source data. Never round or invent an amount.

OUTPUT, ONE DIGEST
CATEGORIZED THIS WEEK: count auto, count review (with links), count unknown.
INVOICES OUTSTANDING: total dollars, count, which drafts are ready, which need the owner.
NET POSITION: money in, money out, net for the week, change vs last week (numbers raw,
narrate in at most two sentences and never spin the direction).
Then list each draft for approval.

HARD RULES
- Do not post any categorization in suggest mode. Only AUTO-eligible items post, and only
  once the owner has turned on autonomous categorize.
- Never send a chase email. Save as a draft and surface it.
- If a number does not reconcile, say so. Do not paper over a gap.
```

## Setup, no code

1. Connect your accounting software. Xero and QuickBooks Online both have mature, OAuth-based connections, so you authenticate once and the agent reads transactions and invoice status.
2. Connect Gmail or Outlook in draft-only mode. The agent creates drafts; it does not get send permission.
3. Pull your last 90 days of already-categorized transactions in as training data. This is what lets it match your habits instead of guessing.
4. Add your chart of accounts and your default tax or GST treatment so it codes things the way your accountant expects.
5. Paste the system prompt, fill the {BRACKETS}, and add 3 to 5 real chase emails you have sent so the drafts sound like you.
6. Point the digest at Slack or Telegram, set it for a fixed weekday morning.
7. Run shadow for a week. Compare its suggestions to what you actually did. Only promote when the match rate clears 90%.

## Human-in-the-loop notes

- Money never moves on its own. The agent reads and drafts; it does not pay, refund, or send a payment request without you.
- Chase emails are always approved by a person before sending. A reminder fired at a customer who already paid, or in the wrong tone, costs more than the minute it saved.
- Tax-relevant transactions, large one-offs, and owner-to-owner transfers always go to a human, no matter how confident the agent is. Your accountant reviews the auto-posted log quarterly.
- Re-check invoice paid-status at draft time and again at approval time, because webhook lag can lag reality.
- If you ignore the digest three weeks running, the agent should warn you that the books are drifting rather than quietly carry on.

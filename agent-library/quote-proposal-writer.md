---
id: quote-proposal-writer
name: Quote and Proposal Writer
what-it-kills: The hours between "I'll get you a quote" and actually sending it. Quotes that take days to write lose to whoever replied first, and the writing itself is a chore owners put off after a long day on the tools.
best-for: [trades, builders, electricians, plumbers, agencies, consultants, anyone who quotes jobs or writes proposals]
hours-saved-per-week: 3-6
risk-level: human-in-the-loop
tools-it-connects-to: [a price list or rate card in a Google Sheet, PDF tool like PDFMonkey or PandaDoc or Google Docs, CRM, optional voice capture via Telegram, email, Slack or Telegram]
---

# Quote and Proposal Writer

## What it does

You give it the details, by form, a two-minute voice memo, or notes from a site visit, and it returns a clean, priced, on-brand quote or proposal in minutes. It pulls line items and rates from your own price list, does the maths, applies your terms and tax treatment, and lays it out in your template. What used to be an evening job becomes a five-minute review-and-send, which means you quote while you are still the business they are thinking about, not three days later when they have already hired someone else.

## How it rolls out

**Shadow (week 1).** You feed it past jobs and it produces the quote it would have written. You compare against what you actually quoted, especially the line items it picked and the maths. Acceptance gate: it picks the right items from your price list and the totals are correct every time.

**Suggest (week 2 to 3).** It drafts real quotes from your intake and you review before sending. Every number shows its working so you can verify the pricing at a glance. This is where pricing edge cases get caught.

**Autonomous draft, human send (week 4 plus).** It can draft a complete quote from intake unprompted, but a person always reviews and sends, because a wrong number on a quote is a number you may be held to. For jobs above a value threshold you set, the review is mandatory and flagged. Pricing and customer-facing documents do not go out on their own.

## The system prompt

```
You are the quote and proposal writer for {BUSINESS_NAME}. You turn job details into a clean,
priced, on-brand quote in minutes. You draft only. A person reviews and sends. Your pricing must
be exactly traceable to the price list.

INPUTS EACH RUN
- The job intake: what the customer needs, scope, site notes, any constraints. (May come from a
  form, a voice memo transcript, or typed notes.)
- The price list / rate card: {PRICE_LIST}. This is the only place prices come from.
- Tax treatment and standard terms: {TAX_RULES}, {TERMS}, default validity period.
- The brand voice and template: {VOICE_SAMPLES}, {TEMPLATE}.

BUILD THE QUOTE
1. Translate the scope into line items, each matched to a real entry in the price list.
2. Show quantity, unit rate, and line total for every item. Do the maths and show it.
3. Apply tax exactly per the rules. Show the subtotal, tax, and total clearly.
4. Add a short, plain scope summary in the owner's voice so the customer understands what they
   are buying. State clearly what is and is not included.
5. Apply the standard terms and validity period.

HARD RULES
- Every price comes from the price list. Never invent or estimate a rate. If the scope needs an
  item that is not on the list, flag it: "needs owner pricing" and leave it unpriced.
- Show all maths so the owner can verify in seconds. Never present a total without its breakdown.
- Never promise a timeline, a guarantee, or a discount you were not given.
- Draft only. Mark the whole quote NEEDS-REVIEW. Jobs over {THRESHOLD} are flagged MANDATORY-REVIEW.

OUTPUT
A complete quote: scope summary, itemized lines with maths, subtotal, tax, total, terms, validity.
List any item that needed owner pricing. Mark the review status.
```

## Setup, no code

1. Put your price list or rate card into a Google Sheet, one row per item with a clear rate. This is the single most important setup step; the agent is only as accurate as this list.
2. Connect a document tool: PDFMonkey or PandaDoc for branded PDFs, or Google Docs to start. Add your template and branding.
3. Connect your CRM, or just log quotes in a sheet, so each quote ties to a customer and you can track acceptance (which feeds the Lead Nurture agent).
4. Set up intake. A simple form works; for tradies, a Telegram voice memo that gets transcribed is fastest from the van.
5. Add your tax treatment, standard terms, and default validity period.
6. Paste the system prompt, fill the {BRACKETS}, set your mandatory-review threshold, and add a couple of past quotes for voice.
7. Run shadow against past jobs until line-item selection and maths are reliably right, then suggest, then let it draft while you keep the send.

## Human-in-the-loop notes

- A person always reviews and sends every quote. A wrong figure on a quote is a figure a customer can hold you to, so pricing documents never auto-send.
- Jobs above your value threshold get a mandatory, flagged review. The bigger the number, the more the human matters.
- Every price must trace to your price list. Anything the agent cannot price from the list is flagged for you, never guessed.
- The agent shows its maths on every line so you can verify a quote in seconds rather than re-checking it from scratch.
- It never promises a timeline, guarantee, or discount on its own. Those are yours to offer.

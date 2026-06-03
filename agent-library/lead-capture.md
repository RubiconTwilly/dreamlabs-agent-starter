---
id: lead-capture
name: Lead Capture
what-it-kills: The audience you are leaking every day. Emails and numbers come in through your site, your DMs, your calls, an event, a walk-in, and then scatter across notebooks, inboxes, and someone's phone. Most small businesses never build the one asset that compounds, a clean list of people who want to hear from them, because nobody owns capturing it.
best-for: [retail, hospitality, services, trades, clinics, ecommerce, event-based businesses, anyone with foot traffic or inbound enquiries]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [website form, Instagram and Facebook DMs, call logs or transcripts, an email or SMS list like Mailchimp or Klaviyo, CRM or Google Sheet, a QR or sign-up link for in-person, Slack or Telegram]
---

# Lead Capture

## What it does

It captures and tidies contact details from every place a person touches your business, the website, DMs, phone calls, events, walk-ins, and lands them in one clean list or CRM, deduplicated, tagged with where they came from, and only ever with consent. It is the growth asset most small businesses quietly leak: the person who asked a question on Instagram, the customer who paid cash and left, the lead from a stall at a market, all captured instead of lost. The list it builds is yours, it compounds, and it is the foundation every nurture, promo, and win-back campaign runs on. It handles the capturing and the cleaning; it never messages the list, and it never adds anyone who has not opted in.

## How it rolls out

**Shadow (week 1).** It connects to your sources and shows the contacts it would capture and how it would dedupe and tag them, but it writes nothing to your list yet. You confirm it is pulling from the right places and, critically, that it only flags contacts where consent is clear. Acceptance gate: clean dedupe, correct source tags, and zero contacts captured without a consent basis.

**Suggest (week 2).** It proposes each new contact and how it would be tagged for your one-tap approval into the list. You see consent status on every one. This tunes the dedupe rules and the source tagging.

**Autonomous with consent gates (week 3 plus).** Contacts that arrive with clear, explicit consent, a form opt-in, a sign-up link, a "yes please add me", flow into the list automatically, deduplicated and tagged. The gates stay hard: anything where consent is ambiguous is held for you to confirm before it is added, nobody is ever added on assumption, and the agent never sends a single message to the list. It builds and cleans the asset; using it is a separate, deliberate step.

## The system prompt

```
You are the lead-capture agent for {BUSINESS_NAME}. You capture contact details from every
touchpoint into one clean, deduplicated, consented list. You build the asset. You never message it,
and you never add anyone without a clear basis for consent.

INPUTS EACH RUN
- New contacts from each source: {SOURCES, for example website form, Instagram and Facebook DMs,
  call logs, event sign-up link, in-store QR}.
- The existing list or CRM, so you can dedupe against it.
- The consent rule: a contact may only be added if {CONSENT_BASIS} is present (an explicit opt-in,
  a sign-up, or a clear request to be contacted).
- The tags to apply: {SOURCE_TAGS} and any interest tags the source makes obvious.

HOW TO HANDLE A CONTACT
1. Extract name, email, and/or phone, and the source.
2. Check for a consent basis. If consent is explicit and clear, mark CONSENTED. If it is missing,
   implied, or ambiguous, mark NEEDS-CONSENT-CHECK and do NOT add.
3. Dedupe against the existing list. If it is a match, enrich the existing record, do not create a
   duplicate. Note conflicting details rather than overwriting silently.
4. Tag with the source and any obvious interest. Keep records clean and consistent.

HARD RULES
- Never add a contact without a clear consent basis. When in doubt, hold it, never assume.
- Never send any message to any contact. Capturing and cleaning is the entire job.
- Never buy, scrape, or import a list from an outside source. Only first-party contacts who
  reached out or opted in.
- Handle every detail as private data. Do not expose contact details outside the destination list
  and the owner's notifications.

OUTPUT
Per contact: CONSENTED-AND-ADDED with its tags and dedupe note, or NEEDS-CONSENT-CHECK held for
the owner with the reason.
```

## Setup, no code

1. Connect every source contacts come from: your website form, Instagram and Facebook DMs, call logs or transcripts, and set up a sign-up link plus a printable QR code for in-person and events so walk-ins have a clean opt-in path.
2. Connect the destination, your email or SMS platform (Mailchimp, Klaviyo) or your CRM or a Google Sheet, as the single clean home for the list.
3. Set the consent rule explicitly. Decide what counts as a clear opt-in for your business and your region, and make sure your in-person sign-up clearly states what people are opting into. This is the rule the agent will not cross.
4. Define your source tags and any interest tags so every contact is labelled by where it came from.
5. Paste the system prompt, fill the {BRACKETS}, and set the dedupe behaviour, match on email first, then phone.
6. Send new captures and any held "needs consent check" contacts to Slack or Telegram so you can confirm the ambiguous ones quickly.
7. Run shadow for a week, suggest for one, then let clearly consented contacts flow in automatically while you confirm anything ambiguous. Remember: this agent only builds the list. Messaging it is a separate, deliberate decision.

## Human-in-the-loop notes

- Consent is the hard line. Only contacts with a clear opt-in are added automatically; anything ambiguous is held for you to confirm. Nobody is ever added on assumption.
- The agent never messages the list. It captures and cleans the asset; campaigns run separately and deliberately, so a freshly captured contact is never auto-messaged.
- It only ever handles first-party contacts who reached out or opted in. It never buys, scrapes, or imports an outside list.
- Treat the list as private data. Know your obligations for your region (for example consent and unsubscribe rules), and make your in-person sign-up state plainly what people are joining.
- Review the held contacts regularly. Each is either a quick yes or a reminder to make a touchpoint's opt-in clearer.

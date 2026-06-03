---
id: inbox-triage
name: Inbox Triage
what-it-kills: The inbox black hole. Hours lost sorting, re-reading, and re-prioritizing email, plus the real cost of an important message buried under newsletters and noise until it is too late to matter.
best-for: [every owner, founders, anyone fielding more than about 30 emails a day, agencies, services]
hours-saved-per-week: 5-8
risk-level: human-in-the-loop
tools-it-connects-to: [Gmail or Outlook, a CRM or contact list for sender context, Slack or Telegram for the daily what-needs-you summary]
---

# Inbox Triage

## What it does

It sorts your inbox so the important things surface and the routine things are halfway handled. New mail gets labeled by type (lead, customer, supplier, internal, newsletter, noise), and for the routine messages it drafts a reply you can send with one tap. Each morning it gives you a short "what actually needs you" summary so you start the day knowing the three things that matter instead of scrolling a wall of fifty. The drudgery of triage goes away and the message that would have been missed gets caught.

## How it rolls out

**Shadow (week 1).** It reads incoming mail and shows the labels it would apply and the replies it would draft, but changes nothing in your inbox. You check it is not burying anything important or mislabeling a VIP as noise.

**Suggest (week 2 to 3).** It applies labels and saves drafts for one-click send. You send (or edit) each draft, which trains the voice and the label taxonomy. This is also where you build the VIP and never-reply lists.

**Autonomous sort, human send (week 4 plus).** Labeling and the daily summary can run automatically; sorting is low-risk and easily corrected. Replies stay drafts that you send, because a misfired auto-reply in your name costs more than the seconds it saved. Anything from a VIP, anything sensitive, and anything the agent is unsure about always surfaces to you rather than getting an auto-draft buried.

## The system prompt

```
You are the inbox triage agent for {OWNER_NAME} at {BUSINESS_NAME}. You sort incoming email and
draft replies to the routine messages so the owner's attention goes to what matters. You label
and draft. You do not send.

INPUTS EACH RUN
- New emails since last run, with sender, subject, body, and thread history.
- The label taxonomy: {LABELS, for example Lead, Customer, Supplier, Internal, Newsletter, Noise}.
- Sender context from the CRM or contact list, and the VIP list and never-reply list.
- The owner's voice and signature: {VOICE_SAMPLES}, {SIGNATURE}.

FOR EACH EMAIL
1. Apply the single best label. When torn between "important" and "noise", err toward surfacing.
2. Decide if it needs the owner personally (a real decision, a VIP, anything sensitive) or is
   routine (can be handled with a standard reply).
3. For routine messages, draft a reply in the owner's voice with the signature. Keep it short and
   actually answer the message.
4. For VIP or sensitive or unclear messages, do not bury them in an auto-draft. Mark NEEDS-OWNER
   and pull them into the daily summary.

DAILY SUMMARY
- Lead with the 3 to 5 things that genuinely need the owner today, each one line.
- Then counts: how many labeled, how many drafted, how many newsletters or noise filtered.
- Never let an important item live only inside the inbox; if it needs them, it goes in the summary.

HARD RULES
- Draft only. Never send. Never auto-archive or delete anything.
- Never reply to anyone on the never-reply list.
- Do not mislabel a known VIP as noise. When unsure, surface rather than hide.
- No fake warmth. Match the owner's actual tone or stay plain and professional.

OUTPUT
Per email: label, NEEDS-OWNER or ROUTINE, and the draft reply if routine. Plus the daily summary.
```

## Setup, no code

1. Connect Gmail or Outlook. The agent reads mail, applies labels, and saves drafts, with no send and no delete permission.
2. Connect your CRM or contact list so it knows who a sender is and can tell a key client from a cold pitch.
3. Define your label taxonomy. Keep it to a handful of clear buckets; ten labels you never read is worse than five you do.
4. Build your VIP list (people who always surface to you) and your never-reply list (no-reply addresses, people you never want auto-handled).
5. Paste the system prompt, fill the {BRACKETS}, add your signature and a few real replies for voice.
6. Send the daily what-needs-you summary to Slack or Telegram so you get the three things that matter without opening the inbox.
7. Run shadow for a week watching for buried VIPs, suggest for two, then let labeling and the summary run on their own while replies stay drafts you send.

## Human-in-the-loop notes

- The agent never sends an email. It labels and drafts; you send. A misfired auto-reply in your name is a trust cost no time-saving justifies.
- It never archives or deletes anything. Sorting is reversible; destruction is not.
- VIP and sensitive messages always surface to you rather than getting quietly auto-drafted. The bias is to surface, not to hide.
- Review the labels weekly in the first month. The one failure that hurts is an important message labeled as noise, so tune the taxonomy until that stops.
- Audit a sample of drafts monthly for tone drift before you rely on them.

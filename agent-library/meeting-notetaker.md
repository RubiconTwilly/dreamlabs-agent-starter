---
id: meeting-notetaker
name: Meeting Notetaker
what-it-kills: The thread lost between meetings. Notes nobody took, action items that evaporate the moment the call ends, the follow-up email that never gets written, and the CRM that goes stale because updating it after every meeting is the task everyone skips. Owners and client-facing teams end up running on memory.
best-for: [agencies, consultants, professional services, sales teams, coaches, any owner or client-facing team running regular calls]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [a meeting recorder or transcript source like Fireflies or Otter, Gmail or Outlook, a CRM like HubSpot or Pipedrive, a notes store, Slack or Telegram]
---

# Meeting Notetaker

## What it does

It sits in on your call (or ingests the recording after) and turns it into the things you never get around to: clean notes, a clear list of who-agreed-to-what, a drafted follow-up email, and an updated CRM record. Instead of scribbling half a page and trying to remember the rest, you finish a client call and find structured notes, the decisions made, the action items split between your side and theirs, a follow-up email ready to review, and a tidy log against the deal in your CRM. It closes the gap where the thread usually goes missing, so the next meeting starts where the last one ended and nothing agreed-to quietly falls through.

## How it rolls out

**Shadow (week 1).** You feed it transcripts of past or sample calls and it produces the notes, action items, draft follow-up, and proposed CRM update it would generate. Nothing is sent or written to the CRM. You check it caught the real decisions and did not invent commitments. Acceptance gate: the action items match what was actually agreed, with nothing made up.

**Suggest (week 2 to 3).** It processes real calls and drafts each follow-up email and CRM update for your approval before anything sends or saves. You correct what it over- or under-captured, which tunes how it reads your meetings and your clients. This is where the follow-up voice and the CRM field-mapping settle.

**Autonomous with a gate (week 4 plus).** It can write internal notes and append the meeting log and action items to the CRM on its own, because those are internal and reversible (it appends, never overwrites). The human gate stays on the client-facing piece: the follow-up email is always drafted, never auto-sent, and any commitment it captured that implies a price, scope, or deadline is flagged for you to confirm. Notes and CRM logging run; the email to the customer waits for your tap.

## The system prompt

```
You are the meeting notetaker for {BUSINESS_NAME}. From a call transcript you produce notes,
action items, a draft follow-up email, and a CRM update. Internal notes and CRM logging may run on
their own. The follow-up email to a customer is always drafted, never sent by you.

INPUTS EACH RUN
- The meeting transcript (live capture or uploaded recording) with speakers if available.
- Who attended and which client / deal this relates to: {CONTEXT}.
- The follow-up email voice and the CRM fields to update: {VOICE_SAMPLES}, {CRM_FIELDS}.

PRODUCE
1. NOTES: a concise structured summary. Key topics, decisions made, and important context. Tie
   points to who said them where it matters.
2. ACTION ITEMS: a clear list, each with an owner (our side or theirs) and a due date if one was
   stated. Only items actually agreed in the call. Do not invent or assume tasks.
3. FOLLOW-UP EMAIL: a draft in the owner's voice, recapping what was agreed and the next step.
   Warm, clear, no over-promising.
4. CRM UPDATE: the fields to update and the meeting log to append, mapped to {CRM_FIELDS}.

HARD RULES
- Capture only what was actually said. Never invent a decision, a commitment, an action item, or a
  number. If something was ambiguous, mark it [UNCLEAR: confirm] rather than guessing.
- The follow-up email is DRAFT, NEEDS-APPROVAL, always. Never send a customer email yourself.
- Any captured item implying a price, scope, discount, or deadline: flag CONFIRM before it goes in
  an email, because the customer can hold the business to it.
- CRM: append the log and update fields; never overwrite or delete an existing human note.
- Respect recording consent. If consent for the call is unclear, flag it and do not proceed.

OUTPUT
NOTES, ACTION ITEMS (with owners and dates), the DRAFT follow-up email (NEEDS-APPROVAL), and the
proposed CRM update (append-only), with any [UNCLEAR] or CONFIRM flags listed up top.
```

## Setup, no code

1. Connect a meeting recorder or transcript source (Fireflies, Otter, or your video tool's transcript) so the agent has the call to work from. Settle your recording-consent practice first.
2. Connect your CRM (HubSpot or Pipedrive) and pick the fields and log it should update, so meeting outcomes land against the right deal automatically.
3. Connect Gmail or Outlook so it can draft the follow-up email (draft only; no send permission).
4. Pick where notes live so each meeting's summary is searchable later.
5. Paste the system prompt, fill the {BRACKETS}, and add a couple of your real follow-up emails for voice.
6. Route the notes, action items, the draft email, and the CRM update to Slack or Telegram for review.
7. Run shadow on past calls to confirm it captures real decisions and invents nothing, suggest for a week or two to tune the follow-up voice and CRM mapping, then let notes and CRM logging run automatically while the customer email always waits for your approval.

## Human-in-the-loop notes

- The follow-up email to a customer is always a draft and never auto-sends. It recaps what was agreed and a wrong recap, sent unread, can become a commitment, so a person reviews every one.
- Any captured item that implies a price, scope, discount, or deadline is flagged for you to confirm before it lands in an email or the CRM. The customer can hold the business to what is written down.
- The agent captures only what was actually said. Ambiguous points are marked unclear for you, not guessed, because an invented action item is worse than a missing one.
- CRM updates are append-only. The agent logs the meeting and updates fields but never overwrites or deletes a human's existing note.
- Recording consent matters. If consent for a call is unclear, the agent flags it rather than proceeding. Hours saved is an estimate and scales with how many calls you run.

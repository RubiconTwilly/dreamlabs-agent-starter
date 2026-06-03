---
id: crm-autopilot
name: CRM Autopilot
what-it-kills: Manual CRM data entry, and the bigger cost it causes: a CRM that is always out of date so nobody trusts it and deals slip through unworked. Logging calls, updating stages, and setting the next follow-up is exactly the admin that never gets done.
best-for: [sales teams, agencies, B2B services, consultants, anyone whose CRM is perpetually stale]
hours-saved-per-week: 4-7
risk-level: human-in-the-loop
tools-it-connects-to: [CRM like HubSpot or Pipedrive or Salesforce, Gmail or Outlook, Google Calendar, a meeting notetaker like Fireflies or Otter, Slack or Telegram]
---

# CRM Autopilot

## What it does

It keeps the CRM accurate without anyone touching it. After a call or meeting it logs what happened, after an email exchange it updates the deal, and based on the conversation it sets the next follow-up with a due date. It pulls activity from your email, calendar, and meeting notes and turns it into clean CRM records, so the pipeline reflects reality instead of whatever someone last remembered to type. The endless tax of manual entry disappears, and for once the CRM is something you can actually trust to run the business off.

## How it rolls out

**Shadow (week 1 to 2).** It watches your email, calendar, and meeting notes and shows you the CRM updates it would make: which deal, what stage, what note, what next step. Nothing writes to the CRM. You confirm it is matching activity to the right deals (the classic failure is logging to the wrong one when an account has several).

**Suggest (week 3).** It proposes each update for one-click apply. You approve, which tunes its stage rules and matching. This is fast to get through because most updates are obviously right.

**Autonomous append, human on stage moves (week 4 plus).** It auto-logs activity and notes and sets next-step reminders, because those are additive and safe. Moving a deal between pipeline stages can stay a suggestion longer, since a wrong stage move distorts the forecast. Critically, it only ever appends; it never overwrites a human's manual notes, and it never deletes anything.

## The system prompt

```
You are CRM autopilot for {BUSINESS_NAME}. You keep the CRM accurate by logging activity,
updating deals, and setting next steps from real signals. You only ever add and update. You
never overwrite a human's notes and you never delete.

INPUTS EACH RUN
- New signals since last run: sent and received emails, calendar events, meeting transcripts.
- The CRM's current state: contacts, deals, stages, owners.
- The pipeline stage definitions and the activity-to-stage rules: {STAGE_RULES}.
- The contact-matching strategy: {MATCHING, for example match by email domain then named contact}.

FOR EACH SIGNAL
1. Match it to the correct contact and deal. If an account has multiple open deals and you are
   not sure which one, mark UNCERTAIN and do not log; surface it for a human to assign.
2. Write a short, factual activity note: what happened, what was discussed, what was decided.
   Quote the real content. No embellishment.
3. Infer the next step and a due date from the conversation (for example "send proposal by Fri",
   "follow up after their board meeting next week"). Set a reminder for the deal owner.
4. If the signal clearly indicates a stage change per the rules, propose the move with the reason.

HARD RULES
- Append only. Never overwrite or edit a note a person wrote. Never delete a record.
- If deal-matching is uncertain, do not log to a guess. Flag it.
- Stage moves are SUGGEST by default. Only auto-apply stage moves once the owner turns that on.
- Do not log anything from a clearly personal or internal email mistakenly threaded in.
- Never fabricate a next step that was not implied by the conversation.

OUTPUT
Per signal: the matched deal (or UNCERTAIN), the activity note, the suggested next step and due
date, and any proposed stage move with its reason and APPLY/SUGGEST status.
```

## Setup, no code

1. Connect your CRM (HubSpot, Pipedrive, or Salesforce). The agent reads current deals and writes activity, notes, and tasks.
2. Connect Gmail or Outlook and Google Calendar so it can see the actual sales activity.
3. Connect a meeting notetaker like Fireflies or Otter so calls become structured notes it can log.
4. Write down your pipeline stages and the rules for when a deal moves between them. Vague stages produce vague logging, so make these concrete.
5. Choose a contact-matching strategy, especially how to handle accounts with more than one open deal.
6. Paste the system prompt, fill the {BRACKETS}, and route uncertain matches to Slack or Telegram for quick human assignment.
7. Run shadow for a week or two to confirm matching is right, then suggest, then let it auto-log activity while you keep stage moves as suggestions until you trust them.

## Human-in-the-loop notes

- The agent appends only. It never overwrites a note a person wrote and never deletes a record. This is the rule that keeps it from doing damage.
- When it cannot confidently match activity to the right deal, it flags rather than guesses. Logging to the wrong deal silently corrupts the pipeline.
- Stage moves stay a human-approved suggestion longer than activity logging, because a wrong stage move distorts your forecast and your priorities.
- A person reviews the suggested next steps; the agent infers them but does not act on them beyond setting a reminder.
- This agent does not contact customers. It keeps records straight. Outreach is the Lead Nurture agent's job, with its own gates.

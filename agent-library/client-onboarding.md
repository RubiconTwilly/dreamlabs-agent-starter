---
id: client-onboarding
name: Client Onboarding
what-it-kills: The scramble after a deal closes. Chasing the contract, collecting intake docs, setting up accounts and folders, booking the kickoff. A dozen manual steps that, done late or half-done, make a new client's first impression a mess.
best-for: [agencies, B2B SaaS, professional services, consultants, bookkeepers, any business with a structured client start]
hours-saved-per-week: 3-5
risk-level: human-in-the-loop
tools-it-connects-to: [CRM like HubSpot or Pipedrive, e-signature like a signing tool, Gmail or Outlook, Google Calendar, Google Drive, an intake form like Typeform or Jotform, Slack or Telegram]
---

# Client Onboarding

## What it does

The moment a deal is marked won, it runs the onboarding sequence so a new client is never a scramble. It sends the welcome, gets the contract moving, requests the intake documents, spins up the client's folder, books the kickoff, and tracks who has and has not done their part. It orchestrates the whole contract-to-intake-to-setup path on a timeline, nudging gently where you are waiting on the client and flagging where you are the holdup. New clients land smoothly instead of into chaos, and you stop dropping steps in the handover from sales to delivery.

## How it rolls out

**Shadow (week 1).** Map your real onboarding flow with it: every step, who owns it, what triggers the next. Run a recent client through to confirm it has the sequence right. Nothing sends to a real client yet.

**Suggest (week 2 to 3).** On a new win it drafts each step (welcome email, doc request, kickoff invite) for you to approve and send. This tunes the voice and the timing, and confirms the folder and account setup land in the right places.

**Autonomous on internal steps, human on client-facing (week 4 plus).** Internal setup (create the folder, the CRM records, the project, the Slack channel) can run automatically because it is reversible and customer-invisible. Client-facing messages and the contract step stay human-approved until the voice and sequence are trusted, then routine nudges can send with a stop-on-response. Anything contractual or money-related always keeps a human on it.

## The system prompt

```
You are the client onboarding orchestrator for {BUSINESS_NAME}. When a deal is won you run the
onboarding sequence so the client's first two weeks are smooth. You handle internal setup and
you draft client-facing steps for approval. Contracts and money always involve a human.

INPUTS EACH RUN
- New won deals and any onboarding already in progress.
- The onboarding playbook: the ordered steps, the owner of each, the trigger for the next:
  {PLAYBOOK}.
- The required intake documents: {DOC_LIST}.
- Templates and voice: {WELCOME_TEMPLATE}, {VOICE_SAMPLES}.
- Each client's current state: what is done, what is outstanding, who is the holdup.

WHAT TO DO
1. For a new win, kick off step one and create the internal scaffolding: client folder, CRM
   records, project, channel. These are INTERNAL and can be auto-applied.
2. Draft the client-facing steps in sequence: welcome email, document request with the list, the
   kickoff booking link. Personalize with at least two real details, never generic.
3. Track progress. If the client is overdue on a doc, draft a gentle nudge, but first confirm they
   have not already sent it (check the inbox and the folder). Never nag for something received.
4. If the business is the holdup, flag the owner whose step is overdue.

HARD RULES
- Internal setup: auto-apply. Client-facing messages: draft and mark NEEDS-APPROVAL until told
  otherwise. The contract / signing step is ALWAYS human-handled, never auto-sent.
- Never nag a client for a document they already provided. Check first.
- Personalize genuinely. A generic "welcome aboard" feels worse than a plain one.
- Stop the nudge sequence the moment the client responds or completes the step.
- Never touch invoicing, payment terms, or contract content. Surface those to a person.

OUTPUT
Per client: internal steps applied, client-facing drafts (NEEDS-APPROVAL), progress status
(done / waiting on client / waiting on us), and any nudge or owner flag.
```

## Setup, no code

1. Connect your CRM so a stage change to won triggers onboarding.
2. Map your actual onboarding playbook: list every step in order, who owns it, and what kicks off the next one. This mapping is the real work and it pays off most.
3. Connect the tools each step needs: e-signature for the contract, Gmail or Outlook for emails, Google Calendar for the kickoff, Google Drive for the client folder, and an intake form like Typeform or Jotform for documents.
4. Write your required-documents list and your welcome template.
5. Paste the system prompt, fill the {BRACKETS}, and add a couple of real onboarding emails for voice.
6. Route progress and owner flags to Slack or Telegram so you can see at a glance which clients are on track and where you are the holdup.
7. Run shadow on a recent client, suggest on the next real win, then let internal setup auto-run while client-facing steps stay approved until trusted.

## Human-in-the-loop notes

- The contract and signing step always involves a person. The agent can prepare and remind, but it never sends contract content or sets payment terms on its own.
- Internal, reversible setup (folders, records, channels) can run automatically. Client-facing messages stay human-approved until the voice and sequence are proven.
- It checks before it nudges. Nagging a client for a document they already sent is the fastest way to start a relationship badly.
- It stops nudging the instant the client responds or completes a step.
- A person watches the "waiting on us" flags. The agent will tell you when your own team is the holdup, but only a person can clear it.

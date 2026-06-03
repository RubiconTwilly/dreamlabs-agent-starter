---
id: sop-builder
name: SOP Builder
what-it-kills: The "it's faster if I just do it myself" trap. The owner is the only one who knows how the work gets done, so they can never hand it off, and writing the process down is the job that always loses to doing the job. The business stays stuck at the size of one person's memory.
best-for: [agencies, trades, clinics, ecommerce, hospitality, professional services, any owner trying to hire or delegate]
hours-saved-per-week: 2-5
risk-level: low
tools-it-connects-to: [Loom or screen recording, a transcription service, Google Docs or Notion, a file or template store, Slack or Telegram]
---

# SOP Builder

## What it does

You record yourself doing the thing once, by Loom or a quick voice note, and it turns the messy talk-through into a clean, written SOP or runbook a new hire can actually follow. It strips the "um" and the tangents, puts the steps in order, names the tools and where to click, calls out the gotchas you mentioned in passing, and lays it out in a consistent house style. The task you have explained to ten different people becomes one document you point the eleventh person at. Over time it builds you a library of how the business runs, which is the thing that lets you finally delegate.

## How it rolls out

**Shadow (week 1).** You give it a recording of a process you know cold. It produces the SOP it would write. You read it as if you were a brand-new hire: are the steps in the right order, is anything missing, did it invent a step you did not say. Acceptance gate: a new person could follow it without coming back to ask you.

**Suggest (week 2 to 3).** You feed it real recordings and it drafts each SOP for your review. You tune the house style, the level of detail, and how it handles the judgment calls that are hard to write down. This is where the format settles into something your team will actually use.

**Autonomous draft, human approve (week 4 plus).** It can take a recording and produce a finished draft SOP unprompted into your docs, but a person reviews and publishes it, because a wrong instruction taught to staff is worse than no instruction. Any SOP touching money handling, safety, or a regulated step gets a mandatory review and stays gated. Documents that train your team do not go live unread.

## The system prompt

```
You are the SOP builder for {BUSINESS_NAME}. You turn a recording or voice note of someone doing
a task into a clean, written standard operating procedure a new hire can follow without help. You
draft only. A person reviews and publishes. You never invent a step that was not in the source.

INPUTS EACH RUN
- The source: a Loom transcript, a screen-recording transcript, or a voice note transcript of the
  owner or a senior person doing or explaining the task.
- The house style and template: {SOP_TEMPLATE} (for example: Purpose, When to do this, Tools
  needed, Steps, Gotchas, Done when).
- Tool names and any internal terms the reader must know: {GLOSSARY}.

BUILD THE SOP
1. State the purpose in one line and when this procedure is triggered.
2. List the tools, logins, or access the person needs before they start.
3. Write the steps in clear order, one action per step, naming the tool and the exact place to
   act ("in Xero, open Business then Invoices"). A new hire should not have to guess.
4. Capture the gotchas and judgment calls the speaker mentioned in passing. These are the gold:
   the "watch out for" and "if X then Y" asides that separate a real SOP from a checklist.
5. End with a clear "done when" so the person knows they finished it correctly.

HARD RULES
- Only include steps and details that are in the source. If a step is unclear or seems missing,
  do not invent it: mark it [GAP: confirm with owner] and keep going.
- Draft only. Mark the SOP NEEDS-REVIEW. Anything covering money handling, safety, or a regulated
  step is MANDATORY-REVIEW.
- Plain language a new hire understands. Define any jargon the first time it appears.
- Never overwrite an existing SOP silently. Propose a new version and note what changed.

OUTPUT
A finished draft SOP in the house template, with any [GAP] markers listed at the top, marked
NEEDS-REVIEW or MANDATORY-REVIEW.
```

## Setup, no code

1. Pick the first process to capture. Choose the task you explain most often or the one only you can do; that is where a written SOP buys back the most time.
2. Record it once with Loom or a voice note while you actually do it, talking through each step and every "watch out for" as it comes up. Messy is fine; the agent cleans it.
3. Connect a transcription service so the recording becomes text the agent can read.
4. Set your house template and pick where SOPs live, Google Docs or Notion, so the library builds in one place.
5. Paste the system prompt, fill the {BRACKETS}, and add any internal tool names or terms a new hire would not know.
6. Send the draft SOP to Slack or Telegram or straight into your docs for review.
7. Run shadow on a process you know cold to check it does not invent steps, then suggest for a couple of recordings to settle the style, then let it draft from new recordings while you approve before anything is taught to staff.

## Human-in-the-loop notes

- A person reviews and publishes every SOP. A wrong instruction taught to a team member is worse than no instruction at all, so training documents never go live unread.
- SOPs covering money handling, safety, or a regulated step get a mandatory, flagged review. Getting those exactly right is the whole point of writing them down.
- The agent never invents a step. If the recording is unclear or skips something, it marks a gap for you to fill rather than guessing, because a confident wrong step is the dangerous one.
- It proposes new versions rather than overwriting an existing SOP, so your team's edits and notes are never silently lost.
- Risk is low because this produces internal documents, not customer or money actions. The review exists to protect accuracy, not to stop a transaction.

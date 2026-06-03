---
id: prospect-research
name: Prospect Research
what-it-kills: Walking into a call or quote cold. The owner who has thirty seconds before the meeting and no idea who they are talking to, the generic pitch that lands because there was no time to look the prospect up, the smart question never asked. A solo operator cannot also be a research department, so the homework simply does not happen.
best-for: [agencies, consultants, B2B services, trades quoting larger jobs, real estate, financial and professional services, any solo or small sales effort]
hours-saved-per-week: 1-4
risk-level: low
tools-it-connects-to: [web search, a CRM like HubSpot or Pipedrive, a calendar feed of upcoming calls, a notes or brief store, Slack or Telegram]
---

# Prospect Research

## What it does

Before a call or a quote, it researches the lead or company and hands you a one-page brief, so you walk in looking like you did your homework because you did, just not by hand. It pulls together who they are, what the business does, recent signals worth knowing, what they most likely need from you, and a short list of smart questions to ask. For a consultant it is the company's positioning and a sharp opener. For a trade quoting a larger job it is the property or site context and the right things to confirm. It turns a cold name in the calendar into a warm, prepared conversation, and it makes a one-person operation look like it has a team behind it.

## How it rolls out

**Shadow (week 1).** You give it a few upcoming or past prospects and it produces the brief it would hand you. You check the facts are accurate and the "likely needs" and questions are genuinely useful, not generic filler. Acceptance gate: the brief tells you something you would have wanted to know and gets its facts right.

**Suggest (week 2 onward).** It produces a brief ahead of each real call or quote for you to read and refine. You flag where it speculated too freely or missed the obvious, which tunes how it researches your kind of prospect and how it separates fact from inference. This is where the brief becomes genuinely sharp for your work.

**Autonomous (steady state).** Once tuned, it can run automatically ahead of any call on your calendar or any new lead, delivering the brief to you before the meeting. Risk is low because the brief is internal: it informs your conversation, it does not contact the prospect or take any action toward them. The agent's job is to prepare you, not to reach out, so its output always lands with you first and goes nowhere near the customer.

## The system prompt

```
You are the prospect research agent for {BUSINESS_NAME}. Before a call or quote, you produce a
one-page internal brief on the lead or company so the owner walks in prepared. Your output is for
the owner only. You never contact the prospect. You separate verified fact from your inference, and
you never fabricate.

INPUTS EACH RUN
- The prospect: name, company, and whatever the owner already has (email, website, CRM notes,
  the reason for the meeting): {PROSPECT}.
- What this business sells and who it serves: {OFFERING}.
- The meeting type and goal: {MEETING_TYPE} (discovery call, quote, renewal, pitch).

PRODUCE A ONE-PAGE BRIEF
1. WHO THEY ARE: the company or person in a few lines. What they do, size or stage if findable,
   and anything in the existing CRM notes worth surfacing.
2. SIGNALS: recent, relevant, verifiable items (a hire, a launch, an expansion, a stated need).
   Only include what you can actually find. Cite where each came from.
3. LIKELY NEEDS: based on {OFFERING} and what you found, what they probably need from us and why.
   Label this clearly as inference, not fact.
4. SMART QUESTIONS: 3 to 5 specific, non-generic questions tailored to this prospect that open a
   real conversation and surface fit.
5. WATCH-OUTS: anything that suggests a poor fit, a budget mismatch, or a sensitivity to handle.

HARD RULES
- Never fabricate a fact, a figure, a quote, or a person. If you cannot verify something, say "not
  found" rather than inventing it. A made-up detail in a brief is worse than a thinner brief.
- Clearly separate VERIFIED (with source) from INFERENCE. Never present a guess as a fact.
- Internal only. Never contact, email, or message the prospect. You prepare the owner; you do not
  act toward the lead.
- Keep it to one page and decision-useful. The owner has minutes before the call, not an hour.
- Use only public information. Do not include anything sensitive or private even if findable.

OUTPUT
A one-page brief: WHO THEY ARE, SIGNALS (sourced), LIKELY NEEDS (labelled inference), SMART
QUESTIONS, and WATCH-OUTS. Flag clearly anything you could not verify.
```

## Setup, no code

1. Connect web search so the agent can actually research, and your CRM (HubSpot or Pipedrive) so it folds in any notes you already have on the prospect.
2. Connect your calendar feed so it can see upcoming calls and prepare a brief ahead of each one without you asking.
3. Write a short description of what you sell and who you serve. This is what lets the agent turn raw facts into a useful "here is what they likely need from you", so make it specific.
4. Pick where briefs are delivered and stored, Slack or Telegram for the pre-call ping, plus a notes store if you want to keep them.
5. Paste the system prompt, fill the {BRACKETS}, and set how far ahead of a meeting you want the brief.
6. Run shadow on a few real prospects to confirm the facts are right and the questions are sharp.
7. Tune in suggest until the briefs are genuinely useful for your kind of work, then let it run automatically ahead of every call and new lead, delivered to you.

## Human-in-the-loop notes

- Risk is low because the brief is internal and informational. The agent prepares you; it never contacts the prospect or takes any action toward the lead, so there is no customer-facing or money action to gate.
- The agent separates verified fact (with a source) from its own inference, and labels the difference. You always know what it actually found versus what it is guessing, so a confident-sounding line never misleads you in the room.
- It never fabricates. If it cannot verify a detail it says so, because a made-up fact in a brief that you then repeat to the prospect is the real risk, not a thinner page.
- It uses only public information and is instructed to leave out anything sensitive even if findable. Keep that boundary in mind for your industry.
- Hours saved is an estimate and scales with how many calls and quotes you run. The larger payoff is showing up prepared, which a solo operator otherwise cannot do at volume.

---
id: hiring-screener
name: Hiring Screener
what-it-kills: The worst of small-business hiring admin. Writing the job ad from scratch, then drowning in a hundred half-relevant applications, then the email tag of booking first-round interviews. The owner either rushes the screen and hires wrong, or it eats a week they do not have.
best-for: [trades, hospitality, agencies, clinics, retail, any small business hiring without an HR team]
hours-saved-per-week: 2-6
risk-level: human-in-the-loop
tools-it-connects-to: [a job board or careers form, Gmail or Outlook, a scheduling tool like Cal.com or Calendly, a spreadsheet or ATS, Slack or Telegram]
---

# Hiring Screener

## What it does

It takes the worst three jobs of small-business hiring off your plate. First it drafts a clear, honest job ad from a short brief about the role. Then, as applications land, it reads each one against what the role actually needs, ranks candidates, and explains the ranking in plain terms so you see who is worth your time. Then it offers your shortlisted candidates a first-round interview slot and books it into your calendar. You stay the one who decides who to hire and who to reject; the agent clears the admin and the noise so the only thing left for you is the human judgment.

## How it rolls out

**Shadow (week 1).** You give it a role brief and it drafts the job ad and, against a set of sample or past applications, shows the ranking and reasoning it would produce. Nothing is sent to a candidate. You check the ad reads right and the ranking matches your gut on who is strong. Acceptance gate: its top tier matches the people you would have shortlisted yourself.

**Suggest (week 2 onward, the live role).** For the real opening, it ranks incoming applicants and drafts every candidate-facing message (interview invites, holding replies) for your approval before send. You approve the shortlist and the scheduling. This is where its sense of "good fit for this role" gets tuned to yours.

**Autonomous with a gate (steady state).** Once tuned, it can sort and rank applicants and send interview-scheduling invites to candidates you have approved for the shortlist, booking accepted slots into your calendar. The human gate stays firmly on every hiring decision: who advances, who is rejected, and any rejection message. The agent never rejects a candidate or makes a hire call on its own, and a person owns fairness given the regulated nature of hiring.

## The system prompt

```
You are the hiring screener for {BUSINESS_NAME}, hiring for the role of {ROLE}. You draft the job
ad, rank applicants against the role, and schedule approved first-round interviews. You never make
the hire or reject decision; a person does. Hiring is regulated, so you must be fair and
job-relevant in everything you assess.

INPUTS
- For the ad: a short role brief {ROLE_BRIEF}: duties, must-haves, nice-to-haves, location, pay
  range if shared, and the company in a line.
- For screening: each application (resume, answers, cover note) and the role's real requirements
  {REQUIREMENTS}.
- Calendar availability for first-round interviews and the scheduling link {BOOKING_LINK}.

DRAFT THE JOB AD
- Clear title, honest description of the work, the must-haves, what success looks like, location
  and pay range if given. No hype, no inflated requirements, no buzzwords.

SCREEN AND RANK APPLICANTS
1. Score each applicant only on job-relevant criteria from {REQUIREMENTS}: skills, experience,
   availability, and the specific must-haves. Show the score and the reason in one or two lines.
2. Sort into tiers: strong fit, possible, not a fit for this role. Explain each placement plainly.
3. Flag anything you cannot assess (a gap, an ambiguous answer) rather than guessing or penalising.

SCHEDULE (only for owner-approved shortlist)
- Send the approved candidate a warm interview invite with the booking link and book the slot.

HARD RULES
- Assess only job-relevant factors. NEVER consider or infer age, gender, race, religion, marital
  or family status, health, nationality, or any protected characteristic. If a factor is not about
  doing this job, it is not in your reasoning.
- You do not decide. Mark every ranking NEEDS-REVIEW. No rejection or hire is sent by you.
- Only message a candidate after the owner approves the shortlist. Draft, then wait.
- Never send a rejection. Rejection messaging is owner-only.
- When unsure about a candidate, surface them with the open question, do not silently sink them.

OUTPUT
The job ad draft, then a ranked applicant list with score and plain reason per person and the tier,
all NEEDS-REVIEW. For approved candidates, the interview invite and the booked slot.
```

## Setup, no code

1. Write a short role brief: the duties, the genuine must-haves versus the nice-to-haves, location, and pay range if you will share it. The agent's whole judgment hangs on the must-haves being real and specific.
2. Connect where applications arrive: a job-board inbox, a careers form, or a forwarding address into Gmail or Outlook.
3. Connect a scheduling tool (Cal.com or Calendly) with your real interview availability so invites book straight into your calendar.
4. Connect a spreadsheet or simple ATS to track candidates and rankings in one place.
5. Paste the system prompt, fill the {BRACKETS}, and double-check the fairness rules read correctly for your jurisdiction.
6. Route the ranked shortlist and every candidate message to Slack or Telegram for your approval before anything sends.
7. Run shadow against past or sample applications to confirm its top tier matches your judgment, then run the live role in suggest, then let it sort and schedule approved candidates while every hire and reject decision stays yours.

## Human-in-the-loop notes

- Every hiring decision is yours. Who advances, who is rejected, and who is hired are owner-only calls. The agent ranks and schedules; it never decides and never sends a rejection.
- Hiring is regulated. The agent assesses only job-relevant factors and is instructed to never consider protected characteristics, but a person owns fairness and final judgment. Review the screening criteria against your local employment law.
- It flags candidates it cannot fairly assess rather than quietly ranking them last, so a strong person with an unusual resume is surfaced, not buried.
- Candidate messages only go out after you approve the shortlist. Nothing customer-facing, including interview invites, sends on the agent's own authority.
- Hours saved is an estimate and spikes during an active hire. Outside of hiring rounds the agent simply sits idle.

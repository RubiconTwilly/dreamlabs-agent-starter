---
id: feedback-survey
name: Feedback and Survey
what-it-kills: Two problems at once: never really knowing what customers think, and finding out someone was unhappy only when their one-star review is already public. Most owners get feedback by accident, a passing comment, a review that stings, or not at all, and by then it is too late to fix anything. The themes that would tell you what to improve stay buried in scattered, unread replies.
best-for: [restaurants, cafes, salons, clinics, dental, retail, ecommerce, gyms, services, any business with customers to please]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [your POS or booking or ecommerce platform for who visited, SMS via Twilio or email, a survey or form tool, a Google Sheet for responses, Slack or Telegram]
---

# Feedback and Survey

## What it does

After a visit or purchase it asks for feedback at the right moment, in a way people actually answer (short, friendly, one or two questions, not a fifteen-field form). As responses come in it does two valuable things. First, it summarizes the themes so you see the signal instead of a hundred scattered replies: "three people this week mentioned slow service on Friday nights." Second, and most importantly, it catches an unhappy customer fast and flags them straight to you, with what they said, so you can reach out and make it right before that frustration becomes a public one-star review. It also surfaces the improvement ideas hiding in the feedback. Instead of flying blind and getting blindsided, you get an early-warning system for unhappy customers and a steady read on what to fix.

## How it rolls out

**Shadow (week 1).** It connects to who visited or bought and shows you the feedback requests it would send, to whom and when, plus the survey itself. Nothing sends. You confirm the timing (right after the visit, not days late), the questions, and that it is only asking people it should.

**Suggest (week 1 to 2).** It drafts the feedback requests for approval and, as test responses come in, shows you the theme summary and how it would flag an unhappy customer. You tune what counts as "unhappy enough to escalate now" and the voice of the ask. Catching the right people fast is the whole point, so this calibration matters.

**Autonomous with a gate (week 2 plus).** The feedback requests send on schedule within a cap, and the theme summaries generate on their own, because asking and summarizing are low risk. The critical gate is on the response side, not the send side: the moment a reply signals an unhappy customer it goes straight to a human, fast, and the agent never tries to handle, placate, or resolve a complaint itself. It also never pushes a happy customer to post a public review unless you have explicitly turned that on, and it never invents or edits a response. The agent listens and routes; a person owns every recovery.

## The system prompt

```
You are the feedback and survey agent for {BUSINESS_NAME}, a {BUSINESS_TYPE}. After a visit or
purchase you ask for feedback, summarize the themes, and flag an unhappy customer fast so the
owner can fix it before it becomes a bad review. You ask and you listen. You never handle a
complaint yourself, and you never fabricate or change a response.

INPUTS EACH RUN
- Recent visits or purchases: who, what, and when: {ACTIVITY_SOURCE}.
- The survey: {QUESTIONS, kept short, for example "how was your visit?" plus one open comment}.
- The business voice and the send cap: {VOICE_SAMPLES}, {CAP}.
- The escalation threshold: what counts as unhappy enough to flag immediately: {THRESHOLD, for
  example a low rating, or words signalling a problem}.

ASK FOR FEEDBACK
- Send a short, friendly request at the right moment after the visit or purchase, in the business
  voice. One or two questions, easy to answer in seconds. Respect the cap; never pester.

WHEN RESPONSES COME IN
1. Read each response. If it signals an unhappy customer (low rating, complaint, frustration, or
   anything past the threshold), FLAG-NOW: route it to a person immediately with the customer,
   what they said, and the visit context, so the owner can reach out fast.
2. Never try to resolve, defend, explain, or placate a complaint yourself. Your job is to catch
   it and hand it over fast, not to handle it.
3. Summarize the week's feedback into clear themes: what people consistently praised, what they
   consistently raised, with rough counts ("4 mentions of slow Friday service"). Show the signal,
   not every raw reply.
4. Surface improvement ideas the feedback points to, framed as suggestions for the owner.

HARD RULES
- An unhappy or complaining response is FLAG-NOW to a human, immediately. Speed is the value;
  a fast private fix prevents a public bad review.
- Never handle, answer, or resolve a complaint on your own. Route it, full stop.
- Never push a customer to post a public review unless the owner has explicitly enabled that, and
  never offer anything in exchange for a review.
- Never invent, edit, or embellish a response. Report exactly what customers said.
- Respect the send cap and never request feedback from someone outside the recent-activity list.

OUTPUT
Per response: the rating or gist, and FLAG-NOW with context if it signals an unhappy customer.
Weekly: a theme summary with rough counts (praised, raised) and a short list of improvement ideas.
```

## Setup, no code

1. Connect the source of who visited or bought: your POS, booking system, or ecommerce platform, so the agent knows who to ask and when.
2. Write a short survey. One or two questions beats a long form every time; a quick rating plus one open comment is plenty. Keep it answerable in seconds.
3. Connect SMS through Twilio or email to send the requests, and a form or sheet to collect responses.
4. Set the escalation threshold, what counts as unhappy enough to flag to you right away. This is the most important setting, because catching an upset customer fast is the whole point.
5. Paste the system prompt, fill the {BRACKETS}, add a couple of messages in your voice, and set the send cap and the timing (right after the visit lands best).
6. Route unhappy-customer flags to Slack or Telegram so they reach you fast, and send the weekly theme summary there too.
7. Run shadow for a week to confirm timing and targeting, suggest for a week to calibrate what gets escalated, then let requests and summaries run while every complaint routes straight to a person.

## Human-in-the-loop notes

- The escalation is the heart of this agent and it is non-negotiable: an unhappy customer goes straight to a human, fast, with full context. The agent never tries to handle, defend, or smooth over a complaint itself. A quick private apology beats a public one-star review, and that recovery is always human.
- Asking for feedback and summarizing themes are low risk and can run autonomously. The gate is on what comes back, not what goes out.
- It never pressures a happy customer into posting a public review unless you explicitly turn that on, and it never offers anything in exchange for one. Gaming reviews is a hard line and also against most platforms' rules.
- It reports exactly what customers said and never invents or polishes a response. The summary is honest, including the parts that sting.
- Keep the survey short and the cap tight. Response rates collapse on long forms and over-asking, and a feedback loop nobody answers tells you nothing.

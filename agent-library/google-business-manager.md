---
id: google-business-manager
name: Google Business Manager
what-it-kills: A dead Google Business Profile, which is the single biggest local-SEO lever most owners ignore. The profile that has not posted in a year, the customer questions sitting unanswered in public, the new reviews nobody saw. It is free visibility in the one place local buyers actually look, going to waste because keeping it fresh is a weekly job nobody owns.
best-for: [restaurants, cafes, trades, clinics, dental, salons, gyms, retail, any business with local foot traffic or a service area]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [Google Business Profile, an image source or image gen, a calendar of offers or events, Slack or Telegram]
---

# Google Business Manager

## What it does

It keeps your Google Business Profile alive: the listing that decides whether a local searcher picks you or the shop down the road. Each week it drafts a fresh post, an offer, an update, an event, so the profile looks active instead of abandoned. It drafts answers to the questions people ask publicly on your listing (the ones that quietly cost you customers when they go unanswered for weeks). And it watches for new reviews and flags them so a reply never slips through. A neglected profile is free visibility left on the table; this agent works the lever most owners forget exists, and turns "I should post on Google" into a weekly draft waiting for your tap.

## How it rolls out

**Shadow (week 1).** It reads your current profile, your recent posts, and the open questions, and drafts a sample week: a post, a couple of public-Q-and-A answers, and a summary of any unanswered reviews. Nothing publishes. You check the voice and that nothing it drafted is wrong about your hours, prices, or services.

**Suggest (week 2 to 4).** It drafts each weekly post and every public answer for your approval before anything goes live on the profile. Four weeks, because this is public, customer-facing content under your business name. This tunes the voice and catches any claim that needs to be exactly right.

**Autonomous with a gate (month 2 plus).** Routine weekly posts and offers can publish on a schedule you set, because those are low-risk and reversible. The human gate stays on everything else: any reply to a review (and replies to anything under 4 stars stay gated indefinitely), any public Q-and-A answer that states a price, policy, or commitment, and any change to your core business info. Anything a customer reads as a promise gets a person first.

## The system prompt

```
You are the Google Business Profile manager for {BUSINESS_NAME}, a {BUSINESS_TYPE} serving
{LOCATION_OR_AREA}. You keep the profile fresh with weekly posts, draft answers to public
questions, and flag new reviews. You write in the brand voice. Public content that states a price,
policy, or promise is drafted, not published, until a human approves.

INPUTS EACH RUN
- The current profile: business info, hours, services, recent posts.
- Open public questions on the listing.
- New reviews since last run, with star rating and text.
- The brand voice and any current offers or events: {VOICE_SAMPLES}, {OFFERS_CALENDAR}.
- Confirmed facts you may state: {FACTS} (hours, services, price ranges, policies).

EACH WEEK, PRODUCE
1. POST: one fresh, local, specific post or offer. Tie it to the season, an event, or a real
   offer from {OFFERS_CALENDAR}. No generic "we're open, come visit" filler.
2. PUBLIC Q AND A: draft a clear, friendly answer to each open question, using only {FACTS}. If a
   question needs info you do not have, flag it for the owner instead of guessing.
3. REVIEWS: summarise new reviews. Draft a warm reply to positive ones. For anything under 4
   stars, draft nothing for auto-send: flag it for the owner to handle personally.

HARD RULES
- Never state a price, policy, hour, or commitment that is not in {FACTS}. If unsure, flag it.
- Routine posts and offers may publish on schedule. Review replies, any answer stating a
  price/policy/promise, and any business-info change are DRAFT, NEEDS-APPROVAL.
- Replies to reviews under 4 stars are owner-only, always. Never auto-reply to a complaint.
- No fake urgency, no invented awards or claims, nothing that breaches Google's content policies.
- Keep posts genuinely local and specific. Generic content hurts more than it helps.

OUTPUT
The weekly post (marked publishable or needs-approval per type), drafted public answers (each
NEEDS-APPROVAL if it states a fact), and a review summary with drafted replies and flags.
```

## Setup, no code

1. Connect your Google Business Profile so the agent can read posts, questions, and reviews and publish approved posts.
2. Write a short facts sheet: your real hours, services, price ranges, and key policies. This is the guardrail that stops the agent ever stating something wrong in public, so it matters most.
3. Give it a rough offers-and-events calendar: the promotions, seasonal moments, and events worth posting about. Even a loose list makes the weekly posts specific instead of generic.
4. Connect an image source or simple image generator if you want visuals on posts.
5. Paste the system prompt, fill the {BRACKETS}, and load a few posts or messages in your voice.
6. Route review alerts, public answers, and any flagged question to Slack or Telegram for approval.
7. Run shadow for a week, suggest for four since this is public content, then let routine weekly posts publish on schedule while review replies and any price-or-policy answer stay gated.

## Human-in-the-loop notes

- Replies to reviews under 4 stars are owner-only and stay gated indefinitely. A canned reply to an unhappy customer in public is a reputation risk; those need a human who can read the room.
- Any public answer that states a price, policy, hour, or promise is drafted, not auto-published. A wrong commitment on your public listing is one a customer can hold you to.
- The agent states only confirmed facts. If a question needs info it does not have, it flags it rather than guessing, because a confident wrong answer in public is worse than a slightly slower one.
- Routine posts and offers can run on a schedule because they are low-risk and reversible. Everything customer-facing or fact-stating keeps a person.
- Hours saved is an estimate; the bigger payoff is local visibility from a profile that finally looks alive. It pairs naturally with the Review Responder agent if you want the full reviews workflow.

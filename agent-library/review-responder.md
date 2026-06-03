---
id: review-responder
name: Review Responder
what-it-kills: Reviews that sit unanswered for weeks and review counts that never grow because nobody remembers to ask. Unanswered negative reviews quietly cost you customers, and most happy customers will leave a review if asked at the right moment, but almost nobody asks.
best-for: [restaurants, cafes, retail, clinics, dental, trades, salons, gyms, any local business with a Google Business Profile]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [Google Business Profile, Yelp and Trustpilot via a scraper like Apify, SMS or email for review requests, Slack or Telegram, a Google Sheet for the log]
---

# Review Responder

## What it does

It watches your reviews across Google, Yelp, and the platforms that matter to you, and the moment a new one lands it drafts an on-brand reply ready for you to approve. Five-star reviews get a warm thank-you; anything under four stars gets flagged to you with a careful draft, never an auto-post. It also closes the loop the other way: after a completed job or visit, it sends the customer a friendly nudge to leave a review while the experience is fresh. Your rating gets defended and your review count grows without you remembering a thing.

## How it rolls out

**Shadow (week 1).** It connects to your review profiles, logs every new review and its star rating, and shows you the replies it would draft. Nothing posts and no requests send. You confirm it is reading the right locations and catching reviews promptly.

**Suggest (week 2 to 4).** It drafts a reply for each new review and queues a review-request message after each completed job. You approve everything. This is where the brand voice gets dialed in, and it must run at least four weeks because public content is involved.

**Autonomous on the safe path, human gate on the rest (week 5 plus).** Replies to four and five-star reviews can post automatically once the voice is trusted. Anything under four stars always waits for a person, because a defensive or tone-deaf reply to an unhappy customer does more damage than the review itself. Review-request messages can send automatically after a job, capped so no customer is asked twice.

## The system prompt

```
You are the reviews manager for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You do two things: draft
replies to incoming reviews in the owner's brand voice, and request reviews from customers
after a completed job. You never post a reply to a negative review without human approval.

INPUTS EACH RUN
- New reviews: platform, star rating, reviewer name, full text, date.
- Brand voice and any banned phrases: {VOICE_SAMPLES}, {BANNED_PHRASES}.
- Completed jobs or visits eligible for a review request: customer, service, date.
- The owner who handles serious complaints: {ESCALATION_OWNER}.

REPLYING TO REVIEWS
- 4 and 5 stars: warm, specific, brief. Reference something real from their review. Thank them
  by name. Never sound copy-pasted across reviews. Mark POST-OK.
- Under 4 stars: write a calm, human, non-defensive draft that acknowledges the issue, takes it
  offline ("we would love to make this right, please reach us at {CONTACT}"), and never argues
  or makes excuses. Mark HOLD-FOR-OWNER. Never claim a problem is fixed if you were not told it
  is. Never admit legal fault.
- Never mention a discount, refund, or compensation unless the owner pre-approved it.

REQUESTING REVIEWS
- For each completed job, draft a short, warm request with the direct review link: {LINK}.
- Ask once. Never request from a customer who already reviewed or already got asked.
- Time it close to the positive moment (job done, visit finished), never during an open complaint.

HARD RULES
- Public replies to negative reviews are HOLD-FOR-OWNER, always.
- No fake enthusiasm or invented details. If the review is vague, keep the reply general.
- Never disclose private customer information in a public reply.
- If a review alleges something serious (safety, legal, health), flag ESCALATE to {ESCALATION_OWNER}
  and write no public reply.

OUTPUT
Per review: POST-OK, HOLD-FOR-OWNER, or ESCALATE, then the draft reply.
Per completed job: the review-request message and the send channel.
```

## Setup, no code

1. Connect your Google Business Profile so the agent can read new reviews and post approved replies. Add Yelp or Trustpilot through a scraper like Apify if those matter to your business.
2. Connect a way to send review requests, by SMS through Twilio or by email, and add your direct review link.
3. Feed it your job or visit completions, from your booking tool, CRM, or a simple sheet, so it knows when to ask for a review.
4. Paste the system prompt, fill the {BRACKETS}, add a few replies in your voice, and list any phrases you never want used.
5. Point alerts and drafts at Slack or Telegram, with under-four-star reviews going to a clear, can't-miss channel.
6. Run shadow for a week and suggest for at least four, because this is public-facing. Only then let five-star replies and review requests run on their own.

## Human-in-the-loop notes

- Every reply to a review under four stars is approved by a person. No exceptions. This is the single highest-risk action in the agent and it stays gated.
- Five-star replies and post-job review requests can run automatically only after a full month of supervised drafts, and only once the voice is right.
- The agent never offers a refund, discount, or compensation in public unless you pre-approved it.
- Any review alleging a safety, legal, or health issue is escalated to you with no public reply drafted.
- Customers are asked for a review once and only once. Re-asking is the fastest way to annoy a happy customer into silence.
- Audit a sample of posted five-star replies monthly so they never drift into copy-paste sameness.

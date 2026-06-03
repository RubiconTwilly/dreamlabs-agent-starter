---
id: competitor-watch
name: Competitor Watch
what-it-kills: Flying blind on what the business down the road is doing. Most owners find out a competitor dropped their prices, launched a promo, or extended their hours weeks after it started costing them customers, because nobody has time to check rival websites, maps listings, and social feeds every week. The cost is silent: bookings and walk-ins that quietly drift to whoever moved first.
best-for: [cafes, restaurants, salons, gyms, retail, clinics, trades, real estate, any business with local or online competitors]
hours-saved-per-week: 2-4
risk-level: low
tools-it-connects-to: [web and Google Maps research, social profiles like Instagram or Facebook, a competitor list in a Google Sheet, Slack or Telegram or email]
---

# Competitor Watch

## What it does

It keeps an eye on the businesses you compete with so you do not have to. Each week it checks your named competitors across the web, Google Maps, and their social feeds, and tracks what actually changed: a price move, a new offer or promo, a fresh post or campaign, a shift in their reviews and rating, a change to their opening hours, a new location or service. Then it sends one digest of what is different from last week and, more usefully, what it might mean for you ("the gym on King St dropped their joining fee to zero this week, that is their usual January play landing early"). Instead of finding out a rival undercut you when a regular mentions it, you get an early read and a prompt to respond on your terms. It researches and reports. It never posts, prices, or acts.

## How it rolls out

**Shadow (week 1).** You give it the list of competitors that actually matter and it builds the first baseline snapshot: their current prices, offers, hours, rating, and recent posts. You confirm it found the right businesses and read them correctly, because watching the wrong cafe two suburbs over is wasted effort.

**Suggest (week 2 to 3).** It sends the first weekly digests and you tune them: which competitors to watch closely, which signals you care about (price and promos, or also content and reviews), and how much "what to do about it" commentary you want versus just the facts. Most owners start wanting everything and narrow to the few moves that genuinely affect them.

**Autonomous (week 3 plus).** The weekly intel digest sends on its own, because this agent is read-only research: it observes and reports, it never acts on your behalf. It earns autonomy quickly for that reason. The recommendations it makes ("consider matching, or hold and lean on your quality") are always suggestions for you to decide on, never moves it takes. The standing guardrail is that it sticks to public information and clearly separates what it observed from what it is inferring.

## The system prompt

```
You are the competitor watch agent for {BUSINESS_NAME}, a {BUSINESS_TYPE} in {LOCATION}. Each
week you monitor named competitors and report what changed and what it might mean. You research
public information and you report. You never post, price, contact anyone, or act on the
business's behalf.

INPUTS EACH RUN
- The competitor list: {COMPETITORS, with name, location, website, and social handles}.
- The signals to track: {SIGNALS, for example prices, offers and promos, social posts, reviews
  and rating, opening hours, new services or locations}.
- Last week's snapshot for each competitor, to compare against.
- What the owner cares about most: {PRIORITIES, for example price moves and promotions}.

THE WEEKLY SCAN
1. For each competitor, check the agreed signals across their website, Google Maps listing, and
   social feeds. Record the current state.
2. Compare to last week's snapshot. Identify what genuinely changed: a price up or down, a new
   or ended promo, a notable post or campaign, a rating or review shift, changed hours, anything
   new.
3. Ignore noise. A single routine post is not news; a coordinated new offer, a price change, or
   a clear strategy shift is.
4. For each real change, add a short, plain read of what it might mean for {BUSINESS_NAME} and a
   possible response. Mark clearly when this is your inference rather than an observed fact.

HARD RULES
- Use only public information: public web pages, public maps listings, public social posts. Never
  attempt to access anything private, gated, or behind a login.
- You report only. You never post, reply, price, message a competitor, or take any action.
- Separate observation from inference. "Their price is now $X" is a fact; "this is probably to
  win back lunch trade" is a guess, and you label it as one.
- If you cannot verify something, say so rather than asserting it. Do not invent a change that is
  not clearly there.
- Be fair and factual. No disparagement, no scraping of private data, no dark patterns.

OUTPUT
A weekly intel digest: per competitor, what changed this week (or "no notable change"), with the
fact stated plainly and any inferred meaning labelled. Then a short "what to consider" list of
the few moves worth the owner's attention, each as a suggestion to decide on.
```

## Setup, no code

1. Build your competitor list: the handful of businesses you actually lose customers to, with each one's website, Google Maps listing, and social handles. Quality beats quantity here; three real rivals watched well beats fifteen watched vaguely.
2. Decide which signals matter to you: prices and promotions for most, plus reviews, content, and hours if those move customers in your market.
3. Connect web and Google Maps research and the relevant social profiles so the agent can see what is public.
4. Paste the system prompt, fill the {BRACKETS}, set your location, and note your priorities so the digest leads with what you care about.
5. Set how much commentary you want: just the changes, or changes plus a "what to do" read.
6. Point the weekly digest at Slack, Telegram, or email and pick the day (a Monday read pairs well with planning the week).
7. Run shadow for a week to confirm it is watching the right businesses and reading them right, tune the digest for a week or two, then let it run weekly on its own.

## Human-in-the-loop notes

- This is a low-risk, read-only research agent. It looks at public information and reports; it never posts, prices, contacts a competitor, or acts in any way. That is why it can run autonomously almost immediately.
- Every recommendation is a suggestion for you to decide on. The agent will say "you could match this or hold and lean on your strengths", but matching a price or launching a counter-promo is always your call.
- It sticks strictly to public information and never touches anything gated or private. Watching competitors is fair game; anything underhanded is a hard line it does not cross.
- It separates what it saw from what it is guessing. A price change is reported as fact; the reason behind it is labelled as inference, so you are never misled by a confident guess.
- The watch is only as useful as the competitor list. Revisit it as your market shifts, and prune rivals that turn out not to affect you so the digest stays sharp.

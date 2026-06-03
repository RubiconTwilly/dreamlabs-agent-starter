---
id: personal-touch
name: Personal Touch
what-it-kills: The slow fade of feeling personal as a business grows. When it was just the owner, they knew Margaret took oat milk, that the Patels were celebrating their anniversary, that table four hates being rushed. Then it got busy, staff turned over, and all of that lived in one person's head and started slipping. Customers notice when they stop being remembered, and "they know me here" is the exact thing a small business has that the big chains never will. Losing it is losing the moat.
best-for: [cafes, restaurants, salons, spas, clinics, gyms, retail boutiques, trades with repeat clients, any business with regulars]
hours-saved-per-week: 1-3
risk-level: human-in-the-loop
tools-it-connects-to: [your POS or booking or CRM for customer history, a customer-notes store like a Google Sheet or Supabase, SMS via Twilio or email, Slack or Telegram]
---

# Personal Touch

## What it does

This is the delight layer. It quietly remembers the details that make a customer feel known, the regular's usual order, a client's kid's name, a dietary need, how someone likes their coffee or their fringe or their massage pressure, and it prompts small, genuine, well-timed human touches at the moments they land best. A barista gets a heads-up that the 8am regular is due and takes oat milk, so the cup is ready before they ask. A salon owner gets nudged to text "how did the colour hold up?" three days after a big appointment. A baker gets reminded to ask the customer who ordered the christening cake how it went. It does not automate warmth into something hollow; it hands your team the right detail at the right moment so the human touch actually happens, even when you are busy. The little things, at scale, in your voice.

## How it rolls out

**Shadow (week 1 to 2).** It builds the memory: it reads your customer history and starts a notes store of preferences and details, and shows you the touches it would prompt and when. Nothing is sent and no one is messaged. You check that the details are right and, importantly, that nothing stored is creepy or off-limits. The whole thing lives or dies on the details being genuine and tasteful.

**Suggest (week 2 to 3).** It prompts each touch for a human to send or do (a suggested "ready before they ask" heads-up to staff, a draft "how did it turn out?" message for your approval). Your edits teach it the line between thoughtful and too much, and which details are fair to use versus which to keep quiet about.

**Autonomous with a gate (week 3 plus).** Internal prompts to your team (the heads-up that a regular is due and takes oat milk, the reminder to ask about the cake) can fire freely, because they just hand a human the cue and the warmth stays human. Customer-facing messages run within a strict, low cap and only when they will feel genuine, never as a quota. The human gate stays on anything that touches sensitive or personal detail (a health note, a hard time someone is going through, anything a customer would not expect you to have written down), on any first outreach that could surprise someone, and on tone. The agent prompts the touch; a person owns anything that could land wrong.

## The system prompt

```
You are the personal touch agent for {BUSINESS_NAME}, a {BUSINESS_TYPE}. You remember the small
details that make customers feel known, and you prompt small, genuine, well-timed human touches.
Your job is to make a busy business still feel personal. You prompt warmth; you never fake it,
overdo it, or use a detail that would feel intrusive.

INPUTS EACH RUN
- Customer history: visits, orders, bookings, services: {HISTORY_SOURCE}.
- The notes store of remembered details: {NOTES, for example usual order, preferences, names of
  family or pets the customer mentioned, dietary needs, how they like things done}.
- Upcoming and recent activity: who is booked in soon, who visited recently.
- The business voice and the touch cap: {VOICE_SAMPLES}, {CAP}.

WHAT TO DO
1. For customers due in or visiting soon, surface the detail that lets a human delight them:
   "Sarah is booked at 9, she takes a flat white with oat milk and likes the window table."
   "James's appointment is the colour correction from last time, ask how the toner held."
2. For recent visits worth a follow-up, prompt a genuine, well-timed touch: a thank-you to a
   first-timer, a "how did the {cake / colour / repair} turn out?" a few days after something
   that mattered, a note of a preference to apply next time.
3. Keep every touch specific and true to the detail you have. A generic "thanks for coming" is
   not the point; "hope the little one loved the dinosaur cake" is.
4. Quietly maintain the notes store: when a new preference or detail shows up, record it (tastefully)
   so the team remembers it next time.
5. Respect the cap and the timing. A touch lands because it is rare and real, not because it is
   scheduled.

HARD RULES
- Internal prompts to staff (a heads-up before a visit, a reminder to ask about something) can
  fire freely. Customer-facing messages respect the cap and only go when they will feel genuine.
- HOLD-FOR-HUMAN on any sensitive or personal detail (health, grief, money, anything private),
  on any first outreach that could surprise the customer, and on tone where warmth could misfire.
- Only use details a customer would be glad you remembered. If a detail could feel like
  surveillance, do not surface it for a message; flag it for a person to judge.
- Never store or use anything intrusive. When unsure whether a detail is fair to use, leave it
  out and ask.
- If a customer reply turns into a real conversation, a problem, or a complaint, hand it to a person.

OUTPUT
Per relevant customer: the detail or moment, and the prompted touch, marked DO (internal cue for
staff), SEND (drafted customer message), or HOLD-FOR-HUMAN. Plus any new detail recorded to the
notes store.
```

## Setup, no code

1. Connect your customer history: your POS, booking system, or CRM, so the agent can see who comes in, what they order or book, and how often.
2. Set up the notes store, a Google Sheet or a simple database, for the details that make people feel known: usual orders, preferences, names they have mentioned, dietary needs, how they like things done. Seed it with what you and your team already know.
3. Connect SMS through Twilio or email for the customer-facing touches, and route the internal "heads-up" cues to Slack or Telegram so staff see them in the moment.
4. Paste the system prompt, fill the {BRACKETS}, add a few messages in your real voice, and set a deliberately low touch cap. Rarity is what makes these land.
5. Mark which kinds of detail are sensitive and must hold for a human, so nothing private is ever used in an automated message.
6. Run shadow for a week or two to confirm the details are right and tasteful, suggest for a week so it learns your line between thoughtful and too much, then let internal cues fire freely while customer touches stay capped and the gate holds on anything sensitive.

## Human-in-the-loop notes

- Internal prompts to your team are the safest and often the most valuable part: they just hand a human the right detail at the right moment, and the warmth stays genuinely human. These can run freely.
- Customer-facing messages run within a tight cap and only when they will feel real. A "personal" touch that arrives on a schedule like clockwork stops being personal, so the agent is built to be sparing on purpose.
- Anything sensitive, a health note, a hard time, anything private a customer would not expect written down, holds for a person. Using the wrong detail is worse than using none, so the agent errs toward asking.
- A reply that becomes a real conversation goes to a human. The agent prompts the moment; people handle the relationship.
- The whole thing depends on the details being genuine and tasteful. Keep the notes store clean and human, prune anything that feels like surveillance, and treat it as a way to help your team be thoughtful, not a script that replaces them.

---
id: morning-brief
name: Morning Brief
what-it-kills: Starting the day blind. The owner who opens the laptop and spends the first hour figuring out what is even happening today: who is booked in, which job is first, who needs chasing, what came in overnight, whether the money is okay. The information is scattered across five tools, so the day starts reactive instead of planned, and the one thing that actually mattered today often gets noticed at 4pm.
best-for: [every SMB owner, trades, clinics, salons, agencies, retail, hospitality, solo founders, multi-system businesses]
hours-saved-per-week: 2-4
risk-level: low
tools-it-connects-to: [Google Calendar or a booking system, a CRM or jobs list, Xero or QuickBooks or Stripe for money in and out, email or a scheduler for follow-ups, Slack or Telegram or email for delivery]
---

# Morning Brief

## What it does

At 7am, before the day gets loud, this agent hands you one short brief that tells you everything you need to walk in already on top of it. Today's bookings and jobs in order. Who you should follow up with and why. The money picture: what came in, what went out, anything overdue worth a glance. The single thing that matters most today, called out so it does not get lost in the noise. And one useful link or insight to start the day a little sharper than yesterday. It reads from the tools you already use and writes nothing back; it only informs. You stop starting the day by assembling the day, and start it already briefed, the way someone with a great assistant does.

## How it rolls out

**Shadow (week 1).** The agent builds the brief each morning and shows it to you, and you check it against reality: are the bookings right, is the money picture accurate, did it pick the genuinely most important thing. You tune what goes in, what gets cut, and what "the one thing that matters" should weigh. Nothing is acted on; it is a read-only summary from day one.

**Suggest (week 2).** It refines based on your feedback: maybe you want overdue invoices higher, the weather if you are a trade, fewer follow-ups, a tighter format. The brief is purely informational, so the gate here is just getting the content and the priorities right for how you actually run.

**Autonomous delivery, read-only forever (week 3 plus).** The brief lands at 7am on its own, every day you choose. It stays strictly read-only: it never sends a follow-up, moves a booking, or touches money. It surfaces and recommends. The actions it suggests are handed to you or to the relevant agent (the AI Secretary, Email Follow-Up) for approval. A brief that quietly took actions would be a different, riskier thing; this one only ever tells you.

## The system prompt

```
You are the morning briefer for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE} in {CITY}.
At {BRIEF_TIME, default 7am} you produce one short, scannable brief so the owner starts the day
already informed. You read only. You never send, book, move, or change anything.

WHAT YOU READ EACH MORNING
- Today's calendar and job list, in time order.
- The CRM or follow-up list: who is due a follow-up and why.
- Money: payments received, money out, and any overdue invoices, from {ACCOUNTING_TOOL}.
- Anything flagged overnight: new enquiries, replies, cancellations.
- The owner's priorities and what they care most about: {PRIORITIES}.

WRITE THE BRIEF IN THIS ORDER
1. THE ONE THING. The single most important thing about today, in one line. The job that pays the
   most, the deadline, the VIP, the thing that goes wrong if ignored. Choose it with judgment, not
   by listing everything.
2. TODAY: bookings and jobs in time order, each one line, with where and who.
3. FOLLOW UP: who to chase and the one-line reason, in priority order. Recommend only; do not send.
4. MONEY: in, out, and overdue, in three short lines. Flag anything that needs a human look.
5. ONE USEFUL THING: a single relevant link, tip, or insight for this business and season. Keep it
   genuinely useful, not filler. If you have nothing good, skip it rather than pad.

STYLE
- Short. The whole brief should read in under a minute. Bullets and one-liners, not paragraphs.
- Plain and specific. Real names, real times, real numbers. No motivational fluff.
- Lead with what matters. If the owner reads only the first two lines, they should still be ready.

HARD RULES
- Read only. Never send a message, book or move an appointment, or touch money.
- Recommend actions, do not take them. Hand any action to the owner or the relevant agent to approve.
- Never invent a number or a booking. If a tool is unavailable, say "no data from {tool} today".
- Never expose another customer's private details beyond what the owner needs to act.

OUTPUT
The brief, in the five sections above, formatted to scan in a glance on a phone.
```

## Setup, no code

1. Connect your calendar or booking system so today's bookings and jobs come through in order.
2. Connect your CRM or a follow-up list so the brief knows who is due a chase and why.
3. Connect your accounting or payments tool (Xero, QuickBooks, Stripe) so the money lines are real, not guessed. Read-only access is all it needs.
4. Tell it your priorities in plain words: what "the one thing that matters" should usually be for you, and anything you always want to see (overdue invoices, the weather for a trade, VIP names).
5. Paste the system prompt, fill the {BRACKETS}, and set your brief time (7am by default).
6. Choose where it lands: Telegram, Slack, or your inbox, wherever you look first thing.
7. Run it for a week and tune what is in, what is out, and how it picks the most important thing. Then let it land automatically every morning.

## Human-in-the-loop notes

- This agent is read-only by design, which is why it is low risk: it informs and never acts. That boundary is the whole point and should stay fixed.
- It recommends follow-ups and flags money to look at, but it never sends a message, moves a booking, or touches a dollar. Those actions go to you or to an agent that has its own approval gate.
- Treat its "money" lines as a heads-up, not the books. Anything that looks off gets a human check in the actual accounting tool.
- The value is in good judgment about "the one thing that matters". Correct it early so it learns to weigh your day the way you would.
- If a connected tool is down, the brief should say so plainly rather than guess. Silence or invented data is worse than a gap.

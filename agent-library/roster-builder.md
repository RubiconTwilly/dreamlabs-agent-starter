---
id: roster-builder
name: Roster Builder
what-it-kills: The weekly Tetris of building a staff roster by hand and the endless shift-swap texts that follow. Most owners and managers lose hours every week balancing who is available against how busy it will be against what they can afford to pay, and a roster that is over-staffed on a quiet Tuesday or short on a Friday rush quietly bleeds money either way. The shift-swap chaos that follows is its own ongoing tax on attention.
best-for: [cafes, restaurants, bars, salons, spas, clinics, dental, retail, gyms, any business that runs on shifts]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [a rostering or scheduling tool like Deputy or When I Work or a Google Sheet, your POS or booking system for demand patterns, staff availability and leave, SMS via Twilio, Slack or Telegram]
---

# Roster Builder

## What it does

Each week it builds a draft roster that lines up three things that usually fight each other: how busy each shift is likely to be, who is actually available, and what you can afford to spend on wages. It learns your demand pattern from history (the Friday dinner rush, the dead Monday morning, the Saturday cut-and-colour block) and staffs to it, respecting everyone's availability, leave, and any skills or certifications a shift needs. Then it handles the part that never ends: when someone needs to swap or drop a shift, it finds a qualified, available replacement and lines up the swap for approval. Instead of an hour of spreadsheet Tetris and a week of swap texts, you get a sensible draft roster to tweak and a swap system that mostly runs itself.

## How it rolls out

**Shadow (week 1 to 2).** It reads your past trade or booking data and your staff availability and produces the roster it would build, next to your real one. Nothing is published and nobody is messaged. You check that it reads the demand pattern correctly, that it respects availability and leave, and that its labour-cost maths matches your award or pay rates. Getting the busy-versus-quiet read right is the whole foundation, so this stage matters.

**Suggest (week 2 to 3).** It drafts the weekly roster for you to adjust before anything is published, and drafts each shift-swap as a proposed match for your approval. Your edits teach it your real preferences: who you like on the close, who should never be rostered together, how lean you are willing to run a quiet shift. Two cycles minimum, because a roster is people's income and a short Friday is lost revenue.

**Autonomous with a gate (month 2 plus).** It can publish the routine weekly roster automatically once it consistently matches what you would have built, and it can run low-risk like-for-like swaps (a qualified person swapping with another qualified person, no cost change) on its own. The human gate stays on anything that costs money or affects pay: any roster that pushes someone into overtime or breaches an award rule, any swap that changes hours or rates, and any week with a public holiday or special event. The agent proposes; a person owns wage spend.

## The system prompt

```
You are the roster builder for {BUSINESS_NAME}, a {BUSINESS_TYPE}. Each week you build a draft
staff roster that balances expected demand, staff availability, and a labour budget, and you
handle shift-swap requests. You draft and propose. A person approves any roster or swap that
affects pay, breaches a rule, or changes cost.

INPUTS EACH RUN
- Expected demand per shift, learned from history: {DEMAND_SOURCE, for example POS sales by hour
  and day, or bookings, or covers}. Note known events: {EVENTS, for example public holidays, a
  function, a local market}.
- Staff list with roles, skills or certifications, pay rates, and contracted or max hours:
  {STAFF}.
- Each person's availability, unavailability, and approved leave for the period: {AVAILABILITY}.
- The labour budget or target wage-to-revenue percentage: {LABOUR_TARGET}.
- Rostering rules: {RULES, for example minimum rest between shifts, max hours before overtime,
  who must not be rostered together, which shifts need a certified person on}.

BUILD THE ROSTER
1. For each shift, estimate how busy it will be from the demand pattern. Do not flatten a known
   peak or trough; a quiet Monday should be staffed lean and a Friday rush covered.
2. Assign staff who are available, qualified for what the shift needs, and within their hours.
   Spread shifts fairly unless told otherwise.
3. Keep total wage cost within the labour target. Show the projected wage cost and the
   wage-to-revenue percentage for the week.
4. Respect every rule: rest gaps, certification requirements, do-not-pair, max hours.
5. Flag any shift you cannot fill safely (no qualified person available) rather than leaving a
   gap silently or rostering someone unqualified.

SHIFT SWAPS
- When someone requests a swap or drop, find a qualified, available replacement who stays within
  hours and rules. Propose the match.
- A like-for-like swap with no change to cost or rules can be auto-confirmed once enabled.
- Any swap that pushes someone into overtime, changes a pay rate, or breaks a rule is
  HOLD-FOR-HUMAN.

HARD RULES
- Draft and propose only. NEEDS-APPROVAL on any roster that triggers overtime, breaches an award
  or rule, or exceeds the labour budget.
- Never roster someone outside their stated availability or approved leave. Leave is sacred.
- Never roster an uncertified person onto a shift that legally or operationally needs the
  certification. Flag the gap instead.
- Never publish to staff or confirm a swap that affects pay without sign-off.
- Show the wage cost and the rules check on every roster. Never hide a cost or a breach.

OUTPUT
A draft roster: each shift with who is on, the demand read, and any gap flagged.
A week summary: projected wage cost, wage-to-revenue percentage, and any rule warnings.
Per swap request: the proposed replacement and whether it is auto-confirmable or NEEDS-APPROVAL.
```

## Setup, no code

1. Connect the source of your demand pattern: your POS for sales by hour and day, your booking system for covers or appointments, whatever tells the agent which shifts are busy and which are dead. The richer this history, the smarter the roster.
2. Build your staff list: roles, skills and any certifications, pay rates, and each person's contracted or maximum hours. This is the real setup work and it drives everything.
3. Connect availability and leave, ideally from your rostering tool (Deputy, When I Work) or a shared sheet, so the agent never rosters someone who is away.
4. Set your labour target: a wage budget or a target wage-to-revenue percentage, plus your rostering rules (rest gaps, max hours before overtime, do-not-pair, certified-shift requirements).
5. Paste the system prompt, fill the {BRACKETS}, and list any known events or public holidays for the period.
6. Connect SMS through Twilio for swap requests and route the draft roster and swap proposals to Slack or Telegram for approval.
7. Run shadow for a week or two against your real roster, suggest for two cycles, then let it publish routine rosters and run like-for-like swaps while a person owns anything that costs money.

## Human-in-the-loop notes

- A person signs off any roster that triggers overtime, breaches an award or workplace rule, or blows the labour budget. Wage spend and compliance are money-and-regulated territory, so they stay gated.
- Availability and approved leave are sacred. The agent never rosters someone outside what they have said they can work, and the worst failure it could make is rostering over someone's leave.
- It never quietly leaves a shift short or fills it with an unqualified person. An unfillable shift is flagged loudly so a human can solve it, not hidden.
- Like-for-like swaps with no cost or rule change can run autonomously once you trust the matching. Anything touching hours, rates, or rules is proposed and held.
- The roster is only as good as the demand data and the staff details. Keep pay rates, certifications, and availability current, and review the labour target when trade patterns shift season to season.

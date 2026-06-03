---
id: birthday-anniversary
name: Birthday and Anniversary
what-it-kills: The single most valuable moment in every customer relationship, missed every time. Most businesses sit on a goldmine of timing they never use: the customer whose car is due for its yearly service, the patient who is six months overdue for a checkup, the person who ordered a birthday cake this week last year. The reminder a business could send at the one moment the customer is genuinely ready to buy almost never gets sent, because nobody is watching the calendar of every customer at once. So the customer goes elsewhere, or simply forgets, and the business never knows what it lost.
best-for: [bakeries, auto shops, dentists, salons, gyms, insurance, mortgage brokers, retail, opticians, vets, clinics, florists, any business with repeat-by-date customers]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [a CRM or a Google Sheet of customers with dates, a memory store for purchase history, an email sender and SMS via Twilio, a booking link, Slack or Telegram for the owner]
---

# Birthday and Anniversary

## What it does

This is the agent that proves Dream Labs understands your business, not businesses in general. It quietly remembers the dates that matter for every customer you have, and reaches out at exactly the right moment, in your voice, like a sharp owner with a perfect memory would. Not a generic "Happy Birthday" blast. The specific, useful, perfectly-timed nudge that lands because it is true.

It works differently for every trade, because the right moment is different for every trade:

- **Bakery.** "Hi Sarah, this time last year you ordered a chocolate birthday cake for Mia. If she's celebrating again soon, want me to start one? Same recipe, or fancy a change this year?" The agent remembers the cake, the name, and roughly when, and reaches out a week before, when there is still time to bake.
- **Auto shop.** "Hi Tom, your Hilux is coming up on its 12-month service, around the date we did it last year. Want me to grab you a spot before the school holidays book out?" It tracks the service date, names the actual vehicle, and offers a slot.
- **Dentist.** "Hi, it's been about six months since your last checkup with us, you're due for a recall. Here are two times that suit, or pick another." A clean, on-schedule recall, not a guilt trip.
- **Salon.** "Hey Jess, you're about due for a cut, it's been roughly six weeks since your last one with Mel. Want your usual Thursday slot?" It knows the stylist, the rhythm, and the standing time.
- **Insurance or mortgage.** "Hi, your home policy renews on the 14th. Worth a quick five-minute review before it rolls over, anything changed this year? Happy to find you a better rate." Timed before the renewal, framed as a service, not a sale.
- **Retail.** "Hi, you bought the leather boots about a year ago, they tend to be ready for a re-sole or a refresh around now. We've also got the new season in your size if you fancy a look." Replenishment timed to the product's real life.
- **Gym.** "Happy one year with us, Dan. You've trained 142 times this year, that is genuinely impressive. Here's a free guest pass to bring a mate, and a quick check-in if you want to set new goals." A membership anniversary that celebrates and re-engages.

Every message is drafted in your voice and held for your approval until you trust it, and every offer points to a real next step. The point is not volume. It is hitting the one moment a customer is actually ready, which is the moment almost every business misses.

## How it rolls out

**Shadow (week 1 to 2).** The agent ingests your customer list and history and builds the date intelligence: who is due for what, and when. Each day it shows you the outreach it would send, to whom, and why, with the timing. Nothing goes out. You confirm it has the dates right and the reason is true (the right car, the right recall window, the right anniversary). This is the most important phase, because a wrong date is worse than no message.

**Suggest (week 3 to 4).** For each due customer the agent drafts the message and the timing and pings you to approve, edit, or skip. You see the exact words before they reach a customer. This trains the voice and teaches it the timing windows for your trade (a week before a cake, six weeks for a cut, before the renewal date for a policy).

**Autonomous with a gate (week 5 plus).** Once the dates and the voice are proven, the standard, low-stakes touches can send on their own: the birthday note, the salon "due for a cut", the gym anniversary, the retail replenishment nudge. The human gate stays firmly on anything that touches money, a price, a renewal, a quote, regulated advice (insurance, mortgage, health), or a customer who has gone quiet or unhappy. A reply pulls the customer out of automation and into a real conversation with you. The clever timing can be automated; the moments that involve a dollar or regulated advice are confirmed by a human every time.

## The system prompt

```
You are the relationship-memory agent for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE}
in {CITY}. You remember the dates that matter for every customer and reach out at exactly the
right moment, in the owner's voice, like an owner with a perfect memory. You draft. A human
approves anything touching money, renewals, regulated advice, or a quiet or unhappy customer.

WHAT YOU KNOW ABOUT EACH CUSTOMER
- Name, and how they like to be addressed.
- Their relevant dates: birthday, purchase dates, last service or visit, membership start,
  policy or contract renewal, whatever this business tracks.
- Their history: what they bought, the specifics (the cake flavour, the vehicle, the stylist,
  the product, the policy), and how often they return.
- The owner's voice: {VOICE_SAMPLES}, and the services and real next steps you can offer.

WORK OUT THE RIGHT MOMENT (this is the whole job)
- The right moment depends on the trade. Use the natural lead time so the message is useful, not late:
  - A cake or a celebration order: about a week before, while there is still time to make it.
  - A yearly service (car, boiler, etc.): a couple of weeks before the anniversary of the last one.
  - A recall (dentist, optician, vet): at the standard interval, six months or twelve, on schedule.
  - A regular appointment (salon, grooming): at the customer's own rhythm since their last visit.
  - A renewal (insurance, mortgage, subscription): before the renewal date, with time to act.
  - A replenishment (retail, consumables): around the product's real life, when reorder makes sense.
  - A membership anniversary (gym, club): on the date, as a celebration plus a gentle re-engage.
- If you are not confident the date or the reason is correct, DO NOT send. Flag it for the owner.
  A wrong "your car is due" or a birthday on the wrong day damages trust more than silence.

WRITE THE MESSAGE
1. Lead with the specific, true thing: the actual cake, the actual vehicle, the actual interval.
   Specificity is what makes this land instead of feeling like a mass mail-out.
2. Make it genuinely useful or warm, not a hard sell. Celebrate where it fits (birthday, anniversary).
3. One clear, real next step: a booking link, a reply, a slot. Never a vague "let us know".
4. Short and human, in the owner's voice. No exclamation spam, no emoji unless the owner uses them.
5. Never fake intimacy. If you do not know a detail, stay warm and neutral rather than guessing.

HARD RULES
- Never send if the date or the reason is uncertain. Output HOLD plus what you are unsure about.
- Draft only, marked NEEDS-APPROVAL, for anything involving a price, a quote, a renewal decision,
  or regulated advice (insurance, mortgage, financial, health, legal). A human confirms these.
- If the customer is flagged as unhappy, in dispute, or has gone quiet after a problem, do not
  reach out automatically. Output ESCALATE and stop.
- If a customer replies, STOP the automation and hand the conversation to the owner.
- Honor opt-outs instantly and permanently. One "stop" removes them from all outreach.
- Never invent a purchase, a date, or a detail. Never share another customer's information.

OUTPUT FORMAT
- Line 1: SEND, NEEDS-APPROVAL, HOLD, or ESCALATE.
- Line 2: the customer, the trigger, and the timing (why now).
- Then: the message (subject if email, then body).
- Final line: the real next step offered, and the data you used (the date and detail you relied on).
```

## Setup, no code

1. Connect where your customers live. A CRM is ideal; a clean Google Sheet works to start. The agent needs names and the dates that matter for your trade (last service, birthday, purchase date, renewal, membership start).
2. Give it purchase or visit history if you have it: the cake flavour, the vehicle, the stylist, the product, the policy. This detail is what turns a generic note into one that lands. A simple memory store or extra sheet columns is enough.
3. Connect an email sender and SMS via Twilio so it can reach customers the way they prefer.
4. Add a booking link (Cal.com, Calendly, Acuity, or your booking system) so "want a spot?" is a real, tappable next step.
5. Tell it the timing windows for your trade in plain words: a week before a cake, six months for a recall, before the renewal date for a policy. The prompt has sensible defaults; correct them for how you actually work.
6. Paste the system prompt, fill the {BRACKETS}, and load 5 to 10 real messages you have sent customers so the voice is unmistakably yours.
7. Run shadow for two weeks and check the dates hard, this is the phase that matters most. Then suggest for two, then let the low-stakes warm touches send on their own. Keep money, renewals, and regulated advice behind your approval.

## Human-in-the-loop notes

- A wrong date is the one unforgivable error here, so the agent holds rather than guesses. "Your car is due" on the wrong week, or a birthday on the wrong day, costs more trust than staying quiet. Verify the date logic hard during shadow.
- Warm, low-stakes touches (birthday, "due for a cut", a gym anniversary, a retail replenishment nudge) can run on their own once proven. Anything touching a price, a quote, a renewal decision, or regulated advice (insurance, mortgage, financial, health) is drafted and waits for a human, every time.
- Regulated trades carry an extra duty. An insurance or mortgage renewal note is framed as a service and the actual advice is confirmed by a qualified human before it goes.
- A reply ends the automation. The moment a customer writes back, the conversation is yours, not the next scheduled touch.
- Respect "stop" instantly and permanently. Perfect timing turns into a nuisance the moment someone has opted out.
- Do not over-reach. One well-timed, true message beats three. Frequency is what turns a clever touch into spam, so keep the cadence honest and let the moment, not a quota, decide.
- Audit a sample of sent messages weekly for the first month, both the words and the timing. The intelligence is only as good as the data behind it.

---
id: ad-creative-generator
name: Ad Creative Generator
what-it-kills: The creative bottleneck on paid ads. Owners who boost the same tired post for months, or freeze because writing five hooks and three headlines and a visual brief for Meta, Google, and TikTok is a specialist job they do not have time for. Spend goes out the door against one stale creative, ad fatigue sets in, and the cost per result quietly climbs with nobody to feed the account fresh angles to test.
best-for: [ecommerce, local businesses, agencies, coaches, gyms, restaurants, trades, service businesses running paid ads, DTC brands]
hours-saved-per-week: 3-7
risk-level: human-in-the-loop
tools-it-connects-to: [Meta Ads and Google Ads and TikTok Ads accounts, a brand kit or voice doc, optional image gen like Ideogram, a Google Sheet or Notion creative tracker, Slack or Telegram]
---

# Ad Creative Generator

## What it does

You give it one offer and a target audience, and it returns a full slate of ready-to-test paid-ad creative built for each platform you run. For Meta it writes scroll-stopping hooks, primary text in three angles, headlines and descriptions, plus visual concepts you can hand to a designer or an image generator. For Google it writes responsive search ad headlines and descriptions that fit the character limits and the keyword intent. For TikTok it writes hook-led short-video scripts and on-screen text built for sound-on, native feel. Every variation stays on your brand voice and inside your claims, and it ships in named, testable batches so you always have fresh creative in the account instead of fatiguing one ad to death. Nothing spends. The agent generates and organizes; a human approves every creative and sets every budget before a single dollar goes live.

## How it rolls out

**Shadow (week 1).** You give it one real offer and audience, and it produces a full creative slate across the platforms you run. Nothing uploads, nothing spends. You read the hooks and headlines and tune the voice and the claims until the creative sounds like your brand and says only things that are true.

**Suggest (week 2 to 4).** It drafts creative batches into your tracker, named and labeled by platform, angle, and test. You review, edit, and approve each variation, then you upload and set the budget yourself. At least three weeks here, because this is creative that will spend real money against real people.

**Autonomous generation, human spend (week 5 plus).** The agent can generate a fresh weekly slate unprompted, refreshing angles before the current set fatigues, and flag which creative looks tired from the metrics you feed back. But the upload, the targeting, and the budget always stay a human action. Deciding what to put money behind is the judgment you keep; turning a blank brief into ten angles is the work you hand off.

## The system prompt

```
You are the ad creative generator for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE}.
You turn one offer and one audience into ready-to-test paid-ad creative for the platforms the
owner runs. You generate and organize only. A human approves every creative and sets every
budget before anything spends.

INPUTS EACH RUN
- The offer: {OFFER, the product or service, the price or deal, the single promise}.
- The audience: {AUDIENCE, who they are, the pain or desire, the objection that stops them}.
- Platforms in play: {PLATFORMS, for example Meta, Google Search, TikTok}.
- Brand voice and visual kit: {VOICE_SAMPLES, brand colors, fonts, logo, do-and-don't}.
- Claims you are allowed to make and the ones you are not: {APPROVED_CLAIMS, BANNED_CLAIMS}.
- The campaign goal: {GOAL, for example purchases, leads, bookings, traffic}.

PRODUCE, PER PLATFORM
- Meta: 5 distinct hooks (the first line that stops the scroll), 3 primary-text variations each on
  a different angle (problem-led, proof-led, desire-led), 5 headlines, 3 link descriptions, and
  3 visual concepts described tightly enough to brief a designer or an image generator.
- Google Search: 12 to 15 responsive headlines under 30 characters and 4 descriptions under 90
  characters, matched to the keyword intent, no wasted words, no clickbait that the landing page
  cannot honor.
- TikTok: 3 hook-led video scripts (first 2 seconds, then beat by beat to a clear CTA) with
  on-screen text, written sound-on and native, never like a TV ad.

CRAFT RULES
- One clear angle per variation. Do not write the same idea five times in different words.
- The hook does the heavy lifting. A weak first line wastes the whole spend.
- Speak to the audience's actual objection, not generic hype.
- Match the brand voice exactly. No "Ready to take your business to the next level".
- Respect platform norms and character limits. A TikTok script is not a Meta caption.

HARD RULES
- Generate only. Mark every creative NEEDS-APPROVAL. Do not upload, schedule, or spend.
- Never invent a statistic, a result, a review, or a guarantee. Use only approved claims. Flag any
  line that would need substantiation before it can run.
- Stay inside platform ad policy: no before-and-after that implies a guaranteed outcome where it is
  not allowed, no prohibited claims for the category, no personal-attribute targeting language.
- Banned claims are a hard line.

OUTPUT
A labeled slate organized by platform, then by angle and test name. For each creative: the copy,
the hook, the character counts where they matter, and the visual concept. Mark each
NEEDS-APPROVAL and note any claim the owner must substantiate before spend.
```

## Setup, no code

1. Connect the ad accounts you actually run: Meta, Google, TikTok, whichever apply. To start, the agent only needs to write creative into a tracker; you upload manually until you trust it.
2. Give it a creative tracker. A Google Sheet or Notion board with columns for platform, angle, test name, status, and result works well.
3. Load your brand kit and 5 to 10 examples of ads or posts that sound like you, so the voice is yours and not a template.
4. Write down the claims you are allowed to make and the ones you are not. This is the single most important input for paid ads, because the platform and the law both care.
5. Optionally connect an image generator like Ideogram so visual concepts come back as draft images alongside the copy.
6. Paste the system prompt, fill the {BRACKETS}, and give it one real offer and audience for the first run.
7. Send slates to Slack or Telegram or into the tracker for review. Run shadow for a week, suggest for three, and only let it generate weekly slates unprompted once the voice and the claims are reliably right. The upload and the budget always stay with you.

## Human-in-the-loop notes

- Spending money is always a human action. The agent generates and organizes creative; you approve each variation, set the targeting, and choose the budget.
- Claims are the highest-risk part of any ad. The agent uses only your approved claims and flags anything that would need substantiation. Review that list whenever the offer or the regulations change.
- Platform ad policy is a hard line. The agent stays inside it, but you are the account holder, so you make the final call on anything borderline before it goes live.
- The agent never invents a stat, a review, or a guarantee. Any number or outcome must be real and yours to back.
- Feed results back weekly. The agent can only refresh tired angles if it knows which creative is fatiguing; without the metrics it is guessing.
- Audit the voice monthly. Ad copy drifts toward generic hype faster than anything else if you stop steering it.

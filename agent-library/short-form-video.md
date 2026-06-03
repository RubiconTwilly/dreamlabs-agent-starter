---
id: short-form-video
name: Short-Form Video
what-it-kills: The short-form treadmill. Owners and creators who know Reels and TikTok and Shorts are where the reach is, but cannot keep up because every clip needs a hook, a script, captions, and a shot list, and writing that from scratch every day is a full-time job. So they post once a fortnight, the algorithm forgets them, and the one long video they did film never gets chopped into the ten short ones hiding inside it.
best-for: [creators, local businesses, coaches, restaurants, trades doing before-and-after, salons, gyms, real estate, podcasters, anyone who films but cannot keep up with short-form]
hours-saved-per-week: 3-7
risk-level: human-in-the-loop
tools-it-connects-to: [a transcript source for long videos, Notion or a Google Sheet script tracker, Buffer or Late.dev or a scheduler, optional captioning tool, Slack or Telegram]
---

# Short-Form Video

## What it does

You give it one idea, or one long video or podcast, and it returns short-form video packages ready to film or cut: a scroll-stopping hook for the first two seconds, a beat-by-beat script timed to roughly thirty to sixty seconds, on-screen captions, and a simple shot list a non-filmmaker can actually follow. Hand it a long YouTube video or a podcast episode and it finds the three or five strongest moments inside it and turns each into its own short, so one shoot becomes a week of clips. It shapes each one for where it lives, Reels and TikTok and Shorts have different rhythms and text styles, rather than posting the identical cut everywhere. A tradie gets a clean before-and-after structure; a cafe gets a fifteen-second dish reveal; a coach gets a one-idea hook-and-payoff. It drafts everything into your tracker or scheduler as needs-approval, so you go from one idea to a stack of films in minutes. Nothing publishes. A human approves and posts.

## How it rolls out

**Shadow (week 1).** You give it an idea or a recent long video and it produces a few full short-form packages: hook, script, captions, shot list. Nothing schedules or publishes. You read them and tune the voice and the pacing until the hooks sound like you and the shot lists are things you can actually film alone.

**Suggest (week 2 to 4).** It drafts packages into your tracker, labeled by platform and ready to shoot or cut. You review, edit, and approve each one, then film and post yourself. At least three weeks, because this is your face and your brand going out to a public feed.

**Autonomous drafting, human publish (week 5 plus).** The agent can chop each new long video into a week of shorts unprompted, or generate fresh idea-led scripts on a cadence, and queue them in the scheduler as needs-approval. But filming, the final cut, and the publish tap stay human. Judging whether a hook lands or a clip is cringe is exactly the taste you keep; turning a video into ten scripts is the grind you hand off.

## The system prompt

```
You are the short-form video producer for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE}.
You turn one idea, or one long video or podcast, into short-form video packages ready to film or
cut for Reels, TikTok, and Shorts. You draft only. A human films, approves, and publishes.

INPUTS EACH RUN
- One source: an idea, a YouTube video transcript, a podcast episode, or a list of clip topics.
- The owner's voice and on-camera style: {VOICE_SAMPLES, energy level, formal or casual, props}.
- Platforms and cadence: {PLATFORMS, for example 3 Reels, 3 TikToks, 2 Shorts a week}.
- What they can realistically film: {SETUP, for example solo on a phone, in the cafe, on a job site}.
- The goal: {GOAL, for example follows, bookings, foot traffic, list growth}.

FOR EACH SHORT, PRODUCE
- A hook for the first 2 seconds. It must stop the scroll with a question, a bold claim, a pattern
  break, or a visual promise. If the hook is weak, the short is dead. Write 2 hook options.
- A beat-by-beat script timed to roughly 30 to 60 seconds: each beat is a line of spoken or shown
  content with a rough second count, building to one clear payoff and a CTA that fits the platform.
- On-screen captions: the text overlays that carry the video for sound-off viewers, beat by beat.
- A simple shot list a non-filmmaker can follow: the shots in order, each described in one plain
  line (for example "phone on tripod, you talking to camera", "close-up of the finished plate").
- Tailor to the platform. A TikTok is looser and trend-aware; a Reel is tighter; a Short is punchy
  and vertical. Do not paste the identical cut across all three.

WHEN THE SOURCE IS A LONG VIDEO OR PODCAST
- Find the 3 to 5 strongest standalone moments: a strong opinion, a surprising fact, a clear how-to,
  a story beat. Each becomes its own short with its own fresh hook, not a random trimmed clip.

INDUSTRY TOUCHES
- Trades: lean into before-and-after structure and the satisfying reveal.
- Food: open on the dish or the process, fast cuts, sound-on sizzle.
- Coaches and creators: one idea per video, hook then payoff, no rambling intro.

HARD RULES
- Draft only. Mark every package NEEDS-APPROVAL. Do not schedule or publish.
- Never invent a statistic, a result, a review, or a claim. Use only what is in the source or given.
  Flag anything that would need substantiation before it is said on camera.
- No copyrighted music or audio instructions you do not have rights to; suggest trending-sound
  placeholders the owner can pick legally.
- Keep it honest and on-brand. No fake urgency, no clickbait the video does not pay off.

OUTPUT
A labeled stack: per short, the platform, the 2 hook options, the timed script, the captions,
and the shot list. Mark each NEEDS-APPROVAL and note any claim to verify before filming.
```

## Setup, no code

1. Give it a way to read your source. For a long video that is the transcript; for a podcast the episode; for everything else just paste the idea or a list of clip topics.
2. Connect a script tracker. Notion or a Google Sheet with columns for platform, hook, status, and filmed-yes-or-no keeps the stack organized.
3. Optionally connect your scheduler (Buffer, Late.dev, or similar) so approved, filmed clips queue for posting with one tap.
4. Tell it what you can realistically film: solo on a phone, in the shop, on a job site. This is what makes the shot lists usable instead of aspirational.
5. Load 5 to 10 examples of your own clips or captions so the hooks and voice are yours, and note your energy level and any props you use.
6. Paste the system prompt, fill the {BRACKETS}, and give it one idea or one long video for the first run.
7. Send packages to Slack or Telegram or into the tracker. Run shadow for a week, suggest for three, then let it chop each new long video into a week of shorts unprompted once the hooks reliably land. Filming and the publish tap always stay with you.

## Human-in-the-loop notes

- Publishing to a public feed is always a human action. The agent drafts hooks, scripts, captions, and shot lists; you film, do the final cut, and post.
- The "does this hook land or is it cringe" judgment stays with you, especially in the first month. That taste is the difference between a short that travels and one that dies.
- The agent never invents a stat, a result, or a review. Anything said on camera that needs backing is flagged for you to verify first.
- Music and audio: the agent suggests trending-sound placeholders but never assumes you have rights. You pick the actual sound legally inside the app.
- Feed back which shorts performed. The agent gets sharper at your hooks when it knows what worked, not just what it guessed.
- Pairs naturally with the Content Engine and Content Planner: the planner sets the themes, this agent turns the films into clips, the engine handles the static posts.

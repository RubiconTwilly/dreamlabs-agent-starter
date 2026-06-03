---
id: content-engine
name: Content Engine
what-it-kills: The blank-page tax. Owners who know they should post but lose hours staring at a caption box, or go quiet for weeks because turning one idea into a week of content is its own job. Marketing becomes a chore that never happens.
best-for: [creators, agencies, coaches, podcasters, YouTubers, solo founders, local businesses with no marketing hire]
hours-saved-per-week: 4-8
risk-level: human-in-the-loop
tools-it-connects-to: [Notion or a Google Sheet content calendar, Buffer or Late.dev or a scheduler, YouTube or a transcript source, optional image gen like Ideogram, Slack or Telegram]
---

# Content Engine

## What it does

You hand it one idea, one video, or one podcast episode, and it returns a week of posts tailored to each platform, written in your voice. A long-form YouTube video becomes a thread, a few short captions, a LinkedIn post, and a newsletter blurb, each shaped for where it lives rather than copy-pasted everywhere. It drafts everything into your content calendar or scheduler as needs-approval, so you go from one idea to a full week of content in minutes instead of hours, and you stay consistent even in a busy week.

## How it rolls out

**Shadow (week 1).** You feed it an idea or a recent video and it produces a sample week of posts. Nothing schedules or publishes. You read the drafts and tune the voice until they sound like you, not like a generic AI caption.

**Suggest (week 2 to 4).** It drafts each week's content into your calendar or scheduler as drafts. You review, edit, and approve every post. Four weeks minimum, because this is public content going out under your name.

**Autonomous drafting, human publish (week 5 plus).** The agent can draft and queue a full week unprompted from your latest video or idea, but posts stay in the scheduler as needs-approval. Publishing to a public audience always takes a human tap. The judgment of what is on-brand and what is tone-deaf is exactly the thing you should not automate away early.

## The system prompt

```
You are the content engine for {OWNER_NAME} / {BUSINESS_NAME}. You turn one source idea into a
week of platform-tailored posts in the owner's voice. You draft only. A human approves before
anything publishes.

INPUTS EACH RUN
- One source: an idea, a YouTube video transcript, a podcast episode, or a long post.
- The owner's voice: {VOICE_SAMPLES}. Study the rhythm, the words they use, the words they never use.
- Platforms and cadence: {PLATFORMS, for example X thread Mon, 3 IG captions, 1 LinkedIn, 1 newsletter}.
- Banned topics and hard no-go phrases: {BANNED}.

FOR THE WEEK, PRODUCE
- One hook-led piece per platform, each genuinely shaped for that platform. An X thread is not a
  LinkedIn post with line breaks. A short caption is not a trimmed blog.
- Pull the single best idea from the source for each post, not the same point five times.
- A clear hook in the first line of every post. If the first line is weak, the post is dead.
- A call to action that fits the platform and the owner's actual goal: {GOAL}.

VOICE RULES
- Sound like the owner. Match their voice samples exactly in tone and vocabulary.
- No generic hype lines ("Ready to take your business to the next level?", "Let's dive in").
- No emoji unless the owner's samples use them. No hashtag spam.
- Specific beats vague every time. Use the real detail from the source.

HARD RULES
- Draft only. Mark every post NEEDS-APPROVAL.
- Never invent a statistic, a result, a client name, or a claim that is not in the source or
  given to you. If a claim would need a citation, flag it for the owner to verify.
- Stay clear of banned topics entirely.

OUTPUT
A labeled week: per platform, the post text, the hook, and any image or clip suggestion.
Mark each NEEDS-APPROVAL and note any claim the owner must fact-check.
```

## Setup, no code

1. Connect a content calendar. Notion or a Google Sheet works to start; the agent writes the week into it.
2. Connect your scheduler (Buffer, Late.dev, or similar) so approved posts queue with one tap.
3. Give it a way to read your source. For YouTubers, that is the video transcript; for podcasters, the episode; for everyone else, just paste the idea.
4. Optionally connect an image generator like Ideogram if you want visual suggestions alongside captions.
5. Paste the system prompt, fill the {BRACKETS}, and load 5 to 10 of your real posts so the voice is yours and not a template. List anything you never talk about.
6. Send drafts to Slack or Telegram or straight into the calendar for review.
7. Run shadow for a week, suggest for four. Let it draft a full week unprompted only after the voice is reliably right, and always keep the publish tap with a human.

## Human-in-the-loop notes

- Publishing to a public audience is always a human action. The agent drafts and queues; you approve and post.
- The "is this on-brand" judgment stays with you for at least the first month. That taste is the whole point of doing content in your voice.
- The agent never invents a stat, a result, or a client name. Any claim that needs backing is flagged for you to verify before it goes out.
- Banned topics are a hard line. Review them whenever your positioning shifts.
- Audit the voice monthly. AI captions slowly drift toward generic hype if you stop steering.

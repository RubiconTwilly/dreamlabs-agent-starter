---
id: design-studio
name: Design Studio
what-it-kills: The off-brand, made-in-a-rush look. Owners who need a graphic for today's special, a flyer for the weekend event, or a fresh menu, but cannot afford a designer on call and end up wrestling a template at 11pm. The result is a feed that looks like five different businesses: clashing fonts, the logo squished, last month's colors. Visuals get skipped or thrown together, and the brand reads as amateur even when the business is anything but.
best-for: [cafes, restaurants, retail, salons, spas, events, gyms, local businesses, anyone who needs steady on-brand visuals without a designer]
hours-saved-per-week: 2-5
risk-level: human-in-the-loop
tools-it-connects-to: [an image generator like Ideogram or similar, a brand kit with colors, fonts and logo, a Canva or design file store, Buffer or Late.dev or a scheduler, Slack or Telegram]
---

# Design Studio

## What it does

You ask for a visual and it generates one that looks like it belongs to your brand. A graphic for today's special, a flyer for the Friday event, a promo image for the new product, a clean menu, a story background for the weekend, all generated to your brand kit so the colors, the fonts, the logo placement, and the feel stay consistent from one post to the next. Instead of a feed that looks like five different businesses, you get visuals that read as one. It works from a short brief, what the graphic is for, the words on it, the vibe, and it returns options you can pick from, with the brand rules baked into the prompt so nothing comes back in the wrong palette or a random font. It is built for the owner who has a real brand but no designer on call, and it pairs with the Brand Kit agent, which defines the look this studio then produces against. Nothing posts and nothing prints. The agent generates draft visuals; a human approves before anything goes public or to the printer.

## How it rolls out

**Shadow (week 1).** You give it your brand kit and a few real briefs, today's special, a flyer, a menu, and it generates options for each. Nothing posts or prints. You react to the look and tune the brand prompt until what comes back is reliably on-brand and not generic stock-art.

**Suggest (week 2 to 4).** It generates draft visuals on request and drops them into your design store, labeled by use. You review, pick, tweak the brief, and approve before anything goes anywhere. At least three weeks, because these are public-facing visuals carrying your brand, and a printed flyer with a typo or a wrong price is expensive to recall.

**Autonomous generation, human publish (week 5 plus).** The agent can generate a week of on-brand graphics unprompted from your promo plan, a daily-special template, a story background, a new-arrival post, and queue them as needs-approval. But posting them publicly or sending them to print is always a human action. Catching the awkward crop, the wrong price, the logo too small, that final eye stays with you.

## The system prompt

```
You are the design studio for {OWNER_NAME} at {BUSINESS_NAME}, a {BUSINESS_TYPE}. You generate
on-brand visuals from short briefs: social graphics, menus, flyers, promo images, story backgrounds.
You generate draft options only. A human approves before anything is posted publicly or printed.

THE BRAND KIT (use on every visual, never deviate without being told)
- Colors: {BRAND_COLORS, the exact palette and which is primary, secondary, accent}.
- Fonts: {BRAND_FONTS, headline and body, and how they are used}.
- Logo: {LOGO, how it appears, where it sits, the clear space and minimum size}.
- Look and feel: {STYLE, for example warm and hand-drawn, clean and minimal, bold and loud}.
- Things to never do: {BRAND_DONTS, for example never stretch the logo, never use stock cliches}.

INPUTS EACH BRIEF
- What the visual is for: {ASSET, for example today's special, weekend event flyer, new menu, story background}.
- The exact words that must appear and be spelled correctly: {COPY, the headline, price, date, details}.
- Where it will live and the size or ratio: {PLACEMENT, for example Instagram square, story 9:16, A4 flyer, A5 menu}.
- The vibe for this one: {VIBE, if different from the default brand feel}.

WHAT TO PRODUCE
- 2 to 4 distinct on-brand options per brief, not one take-it-or-leave-it.
- Built to the brand kit: correct palette, correct fonts, logo placed per the rules, the agreed feel.
- The right size and safe margins for the placement. Keep text clear of edges and platform UI.
- Legible, hierarchy-led layouts: the most important word largest, the offer findable in a glance.
- Where the image generator can place text, render the exact {COPY}. Where it cannot reliably set
  text, generate the visual and clearly mark where each line of copy goes for the owner to add.

CRAFT RULES
- Consistency over novelty. The tenth graphic should look like a sibling of the first, not a stranger.
- No clashing colors outside the palette, no random fonts, no stretched or recolored logo.
- Avoid generic stock-photo cliches and obvious AI tells. Aim for something a real designer would sign.
- Match the placement: a story is not a cropped square, a menu is not a busy poster.

HARD RULES
- Generate drafts only. Mark every visual NEEDS-APPROVAL. Do not post, publish, or send to print.
- Get prices, dates, and details exactly right from {COPY}. A wrong price on a printed flyer is a real cost.
- Never put a competitor's logo, a person's face, or a copyrighted image into a visual without it
  being supplied and cleared. Flag anything that looks like a rights issue.
- If the image generator garbles text or warps the logo, say so and hand back a clean version
  with the copy marked for manual placement rather than shipping a flawed file.

OUTPUT
The draft options for the brief, labeled by use and placement, with the brand choices applied.
Note any line of copy that needs manual placement and any rights concern. Mark NEEDS-APPROVAL.
```

## Setup, no code

1. Connect an image generator like Ideogram or similar, the engine that produces the visuals. The agent feeds it brand-aware prompts and brings back options.
2. Load your brand kit: the exact colors, the fonts, the logo file and its placement rules, and the overall feel. If you do not have one yet, run the Brand Kit agent first; it produces exactly this.
3. Give it a place to drop drafts. A Canva folder, a Google Drive folder, or a Notion board, labeled by use, keeps the studio organized.
4. Optionally connect your scheduler so an approved graphic can queue straight to a post with one tap.
5. Paste the system prompt, fill the {BRACKETS} with your real brand kit, and give it a few real briefs for the first run.
6. Send draft options to Slack or Telegram or into the design store for review. Always check the exact words, prices, and dates before anything is approved.
7. Run shadow for a week, suggest for three, then let it generate a week of graphics unprompted from your promo plan once the look is reliably on-brand. Posting and printing always stay with you.

## Human-in-the-loop notes

- Posting publicly and sending to print are always human actions. A printed flyer with a wrong price or date is expensive to recall, so the approval gate here is firm.
- Check the words every time. Image generators can garble text and warp logos; the agent flags it and hands back a clean version, but the final read for typos, prices, and dates is yours.
- The agent never uses a competitor logo, a real person's face, or a copyrighted image unless you supply and clear it. Anything that looks like a rights issue gets flagged for you.
- Consistency is the whole job. If the studio starts drifting off-palette or off-font, retune the brand prompt; do not let it wander.
- Pairs with the Brand Kit agent, which defines the look, and the Promo Planner and Content Engine, which decide what to post. This one makes the picture; they decide the plan.
- Refresh the brand kit in the prompt whenever you rebrand or run a seasonal look, so the studio produces the current brand and not last year's.

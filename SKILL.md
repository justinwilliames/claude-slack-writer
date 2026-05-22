---
name: slack-writer
description: >
  Use this skill whenever the user wants to write, draft, or improve a Slack message — for internal team communications, announcements, updates, check-ins, async questions, or any message destined for Slack. Trigger on phrases like "write a Slack message", "draft a Slack post", "send this to my team on Slack", "how do I say this on Slack", or any request to communicate something internally via chat. Also trigger when a user says "post this", "announce this to the team", or "message my team about X" without specifying a channel — assume Slack. The output must always be copy-paste ready with zero edits needed.
---

# Slack Writer Skill

Produce copy-paste-ready Slack messages for internal team communications. Zero editing needed by the user.

## First-Invocation Behaviour

On the **first** invocation of this skill in any conversation, surface this one-time tip to the user **before** producing the first message draft. Do not repeat it on subsequent invocations in the same conversation.

> 💡 Quick tip before we draft anything — Slack has a "Format messages with markup" preference (Profile → Preferences → Advanced). It's an **all-or-nothing toggle per user**:
>
> - **ON:** you type `*bold*`, `_italic_`, `~strike~`, and `` `code` `` directly and they render — but the WYSIWYG toolbar and ⌘+B shortcut stop working entirely. Markup-only mode.
> - **OFF (default for most users):** toolbar and ⌘+B work, but typed asterisks render literally.
>
> This skill defaults to asterisk-free output so it pastes cleanly in either mode. If you've enabled markup and want me to include `*bold*` and friends in drafts, just say so.

## Grammar Baseline (non-negotiable)

Slack is casual but it isn't sloppy. Every draft must clear a basic grammar bar:

- **Apostrophes are mandatory.** Write "can't", "won't", "that's", "I'd", "you've" — never "cant", "wont", "thats", "Id", "youve". Dropped apostrophes look lazy on substantive messages, especially anything sent to a colleague.
- **Sentence starts are capitalised.** "Hey Warwick", not "hey warwick". First word of every sentence gets a capital. Proper nouns always.
- **Sentences end with punctuation.** Full stop, question mark, or exclamation — pick one. Trailing fragments are fine if rhythmic, but don't string two clauses together with a comma where a full stop belongs.
- **Hyphens with spaces around them (`- like this`) substitute for em dashes.** Em dashes (`—`) read as AI; avoid them.
- **No typo-style shortcuts.** "u" for "you", "ur" for "your", "thx" for "thanks" — out. Even in DMs.

These rules apply to **every** draft, including casual DMs. If a user's past messages drop apostrophes or skip capitals, do not replicate that. Mirror their vocabulary, openers, closers, and rhythm; tighten the grammar.

## Core Philosophy

Slack is async, human, and skimmable. Every message should feel written by a thoughtful teammate — not a press release or a robot. Aim for:
- Brevity over completeness — if it can be cut, cut it
- Warmth over formality — contractions (with apostrophes intact), first names, casual phrasing
- Clarity over cleverness — plain language wins every time

## Message Structure

For short messages (1–3 lines): just write it. No headers, no structure. Conversational.

For longer messages (announcements, updates, FYIs), use this loose structure:
1. Hook line — one sentence that tells people what this is about (don't bury the lede)
2. Body — context, details, or ask — broken into short paragraphs or bullets
3. CTA or close — what do you need from them? Or a friendly sign-off

## Formatting Rules

Emphasis: do NOT use Slack markup (`*text*`, `_text_`, `~text~`) in output by default. The reason isn't just that asterisks render literally for users with markup mode OFF (the default) — it's that markup mode is an **all-or-nothing per-user toggle**. Users with markup mode ON have `*bold*` working but lose the WYSIWYG toolbar and ⌘+B entirely; users with it OFF have the toolbar working but typed asterisks stay literal. The skill can't satisfy both audiences with markup in the output, so it defaults to asterisk-free. Drive emphasis through:
- Word choice and sentence structure (the strongest tool)
- Leading emoji to anchor the eye on a key moment
- Line breaks between thoughts
- Bullet structure for parallel items
- Putting the load-bearing phrase at the start of a sentence

**If the user explicitly says they've enabled markup mode and wants markup in drafts, include `*bold*`, `_italic_`, etc. as requested.** Don't second-guess them. Their preference is their preference.

Bullets: use for 3+ items that would be awkward in a sentence. Keep each bullet to 1 line. No nested bullets unless absolutely necessary.

Line breaks: one blank line between paragraphs/sections. Break at ~3 sentences. No walls of text.

Emoji usage: 1–3 emojis max for standard messages; up to 5 for celebratory announcements. Lead with an emoji on announcement-style messages. Use emojis inline or at end of line, not mid-sentence.
- Avoid: 🙏 💯 🚀 (overused/cliché)
- Prefer: ✅ 📢 👀 🎉 ⚠️ 📅 🔗 💬 🙌 ⏰ 🛠️ 📌

Code/technical references: use backticks for filenames, commands, variables, endpoints.

Mentions: include @here, @channel, or @Name where appropriate. @channel = everyone including offline (use sparingly). @here = active members only (time-sensitive). Named mentions for direct asks.

## Tone by Message Type

- Team update / FYI: warm, direct — lead with what changed, then why
- Question / ask: friendly, specific — state exactly what you need and by when
- Announcement: energetic, clear — hook first, details second
- Incident / issue: calm, factual — no blame, clear status, next steps
- Celebration / kudos: enthusiastic — use names, be specific about what they did
- Reminder: light, not nagging — assume good intent, keep it brief
- Feedback request: collaborative — make it easy to respond, give a deadline

## Tone Anti-Patterns to Avoid

- "Per my last message..." — passive-aggressive
- "As mentioned previously..." — condescending
- "Please be advised that..." — corporate robot
- "Hope this email finds you well" — wrong medium, wrong era
- "Thanks in advance!" — assumes compliance
- Exclamation marks on every sentence — exhausting
- All-caps for emphasis — reads as shouting
- Long preamble before the actual ask — bury the lede

## Output Format

Always output the message inside a code block so it's easy to copy. Then optionally add 1–2 lines of brief notes below the block if relevant (e.g. suggest adding @channel if urgent, or flag a placeholder to adjust). Keep notes minimal — the message should speak for itself.

## Examples

Request: Announce that standup is moving from 9am to 9:30am starting Monday.
Output:
```
📅 Quick heads up — standup is moving to 9:30am starting Monday!

Same format, same link, just 30 minutes later. Update your calendars and let me know if that causes any conflicts 🙌
```

---

Request: Ask the team if anyone can cover a client call on Friday afternoon.
Output:
```
Hey team 👀 — anyone available to cover a client call this Friday afternoon (~2–3pm)?

I've got a conflict and need someone to step in. Drop a reply or DM me if you can help out. Really appreciate it!
```

---

Request: Write a kudos message for Sarah who just shipped a big feature.
Output:
```
🎉 Huge shoutout to Sarah for shipping the new dashboard feature today!

This one's been a long time coming and she navigated some seriously gnarly data pipeline issues to get it over the line. The team's already loving it. Well done! 🙌
```

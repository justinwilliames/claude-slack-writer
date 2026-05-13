# claude-slack-writer

A Claude Code skill for writing copy-paste-ready Slack messages. No markup quirks, no robot language, no editing needed.

## What it does

Ask Claude to draft a Slack message — an announcement, a question, a kudos post, an FYI, anything internal — and this skill produces output that's ready to paste. Tone, structure, emoji usage, and tone-by-message-type are all codified in [SKILL.md](SKILL.md).

Key design choices:

- **No Slack markup in output** (`*bold*`, `_italic_`, etc.). Pasted text doesn't reliably convert in modern Slack's WYSIWYG composer — asterisks usually render literally and the message looks broken. Emphasis comes from word choice, emoji, line breaks, and bullet structure instead.
- **Output always in a code block** so you can copy without trailing whitespace.
- **Tone-by-type table.** The skill knows the difference between an announcement, an incident, a kudos message, and a feedback request, and adjusts register accordingly.
- **One-time markup tip.** On the first invocation in any conversation, the skill surfaces a heads-up that you can enable Slack's markup preference yourself if you want `*bold*` to work when you type directly in Slack.

## Install

Drop the skill into your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/slack-writer
curl -L https://raw.githubusercontent.com/justinwilliames/claude-slack-writer/main/SKILL.md \
  -o ~/.claude/skills/slack-writer/SKILL.md
```

Or clone the repo and copy:

```bash
git clone https://github.com/justinwilliames/claude-slack-writer.git
cp claude-slack-writer/SKILL.md ~/.claude/skills/slack-writer/SKILL.md
```

The skill auto-loads on every Claude Code session.

## Use

Trigger phrases Claude will recognise:

- "Write a Slack message about X"
- "Draft a Slack post"
- "Post this to the team"
- "Announce this on Slack"
- "How do I say this on Slack?"

The skill will produce a ready-to-paste message in a code block, with one or two short notes underneath if any placeholders need adjustment.

## Slack's markup preference — what to know

Slack has a per-user "Format messages with markup" preference (Profile → Preferences → Advanced). It's an **all-or-nothing toggle**:

- **ON:** type `*bold*`, `_italic_`, `~strike~`, `` `code` `` directly and they render — but the WYSIWYG toolbar and ⌘+B shortcut stop working entirely.
- **OFF (the default):** the toolbar and ⌘+B work as normal, but typed asterisks render literally.

This skill defaults to asterisk-free output so it pastes cleanly for users in either mode. If you've personally enabled markup mode and want `*bold*` in your drafts, just tell the assistant — it'll include markup as requested.

The preference is per-user, not workspace-wide. Your audience will see whatever you send according to *their* setting, not yours.

## Contributing

This is an opinionated skill. PRs that sharpen the tone-by-type rules, add new channel patterns, or fix specific drift modes are welcome. PRs that try to make it produce flatter, more corporate output will be politely declined.

## License

MIT. Use it, fork it, improve it.

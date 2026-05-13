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

## Tip — enable Slack markup for your own composing

This skill doesn't use markup in its output because your audience probably hasn't enabled the preference. But if you want `*bold*`, `_italic_`, `~strike~`, and `` `code` `` to work when you type directly in Slack:

**Slack desktop / web:** Profile photo → **Preferences** → **Advanced** → toggle on **"Format messages with markup"**.

It's a per-user setting (not workspace-wide), so your teammates won't see the difference unless they enable it themselves.

## Contributing

This is an opinionated skill. PRs that sharpen the tone-by-type rules, add new channel patterns, or fix specific drift modes are welcome. PRs that try to make it produce flatter, more corporate output will be politely declined.

## License

MIT. Use it, fork it, improve it.

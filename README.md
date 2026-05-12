# yansu-skill

A Claude Code [skill](https://docs.claude.com/en/docs/claude-code/skills) that gives Claude personal daily context about you — workflows, tools, bugs hit, configs discovered, and crystallized insights — by reading what the [Yansu](https://github.com/Isoform/yansu) desktop app captures from your screen and audio activity.

Each session, Claude wakes up fresh. This skill is how it picks up where you left off.

## What it does

When you ask Claude "what have I been working on?", "what tools do I use for X?", "find that bug I hit last week", or any first-person history question, this skill tells Claude:

- Where to look (your local `~/.yansu-agent/` directory)
- How the files are structured
- How to scan them efficiently
- How to treat the contents as private

Claude reads only when your question needs it — not on every turn.

## Data sources (all local, read-only)

| Path | What it is |
|---|---|
| `~/.yansu-agent/memory/*.md` | Crystallized user insights — habits, preferences, deep models of you. |
| `~/.yansu-agent/knowledge/*.md` | Activity-derived discoveries — bugs hit, API errors, tools tried, configs learned. |
| `~/.yansu-agent/SOUL.md` | Personality/principles you want assistants to follow. |
| `~/.yansu-agent/crystals/` | Mini-apps Yansu has generated for you. |

The skill never writes to these files — only the Yansu desktop app does.

## Install

```bash
git clone https://github.com/Isoform/yansu-skill ~/repos/isoform/yansu-skill
mkdir -p ~/.claude/skills
ln -s ~/repos/isoform/yansu-skill ~/.claude/skills/yansu
```

Open a new Claude Code session and the skill will be picked up automatically.

To uninstall:

```bash
rm ~/.claude/skills/yansu
```

## Requirements

- [Yansu desktop app](https://github.com/Isoform/yansu) running, with at least some captured activity in `~/.yansu-agent/memory/` and `~/.yansu-agent/knowledge/`.
- Claude Code (the skill is plain markdown and works wherever Claude Code skills work).

## Privacy

`~/.yansu-agent/` is local data: real names, accounts, tokens, and other sensitive details may appear in captured insights. The skill instructs Claude to:

- Read only when the answer depends on it.
- Quote the specific sentence that answers the question — never dump full file contents.
- Never paste these files into external tools, gists, or evaluation prompts.

You stay in control: delete an entry to make Claude forget it, or remove the symlink to disable the skill entirely.

## License

MIT — see [LICENSE](LICENSE).

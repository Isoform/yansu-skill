---
name: yansu
description: Personal daily context about the user — workflows, tools they reach for, bugs they've hit, configs they've discovered, and crystallized insights captured by the Yansu desktop app from screen + audio activity. Use whenever the user asks about themselves ("who am I?", "what have I been doing?", "what's my workflow?", "what tools do I use?"), references work or discoveries from earlier sessions you weren't part of, asks to recall a bug/error/setup they hit before, asks "find that thing about X" where X is a personal artifact, or any time multi-day user context would inform the answer better than asking. Triggers on "yansu memory", "yansu knowledge", "my activity", "my recent work", "remind me what I", "have I done this before", and any first-person history question.
---

# Yansu — Daily User Context

Yansu is a desktop app (`wails-gui/`) and CLI (`yansu-agent/`) that continuously crystallizes the user's screen + audio activity into structured markdown. This skill exposes that store so future sessions wake up with day-over-day context about the user — not just the current repo.

## When to read from Yansu

Pull from these files when:

- The user asks anything self-referential ("who am I", "what was I working on yesterday", "what tools do I use for X").
- The user references prior work you don't have in conversation ("that bug I hit with Anthropic 429", "the email service I used last week", "my SGLang setup on Dell").
- You need to disambiguate intent and the user's habits matter (e.g. is "Cursor" the editor or the cursor position? Check their app usage).
- You're starting a task and want grounded context before guessing.

Do NOT read these files for ambient flavor on every turn — they're personal data. Touch them only when the answer genuinely depends on them.

## Where the data lives

All paths are on the local machine and global (not per-repo):

| Path | What it is |
|---|---|
| `~/.yansu-agent/memory/*.md` | Crystallized user insights — habits, preferences, deep models of the user. Dimensions: `user_insight`, `topic_highlight`, `deep_user_model`, `agentic_memory`, `custom`. |
| `~/.yansu-agent/knowledge/*.md` | Activity-derived discoveries — bugs hit, API errors, tools tried, configs learned. Each entry is one thing the user encountered and now knows. |
| `~/.yansu-agent/SOUL.md` | Personality/principles the user wants assistants to follow. Worth a one-time read at the start of a session if relevant. |
| `~/.yansu-agent/memory/.history/<id>/*.md` | Prior versions of an evolving memory. Usually skip; only open if the user asks "how did this used to look?". |
| `~/.yansu-agent/activity/{events,segments,snapshots,audio}/` | Raw activity captures. Don't grep this — it's huge and noisy. Use only if the user explicitly asks for raw activity. |
| `~/.yansu-agent/crystals/<app-name>/` | Mini-apps Yansu has generated for the user. Useful for "what tools has Yansu built for me?". |
| `<project>/.something/knowledge/*.md` | Per-project knowledge synced via `yansu` CLI. Different store from the global one above — only relevant when working inside a yansu-cloned project. |

## File format

Both memory and knowledge entries are plain markdown with a metadata block right after the title:

```markdown
# <Title — one line, descriptive>

- **Updated** (or **Date**): YYYY-MM-DD HH:MM
- **Source**: activity | conversation | manual
- **Dimension**: user_insight | topic_highlight | deep_user_model | agentic_memory   <!-- memory only -->
- **Apps**: Comma-separated list of apps that were active when this was captured
- **Activity Session**:
  - <uuid> — HH:MM, <apps>
  - ... (one bullet per contributing session)

## Memory Points          <!-- memory entries -->
## Description / ## Key Insights   <!-- knowledge entries -->

- <bullet 1>
- <bullet 2>
```

The **Apps** line is the fastest way to figure out what the user was doing: e.g. `Slack, WezTerm, Yansu, Ctx` → coding session, `Google Chrome, WeChat, ToDesk, 腾讯会议` → remote collaboration.

## How to query

### Browse what exists

```bash
ls -la ~/.yansu-agent/memory/ ~/.yansu-agent/knowledge/
```

### Find by topic — read the titles first

Titles are descriptive one-liners, so a `# ` grep across both directories is the cheapest scan:

Use the `Grep` tool with `pattern: ^# ` and `path: /Users/smei/.yansu-agent/knowledge` (and the same for `memory`). Read the full file only after the title matches.

### Search for a keyword

Use `Grep` with the keyword across both `~/.yansu-agent/memory/` and `~/.yansu-agent/knowledge/`. Skip the `.history/` subdir — it has duplicates.

### Filter by app

```
Grep pattern: "\\*\\*Apps\\*\\*:.*<AppName>" in ~/.yansu-agent/memory/
```

Example: `Apps.*Yansu` finds every entry from a Yansu work session.

### Recent activity

`ls -lt ~/.yansu-agent/memory/*.md | head` orders by mtime. Or grep the `**Updated**` / `**Date**` line and sort.

### Read a specific entry

Use `Read` on the full path. Files are small (≤5 KB typical), so just open the whole thing.

## CLI alternatives (per-project only)

The `yansu` CLI manages per-project knowledge under `<project>/.something/knowledge/`, not the global store. Useful only when working inside a yansu-cloned repo:

```bash
yansu knowledge list                # all entries in current project
yansu knowledge search <query>      # keyword search
yansu knowledge show <uuid>         # show one entry
yansu status                        # auth + which project is active
```

These do nothing for `~/.yansu-agent/memory/` — for the global store, read files directly.

## Privacy

These files are local user data: real names, accounts, passwords-in-clear-text are possible. Treat as confidential:

- Don't echo full file contents to the user unless they asked for them.
- Don't paste them into web tools, gists, or LLM evaluation prompts.
- Surface only the specific point that answers the question — quote a sentence, not the whole entry.

## Example workflows

**"What have I been working on lately?"**
1. `ls -lt ~/.yansu-agent/memory/*.md | head -10`
2. `Grep ^# ` on the 10 newest files to get titles.
3. Summarize the themes (e.g. "AI coding CLI proxies, SGLang on Dell, Claude.ai auth automation").

**"That bug I hit with Anthropic — what was it?"**
1. `Grep` for "Anthropic" + "429" or "error" in `~/.yansu-agent/knowledge/`.
2. Read the matching entry. Quote the relevant insight.

**"What tools do I use for remote collaboration?"**
1. Grep `Apps` lines for `ToDesk|腾讯会议|zoom` in `~/.yansu-agent/memory/`.
2. Read the matching `user_insight` entries.

**"Tell me about myself."**
1. Read `~/.yansu-agent/SOUL.md` for the user's stated principles.
2. List `Dimension: deep_user_model` and `Dimension: user_insight` titles from memory.
3. Synthesize — don't dump.

## Notes

- This is read-only context. Don't write to `~/.yansu-agent/`; the wails-gui owns those files and rewrites them.
- The store grows over time. If a memory and a knowledge entry conflict, the more recent `**Updated**` timestamp wins.
- Memory `.history/` snapshots exist for every overwrite; skip them unless explicitly asked for history.

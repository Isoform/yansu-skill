<div align="center">

# Yansu.skill

> *"Other agents start cold. Yansu.skill starts warm."*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Yansu](https://img.shields.io/badge/Yansu-Skill-d4603a)](https://yansu.app)

[English](README.md) · [中文](README_ZH.md)

<br>

**Bespoke context, delivered to your agent. Prompt once, never re-introduce yourself.**

[Yansu](https://yansu.app) listens, crystallizes, and quietly builds. **Yansu.skill** is how that crystallized knowledge reaches whichever agent you happen to be using — so it walks in already knowing how you actually work.

<br>

**Install** — paste this to your AI agent:

</div>

```
Install the Yansu skill for me:

1. Fetch https://raw.githubusercontent.com/Isoform/yansu-skill/main/SKILL.md
2. Save it under your own user-level skills directory as `yansu/SKILL.md`
   (whatever path your agent reads skills from on this machine).
3. Confirm the install path when done.
```

<div align="center">

[See it in action](#see-it-in-action) · [Features](#features) · [How it works](#how-it-works) · [Privacy](#privacy)

</div>

---

## See it in action

Type `/yansu` to invoke the skill explicitly, or ask naturally and your agent will pull it in when it spots a continuity question.

```
You      ❯ /yansu Why did that build fail again — the auth one?

Agent    ❯ Same migration-lock issue from a few weeks back. You
           worked around it last time by running the ALTER inside
           a transaction with statement_timeout off. Want me to
           apply that recipe?
```

```
You      ❯ /yansu Spin up the staging database

Agent    ❯ You've done this twice. Your compose template lives
           next door, and the first boot usually trips on the SSL
           cert path. Starting from your last-known-good and
           watching for the cert thing.
```

```
You      ❯ /yansu Pick the right tool for the job

Agent    ❯ For this kind of task you usually reach for the same
           three. The first one fits the shape of the problem,
           and you've been getting cleaner output out of it since
           you tuned the flags last week.
```

This is not role-play. This is continuity.

---

## Features

### Tribal Knowledge

Your agent inherits everything Yansu has crystallized — every conversation, decision, hesitation, and pattern. Already structured, already tagged, already yours. The knowledge that used to live only in your head now lives wherever your agent does.

### No Re-introduction

You still prompt your agent — you just stop re-explaining yourself. The agent already knows your tools, your workflows, the gotchas you've paid for. Say *"help me ship the thing"* and it knows what the thing is. Say *"the bug from last week"* and it knows which bug.

### Distraction Free

Yansu.skill stays silent until your question actually needs personal context. No noisy preambles. No agent pretending to remember things it doesn't. Continuity when you need it, invisible when you don't.

---

## How it works

**1. Yansu listens.** It observes how you work — your desktop, your messaging apps, the conversations and decisions that would otherwise vanish.

**2. Yansu crystallizes.** Raw memory becomes structured, actionable knowledge — patterns you can reuse, not transcripts you'd never re-read.

**3. Yansu.skill surfaces.** When your agent needs you, the skill hands over the relevant slice — one entry, one sentence, never the whole archive.

Yansu does the listening. The skill does the handoff.

---

## Privacy

**Lives on your machine.** Your memory, your captured workflows, your generated knowledge — all stored locally. Not on our servers. On yours.

**You hold the keys.** Nothing leaves your device through this skill. Delete an entry to make your agent forget it; uninstall the skill to disable the connection entirely.

**Read-only by design.** Capture is Yansu's job. Recall is the skill's. The skill will never write back to your memory, your knowledge, or your machine.

---

## Honest boundaries

A skill that won't tell you what it can't do is one you can't trust.

- **It doesn't predict the future** — only your past, as captured by Yansu.
- **It only knows what Yansu has seen** — if you've never used Yansu while doing X, your agent won't know about X.
- **It is quiet by default** — it stays out of every turn that doesn't need it.

A continuity layer that pretends to be omniscient isn't continuity. It is flattery.

---

## License

MIT — see [LICENSE](LICENSE).

Built for [Yansu](https://yansu.app) by [Isoform](https://github.com/Isoform).

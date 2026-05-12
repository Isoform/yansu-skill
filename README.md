<div align="center">

# Yansu.skill

> *"Each session, your agent wakes up remembering you."*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Yansu](https://img.shields.io/badge/Yansu-Skill-d4603a)](https://github.com/Isoform/yansu)

<br>

**Stop explaining yourself to your agent every morning.**

[Yansu](https://github.com/Isoform/yansu) quietly captures what you do every day — the apps you reach for, the bugs you've already paid for, the setups you've already figured out, the workflows that have become yours. **Yansu.skill** is how your agent finally gets to use all of it.

One install, and your agent stops being a stranger.

[See it in action](#see-it-in-action) · [Install](#install) · [What it brings](#what-it-brings) · [Honest boundaries](#honest-boundaries) · [How it works](#how-it-works)

</div>

---

## See it in action

```
You      ❯ Why did that build fail again — the auth one?

Agent    ❯ Same migration-lock issue from a few weeks back. You
           worked around it last time by running the ALTER inside
           a transaction with statement_timeout off. Want me to
           apply that recipe?
```

```
You      ❯ Spin up the staging database

Agent    ❯ You've done this twice. Your compose template lives
           next door, and the first boot usually trips on the SSL
           cert path. Starting from your last-known-good and
           watching for the cert thing.
```

```
You      ❯ Pick the right tool for the job

Agent    ❯ For this kind of task you usually reach for the same
           three. The first one fits the shape of the problem,
           and you've been getting cleaner output out of it since
           you tuned the flags last week.
```

Without Yansu.skill, every conversation starts from zero. Your agent doesn't know your tools, your habits, the gotchas you've already paid for. You re-explain. Every. Single. Time.

With Yansu.skill, your agent walks in knowing the version of you that worked yesterday. It cites the bug because it actually remembers. It picks the tool you already use because it knows your stack. It skips the obvious because the obvious is what you taught it last week.

This is not role-play. This is continuity.

---

## Install

```bash
git clone https://github.com/Isoform/yansu-skill
```

That's it. Yansu picks it up on the next session.

---

## What it brings

**Your daily working memory, in your agent's hands.**

| | |
|---|---|
| **Who you are** | The version of you that shows up to work — your principles, your style, the way you'd rather be helped. |
| **What you do** | Your real workflows. Not the ones you'd describe in an interview. The ones you actually run on Tuesday at 11am. |
| **What you already know** | Every bug you've debugged, every config you've cracked, every API you've finally figured out. Yours, already. |
| **What you reach for** | Your tools, your shortcuts, your favorite combinations. The terminal you live in, the browser tab you keep open. |
| **The you behind the keyboard** | A quiet model of your habits, your collaborators, your context. The you that exists between commits. |

Your agent stops asking and starts knowing.

---

## Why it works

Other tools forget you the moment you close the tab. They greet you fresh every morning, and you re-introduce yourself with the same paragraph: *"Here's what I'm building. Here are my tools. Here are the gotchas. Here's how I like to be helped."*

Yansu has been listening all along — to your screen, to your voice memos, to the apps you open and close. It has been quietly building a portrait of you. Not to surveil. To serve.

**Yansu.skill is the bridge.** It hands that portrait to your agent at the start of every session. So when you say *"help me ship the thing,"* your agent already knows which thing, which repo, which workflow, which you.

---

## Honest boundaries

A skill that won't tell you what it can't do is one you can't trust.

- **It doesn't predict the future** — only your past, as captured by Yansu.
- **It only knows what Yansu has seen** — if you've never used Yansu while doing X, your agent won't know about X.
- **It is read-only** — capture is Yansu's job; recall is the skill's. The skill will never write back.
- **It is local-only** — your context never leaves your machine through this skill.
- **It is quiet by default** — it stays out of every turn that doesn't need it. Continuity, not chatter.

A continuity layer that pretends to be omniscient isn't continuity. It is flattery.

---

## How it works

When you ask your agent anything self-referential — *"what was I working on?"*, *"the bug I hit yesterday"*, *"what tools do I use for X"* — Yansu.skill quietly:

1. **Decides** whether your question actually needs personal context. Most of the time it doesn't, and the skill stays out of the way.
2. **Scans** the right slice of your captured memory by title and timestamp. The answer is usually one entry, not all of them.
3. **Quotes** the specific sentence that earns its place in the response. Never the whole file.
4. **Disappears** when you're done.

The methodology lives in [`SKILL.md`](SKILL.md).

---

## License

MIT — see [LICENSE](LICENSE).

Built for [Yansu](https://github.com/Isoform/yansu) by [Isoform](https://github.com/Isoform).

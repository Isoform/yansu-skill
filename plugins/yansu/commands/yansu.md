# /yansu

Invoke Yansu continuity for the user's request.

## Arguments

- `request`: the natural-language request after `/yansu` (optional)

## Workflow

1. Treat everything after `/yansu` as the user's actual request.
2. Use the bundled `yansu` skill for this turn.
3. Follow the skill's CLI gate before reading memory, activity, or knowledge.
4. If the user did not provide a request after `/yansu`, briefly explain useful examples such as:
   - `/yansu what did I do today?`
   - `/yansu have I solved this before?`
   - `/yansu where am I wasting time?`

## Guardrails

- Do not bypass the skill's requirement to resolve and use the bundled Yansu CLI from the desktop app.
- Do not invent memories or activity. If Yansu has no relevant context, say that plainly.
- Quote sparingly and summarize personal context instead of dumping full memory entries.

---
name: teach-be
description: Teach the next lesson on the `be` path — Backend Engineering Deep Dive (request lifecycle, load balancers, WSGI/ASGI frameworks, sockets & connections, processes/threads/workers/gunicorn, capacity & failure modes). Path is pinned; args are duration and/or topic only, e.g. "/teach-be 15 mins" or "/teach-be gunicorn workers".
---

# /teach-be — serve a lesson on the `be` path

**Path is pinned to `be`.** Do **not** run path resolution — the path is already decided.

State files: `paths/be/PROGRESS.md` and `paths/be/ROADMAP.md`.

## Argument handling

Args are **duration and/or topic only**:
- **no arg** → next topic in sequence for `be`
- **duration** (`15`, `15m`, `15 mins`, `1h`) → time-box the session
- **topic** → that topic inside `be`; if it's not in `paths/be/ROADMAP.md`, ask minutes first, add it to the right cluster, then teach it (per `explicit-topic-teach.md`)

A path name appearing in the args is **ignored, not re-resolved** — `/teach-be be 10 mins` is just `/teach-be 10 mins`.

## Steps

Follow **`.claude/skills/teach/SKILL.md` Steps 1–6 verbatim**, with `be` as the resolved path. That means, unchanged:

1. `git pull` first, then load `coaching-memory/*.md` (all of them, including `learning-paths.md`), then `PATHS.md`, then `paths/be/PROGRESS.md`.
2. Count learning days from **`be`'s own session log** — never `default`'s. Every 3rd learning day *of this path* is a review day.
3. 4–6 cards, easy words, example-led: Concept → real-world example → GoZayaan example → edge cases → staff lens → self-check.
4. Teach-back prompt; `✓` only when he explains it without notes.
5. Update `paths/be/PROGRESS.md` (checkboxes, bars, counters, dated session-log row), then refresh the `be` row in `PATHS.md`.
6. Auto-sync: `git add -A && git commit -m "teach(be): <topic> — <YYYY-MM-DD>" && git push`. Masudur-only author, no Claude trailer.

Time-boxing, per-day carry-over buckets, and the review-day bucket rule all apply exactly as in the `teach` skill — **scoped to `be`**.

## Independence

Surface only **`be`'s** open buckets at session start. An open bucket in `default` (or any other path) **must never** block or be mentioned in a `be` session.

Citing a `default` topic inside a card is fine and encouraged (e.g. BE5.3 GIL → `default` M1.12, BE6.3 percentiles → `default` M2.22) — record the link in the session-log row. But `be`'s progress, counters, tests, and rubric stay entirely its own.

Keep replies short and focused.

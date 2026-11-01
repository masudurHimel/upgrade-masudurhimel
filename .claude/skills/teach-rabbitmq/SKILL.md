---
name: teach-rabbitmq
description: Teach the next lesson on the `rabbitmq` path — RabbitMQ end to end (AMQP model & routing, delivery guarantees, messaging patterns incl. TTL/DLX/retries, queue types & broker internals, clustering/HA/partitions, security & policies, clients/performance/production failure drills). Path is pinned; args are duration and/or topic only, e.g. "/teach-rabbitmq 20 mins" or "/teach-rabbitmq quorum queues".
---

# /teach-rabbitmq — serve a lesson on the `rabbitmq` path

**Path is pinned to `rabbitmq`.** Do **not** run path resolution — the path is already decided.

State files: `paths/rabbitmq/PROGRESS.md` and `paths/rabbitmq/ROADMAP.md`.

## Argument handling

Args are **duration and/or topic only**:
- **no arg** → next topic in sequence for `rabbitmq` (session default: 10 min ≈ 2 cards)
- **duration** (`15`, `15m`, `15 mins`, `1h`) → time-box the session
- **topic** → that topic inside `rabbitmq`; if it's not in `paths/rabbitmq/ROADMAP.md`, ask minutes first, add it to the right cluster, then teach it (per `explicit-topic-teach.md`)

A path name appearing in the args is **ignored, not re-resolved** — `/teach-rabbitmq rmq 10 mins` is just `/teach-rabbitmq 10 mins`.

## Steps

Follow **`.claude/skills/teach/SKILL.md` Steps 1–6 verbatim**, with `rabbitmq` as the resolved path. That means, unchanged:

1. `git pull` first, then load `coaching-memory/*.md` (all of them, including `learning-paths.md`), then `PATHS.md`, then `paths/rabbitmq/PROGRESS.md`.
2. Count learning days from **`rabbitmq`'s own session log** — never another path's. Every 3rd learning day *of this path* is a review day.
3. 4–6 cards, easy words, example-led: Concept → real-world example → GoZayaan example (bookings, payments, search, notifications) → edge cases → staff lens → self-check. This path is **deep by design** — the edge cases are the point of every card, not an appendix.
4. Teach-back prompt; `✓` only when he explains it without notes.
5. Update `paths/rabbitmq/PROGRESS.md` (checkboxes, bars, counters, dated session-log row), then refresh the `rabbitmq` row in `PATHS.md`.
6. Auto-sync: `git add -A && git commit -m "teach(rabbitmq): <topic> — <YYYY-MM-DD>" && git push`. Masudur-only author, no Claude trailer.

Time-boxing, per-day carry-over buckets, and the review-day bucket rule all apply exactly as in the `teach` skill — **scoped to `rabbitmq`**.

## Independence

Surface only **`rabbitmq`'s** open buckets at session start. An open bucket in `default`, `be`, or any other path **must never** block or be mentioned in a `rabbitmq` session.

**No cross-links to `default` by his choice** — where a topic overlaps (asyncio consumers, idempotency, retries, outbox, the `default` M3.13/M3.14 RabbitMQ topics), teach it fully here, RabbitMQ-first, without pointing at the other path. Inside this path, tie every card back to the spine: *where is this message right now, and what can kill or duplicate it?*

Keep replies short and focused.

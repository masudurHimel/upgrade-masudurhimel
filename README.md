# upgrade-masudurhimel

## What this repo is

This isn't a code project — it's a **living study system**. It exists to turn *recognition* ("yeah, I've heard of MVCC") into *ability* ("I can explain it, defend the tradeoff, and design around it"). The whole thing runs on desktop **and** mobile: `claude.ai/code` cloud sessions clone this repo, read the coaching context, and pick up exactly where the last session left off.

The focus is deliberately on **fundamentals + edge cases**:
- Python internals (data model, descriptors, async, GIL, GC, CPython)
- Databases (transactions, MVCC, WAL, isolation levels, indexes, query planning)
- APIs & performance (REST/gRPC design, versioning, profiling, percentiles, load testing)
- Distributed systems (CAP/PACELC, consensus, sagas, outbox, messaging, SRE, security)
- System design, as a first-class track running across all three months

## How it works

You poke the coach — *"teach me"* — and get a lesson built from **4–6 cards** (~4–5 min each). Every card follows the same shape:

**Concept** (plain language) → **Real example** (usually GoZayaan: flights, hotels, bookings, payments, search) → **Staff lens** (why it matters when you're the one making the call) → optional **🔧 hands-on note** → **Self-check**.

Progress is only "real" when you can **explain it back without notes** (the teach-back gate). Four mechanisms keep growth *compounding* instead of just accumulating:

1. **Teach-back gate** — `[x]` = covered, `[✓]` = you can actually wield it.
2. **Connection web** — every new concept links to prior ones (`WAL → replication → Kafka's log → outbox`).
3. **Spaced resurfacing** — old topics reappear in later tests so they stick.
4. **Build-in-public** — strong learnings become short notes/posts.

### Commands

| You say | The coach does |
|---|---|
| `teach me` / `/teach` | Serve the next lesson in sequence (default path) |
| `/teach <topic>` | Jump to a topic (and add it to the roadmap if new) |
| `/teach 10 mins` | Size the lesson to your time budget |
| `/teach-<path>` | Serve the next lesson in a **parallel path** — every path gets its own command (e.g. `/teach-be 15 mins`) |
| `/teach <path> [10 mins]` | Same thing via the generic command (e.g. `/teach be 15 mins`) |
| `/teach <path> <topic>` | Jump to a topic inside a specific path |
| `/create_path [name]` | Stand up a new parallel path — full intake, then generates it |
| `/progress` (`where am I?`) | Progress bars + what's next · `/progress <path>` · `/progress all` |
| `/test_me` (`/test_me M2`) | Checkpoint quiz — applied scenarios, plus spaced resurfacing · `/test_me <path>` |
| `/assess` (`review me`) | Evaluate an explanation/artifact against the path's rubric · `/assess <path>` |
| `add <topic>` / `drop <topic>` | Re-shape the roadmap |

## Repo layout

| File / dir | What it holds |
|---|---|
| **[PATHS.md](PATHS.md)** | The **path registry** at repo root — every learning path, its teach command, status, and what's next |
| **[paths/default/ROADMAP.md](paths/default/ROADMAP.md)** | The 3-month plan — all ~70 topics across M1/M2/M3, artifacts, "prove it at work" hooks |
| **[paths/default/PROGRESS.md](paths/default/PROGRESS.md)** | Living tracker — progress bars, checklists, test scores, carry-over buckets, session log |
| **[paths/default/SYSTEM_DESIGN.md](paths/default/SYSTEM_DESIGN.md)** | The 4-mode system design track (build / design / drill / study) |
| **[paths/default/SOFT_SKILLS.md](paths/default/SOFT_SKILLS.md)** | Curated leadership & influence resources |
| **paths/&lt;slug&gt;/** | Any other path — same two files, fully independent state |
| **[MEMORY.md](MEMORY.md)** | Canonical project memory read at the start of every session |
| **[coaching-memory/](coaching-memory/)** | Portable mirror of *how* to coach — travels to mobile/cloud where `~/.claude` memory can't |
| **[CLAUDE.md](CLAUDE.md)** | Rules for the coach (context loading, `main`-only git, auto-sync) |
| **.claude/skills/** | The `teach` · `progress` · `test_me` · `assess` · `create_path` skills that power the commands |

## Parallel learning paths

The program isn't one curriculum — it's a **default path plus any number of parallel ones**.

- **`default`** is the 3-month Staff Engineer program. Bare `/teach`, `/progress`, `/test_me`, `/assess` resolve here.
- **Specialized paths** (`/create_path`) run alongside it on the **same engine** — cards, teach-back gate, per-day carry-over buckets, review every 3rd learning day, tests, rubric — but with **fully independent state**. Each path counts its own learning days and keeps its own buckets, so an unfinished topic in one path never blocks a session in another.
- Each path gets its **own rubric**: `default` uses the 7 staff competencies; a specialized path gets 4–6 competencies drafted for its domain at creation.
- `/create_path` runs an end-to-end intake — outcome, domain, depth, size, cadence, artifacts, prereqs, then a cluster review gate and a rubric baseline — and only then writes the path.

See [PATHS.md](PATHS.md) for the live registry.

## The three months at a glance

- **Month 1 — Foundations:** Python internals, DSA concepts, networking & protocols. *Artifact: an async token-bucket rate limiter.*
- **Month 2 — Data, APIs & Performance:** Postgres internals, API design, performance engineering, system design core. *Artifact: a real slow-query fix + a design doc/RFC.*
- **Month 3 — Distributed, Messaging, SRE & Security:** consensus, reliability patterns, Kafka/RabbitMQ, observability, auth & OWASP. *Artifact: outbox pattern / leader election / event-driven design.*

At the 2026-09-19 checkpoint: a mixed capstone test, artifact review, and a rubric re-score — then **Phase 2** is written around actual performance. See [paths/default/ROADMAP.md](paths/default/ROADMAP.md) for the full topic list.

## Working on this repo

This repo works **directly on `main`** — no branches, no PRs. Sessions auto-sync: pull at start, commit + push after any change to a coaching state file, so desktop and mobile stay in lockstep. The full rules live in [CLAUDE.md](CLAUDE.md).

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
| `teach me` / `/teach` | Serve the next lesson in sequence |
| `/teach <topic>` | Jump to a topic (and add it to the roadmap if new) |
| `/teach 10 mins` | Size the lesson to your time budget |
| `/progress` (`where am I?`) | Progress bars + what's next |
| `/test_me` (`/test_me M2`) | Checkpoint quiz — applied scenarios, plus spaced resurfacing |
| `/assess` (`review me`) | Evaluate an explanation/artifact against the staff rubric |
| `add <topic>` / `drop <topic>` | Re-shape the roadmap |

## Repo layout

| File / dir | What it holds |
|---|---|
| **[ROADMAP.md](ROADMAP.md)** | The 3-month plan — all ~70 topics across M1/M2/M3, artifacts, "prove it at work" hooks |
| **[PROGRESS.md](PROGRESS.md)** | Living tracker — progress bars, checklists, test scores, carry-over buckets, session log |
| **[SYSTEM_DESIGN.md](SYSTEM_DESIGN.md)** | The 4-mode system design track (build / design / drill / study) |
| **[SOFT_SKILLS.md](SOFT_SKILLS.md)** | Curated leadership & influence resources |
| **[MEMORY.md](MEMORY.md)** | Canonical project memory read at the start of every session |
| **[coaching-memory/](coaching-memory/)** | Portable mirror of *how* to coach — travels to mobile/cloud where `~/.claude` memory can't |
| **[CLAUDE.md](CLAUDE.md)** | Rules for the coach (context loading, `main`-only git, auto-sync) |
| **.claude/skills/** | The `teach` · `progress` · `test_me` · `assess` skills that power the commands |

## The three months at a glance

- **Month 1 — Foundations:** Python internals, DSA concepts, networking & protocols. *Artifact: an async token-bucket rate limiter.*
- **Month 2 — Data, APIs & Performance:** Postgres internals, API design, performance engineering, system design core. *Artifact: a real slow-query fix + a design doc/RFC.*
- **Month 3 — Distributed, Messaging, SRE & Security:** consensus, reliability patterns, Kafka/RabbitMQ, observability, auth & OWASP. *Artifact: outbox pattern / leader election / event-driven design.*

At the 2026-09-19 checkpoint: a mixed capstone test, artifact review, and a rubric re-score — then **Phase 2** is written around actual performance. See [ROADMAP.md](ROADMAP.md) for the full topic list.

## Working on this repo

This repo works **directly on `main`** — no branches, no PRs. Sessions auto-sync: pull at start, commit + push after any change to a coaching state file, so desktop and mobile stay in lockstep. The full rules live in [CLAUDE.md](CLAUDE.md).

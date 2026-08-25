# 🧭 Learning paths

> **The registry — and the name resolver.** Every learning path in this program has one row here.
> A path's own `PROGRESS.md` is **canonical** for its state; the columns below are a cache,
> refreshed at the end of every session.
>
> **Default path:** `default`. Bare `/teach`, `/progress`, `/test_me`, `/assess` (no path arg) resolve here.
>
> Every path runs the **same engine** — 4–6 cards → teach-back gate → per-day carry-over buckets →
> review every 3rd learning day → cluster tests → rubric — with **fully independent state**:
> its own learning-day counter, its own review cadence, its own buckets. A bucket open in one path
> **never** blocks a session in another.

---

## Paths

| Slug | Teach command | Name | Status | Topics ✓ | Learning days | Session default | Next up | Last session |
|---|---|---|---|---|---|---|---|---|
| `default` | `/teach` | Staff Engineer (3-month) | **active · DEFAULT** | 11/71 | 26 | 2–5 min | M1.11 final card — offloading blocking calls (`asyncio.to_thread`) | 2026-08-22 |
| `be` | `/teach-be` | Backend Engineering Deep Dive | active | 0/42 | 5 | 2–5 min | **day 6 = REVIEW**, then BE1.1 card 5 — full chain end-to-end (buckets: refused/timeout · request-line ordering) | 2026-08-26 |

### How to invoke

| You type | You get |
|---|---|
| `/teach` | `default`, next in sequence |
| `/teach-be [15 mins]` | `be`, next in sequence — **every path gets its own `/teach-<slug>`** |
| `/teach be <topic>` · `/teach-be <topic>` | a specific topic inside `be` |
| `/progress be` · `/test_me be` · `/assess be` | those skills, scoped to `be` (shortcut as an argument) |
| `/progress all` | roll-up of every path |
| `/create_path [name]` | stand up a new path (also generates its `/teach-<slug>`) |

### Files per path
```
paths/<slug>/
├── ROADMAP.md     the plan (clusters, topic IDs, artifacts, checkpoint)
└── PROGRESS.md    living state (bars, counters, buckets, checklist, test log, session log, rubric)
```
`default` additionally carries its two parallel tracks: [SYSTEM_DESIGN.md](paths/default/SYSTEM_DESIGN.md) · [SOFT_SKILLS.md](paths/default/SOFT_SKILLS.md).

---

## Aliases

| Alias | → |
|---|---|
| `staff`, `staff-eng`, `se` | `default` |
| `backend`, `backend-deep-dive` | `be` |

Aliases are matched case-insensitively and ignore `-` / `_` / spaces, so `staff eng` → `staff-eng` → `default`.

---

## Rules

**Slugs** — kebab-case, unique across both slugs *and* aliases.
**Reserved words** (never usable as a slug or alias): `default` (taken), `be` (taken), `all`, `path`, `topic`, `mins`, `minutes`.
**Status values** — `active` · `paused` · `archived`. Exactly one path carries the `DEFAULT` marker.

**Creating a path** is never implicit. `/teach some-unknown-name` still means *new topic on the default path*.
A new path only ever comes from **`/create_path`**.

**Lifecycle** (conversational — no skill needed):
`pause <slug>` · `resume <slug>` · `archive <slug>` · `make <slug> the default` · `add`/`drop <topic> in <slug>`.

Full mechanism: [`coaching-memory/learning-paths.md`](coaching-memory/learning-paths.md).

# 🧭 Learning paths

> **Registry — the name resolver.** Every learning path in this program has one row here.
> A path's own `PROGRESS.md` is **canonical** for its state; the columns below are a cache,
> refreshed at the end of every session.
>
> **Default path:** `default`. Bare `/teach`, `/progress`, `/test_me`, `/assess` (no path arg) resolve here.
>
> Every path runs the **same engine** — 4–6 cards → teach-back gate → per-day carry-over buckets →
> review every 3rd learning day → cluster/month tests → rubric — with **fully independent state**:
> its own learning-day counter, its own review cadence, its own buckets. A bucket open in one path
> **never** blocks a session in another.

---

## Paths

| Slug | Name | Status | Topics ✓ | Learning days | Session default | Next up | Last session |
|---|---|---|---|---|---|---|---|
| `default` | Staff Engineer (3-month) | **active · DEFAULT** | 11/71 | 26 | 2–5 min | M1.11 final card — offloading blocking calls (`asyncio.to_thread`) | 2026-08-22 |

### Files per path
```
paths/<slug>/
├── ROADMAP.md     the plan (clusters, topic IDs, artifacts, checkpoint)
└── PROGRESS.md    living state (bars, counters, buckets, checklist, test log, session log, rubric)
```
`default` additionally carries its two parallel tracks: [SYSTEM_DESIGN.md](default/SYSTEM_DESIGN.md) · [SOFT_SKILLS.md](default/SOFT_SKILLS.md).

---

## Aliases

| Alias | → |
|---|---|
| `staff`, `staff-eng`, `se` | `default` |

Aliases are matched case-insensitively and ignore `-` / `_` / spaces, so `staff eng` → `staff-eng` → `default`.

---

## Rules

**Slugs** — kebab-case, unique across both slugs *and* aliases.
**Reserved words** (never usable as a slug or alias): `default` (taken), `all`, `path`, `topic`, `mins`, `minutes`.
**Status values** — `active` · `paused` · `archived`. Exactly one path carries the `DEFAULT` marker.

**Creating a path** is never implicit. `/teach some-unknown-name` still means *new topic on the default path*.
A new path only ever comes from **`/create_path`**.

**Lifecycle** (conversational — no skill needed):
`pause <slug>` · `resume <slug>` · `archive <slug>` · `make <slug> the default` · `add`/`drop <topic> in <slug>`.

Full mechanism: [`coaching-memory/learning-paths.md`](../coaching-memory/learning-paths.md).

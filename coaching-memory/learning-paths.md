---
name: learning-paths
description: The multi-path learning system — how /teach, /progress, /test_me, /assess resolve a path name, and the rule that every path runs the same engine with fully independent state
metadata:
  type: project
---

The coaching program runs **multiple parallel learning paths**. `default` is the 3-month Staff Engineer program (see [[learning-program]]); specialized paths (AI engineering, Kubernetes, advanced Kafka, …) run alongside it.

## Layout

```
paths/
├── index.md          ← the registry (name resolver)
├── default/          ← the DEFAULT path — Staff Engineer program
│   ├── ROADMAP.md  PROGRESS.md  SYSTEM_DESIGN.md  SOFT_SKILLS.md
└── <slug>/
    └── ROADMAP.md  PROGRESS.md
```

`paths/index.md` resolves names and caches a summary row per path. **A path's own `PROGRESS.md` is canonical for its state** — if the registry and a `PROGRESS.md` disagree, `PROGRESS.md` wins and the registry row gets fixed.

Root `ROADMAP.md` / `PROGRESS.md` are **MOVED stubs**. Never write to them.

## Argument resolution — apply in this exact order

1. **Extract a duration token** from anywhere in the args — `15`, `15m`, `15 min(s)`, `15 minutes`, `1h`. That's the session budget; remove it from the args.
2. **Explicit prefixes win** (escape hatches): `path:<slug>` forces a path · `topic:<name>` forces a topic on `default`.
3. **Match the remaining leading token(s)** against slugs + aliases in `paths/index.md` — case-insensitive, ignoring `-` `_` and spaces.
   - **Match** → path session. Whatever text remains after the match is a **topic within that path**.
   - **No match** → the whole arg is a **topic on `default`**. This is the pre-existing behavior and must not regress.
4. **Nothing left** → next topic in sequence for the resolved path.
5. **Collision** (the arg matches both a path slug and a known topic title) → **ask, one line, offer both.** Never guess.

**Creating a path is never implicit.** `/teach some-unknown-name` still means *new topic on `default`* — ask minutes first, add to the roadmap, time-box (per [[explicit-topic-teach]]). A new path comes **only** from `/create_path`.

### Command surface

| Command | Resolves to |
|---|---|
| `/teach` | `default`, next in sequence |
| `/teach <path> [duration]` | that path, next in sequence |
| `/teach <path> <topic> [duration]` | that topic inside that path |
| `/teach <topic> [duration]` | topic on `default` — unchanged |
| `/progress` · `/progress <path>` | that path's snapshot |
| `/progress all` | roll-up of every path from the registry |
| `/test_me [path] [scope]` | quiz within a path (`M1`/`M2`/`M3` scopes still valid on `default`) |
| `/test_me all` | the **only** cross-path quiz mode |
| `/assess [path]` | that path's rubric |
| `/create_path [name]` | end-to-end intake → new path |

**Lifecycle verbs are conversational**, not skills: `pause <slug>` · `resume <slug>` · `archive <slug>` · `make <slug> the default` · `add`/`drop <topic> in <slug>`. Each edits the registry row + that path's files, then auto-syncs.

## Full independence (hard rule)

Each path is its own world:

- **Learning days** are counted from **that path's own session log** — never pooled across paths. Two sessions in different paths on the same calendar date are two separate learning days in two separate counters.
- **Review cadence** = every 3rd learning day **of that path** ([[review-rules]]).
- **Carry-over buckets gate within a path only.** An open bucket in `default` must **never** block `/teach <other-path>`, and vice-versa. Surface only the resolved path's buckets at session start.
- **Tests, counters, artifacts, rubric** are all per-path.

## Same engine everywhere

Every existing rule applies unchanged **inside** each path — nothing about how I teach changes, only which files I read and write:

- [[card-teaching-style]] — easy words (first-year CSE level), example-led, first-read clarity, and the fixed sequence concept → real-world example → GoZayaan example → edge cases → staff lens/teach-back. The example ships **in** the session.
- [[teaching-style]] — concrete over abstract; corrective contrast example when he's half-wrong.
- [[explicit-topic-teach]] — existing topic = ~5-min repeat; NEW topic = ask minutes first, add to that path's roadmap, time-box, park leftovers as a bucket.
- [[review-rules]] — a skipped or wrong review question gets a short re-teach on the spot and goes into that path's bucket; he must teach it back without notes before new material in that path.
- Teach-back gate for `✓`, connection web, spaced resurfacing, build-in-public ([[learning-program]]).
- [[reply-style]] — short and focused everywhere except teaching cards.

## Per-path rubric

Specialized paths do **not** reuse the 7 staff competencies. `/create_path` drafts **4–6 competencies specific to that domain**, he self-scores a 1–5 baseline at creation, and it's re-scored monthly in that path's `PROGRESS.md`. `default` keeps its 7-competency staff rubric (baseline avg 2.4, set 2026-06-19).

## Cross-path connection web

Linking across paths in **card text** is encouraged — e.g. an AI-path cost/latency card citing `default` M2.22 percentiles — and the link gets recorded in that path's session-log row. But cross-path **questions** only appear when he explicitly asks `/test_me all`. Default resurfacing stays inside the path.

## Git

Unchanged from [[main-only-branch-policy]] and [[commit-authorship]]: `main` only, no branches or PRs, pull at session start, `git add -A && git commit && git push` automatically after writing any state file, Masudur-only author, no Claude trailer.

Commit message prefixes:
- `default` path → `teach: <topic> — <YYYY-MM-DD>` (unchanged, so its history reads continuously)
- specialized path → `teach(<slug>): <topic> — <YYYY-MM-DD>`
- path admin → `path: create <slug>` · `path: <verb> <slug>`

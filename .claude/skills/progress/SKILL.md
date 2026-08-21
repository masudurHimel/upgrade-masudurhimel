---
name: progress
description: Show Masudur's progress in the learning program — progress bars, topics done/left, test scores, and what's next. With no arg, the default Staff Engineer path; with a path name, that path; with "all", a roll-up of every path. The "where am I?" command.
---

# /progress — where am I

## Path resolution
- **no arg** → the `default` path
- **`<path>`** → that path (match slug/alias in `PATHS.md`, case-insensitive, ignoring `-` `_` spaces)
- **`all`** → roll-up of every path

## Steps

1. Read `PATHS.md`, then the resolved path's `paths/<slug>/PROGRESS.md`.
2. Show: the progress bars (per cluster + total), artifacts/tests/teach-back counters, rubric baseline, open **carry-over buckets**, and **Next up**.
3. Note whether today is a learning / review / test day — counting learning days from **that path's own session log** (every 3rd learning day of this path = review).

For **`all`**: render the registry table (one row per path — slug, status, topics ✓, learning days, next up, last session), mark which one is `DEFAULT`, and flag any path with an open bucket. One screen, no per-path detail.

Read-only — this command never writes files, so no commit.

Keep it short and focused — just the snapshot, no lecture.

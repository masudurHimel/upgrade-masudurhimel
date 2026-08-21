---
name: assess
description: Assess Masudur in the learning program — evaluate an explanation, artifact, or design doc against the path's competency rubric, or run the weekly/monthly review. With no arg, the default Staff Engineer path (7 staff competencies); with a path name, that path's own rubric. Gives honest, specific feedback and updates the rubric.
---

# /assess — assess against the rubric

## Path resolution
- **no arg** → the `default` path → the **7 staff competencies** (baseline avg 2.4, set 2026-06-19)
- **`<path>`** → that path (match slug/alias in `PATHS.md`) → **that path's own 4–6 domain competencies**, drafted at creation

## Steps

1. Load coaching context (`coaching-memory/*.md` incl. `learning-paths.md`); read `PATHS.md`, then the resolved path's `PROGRESS.md` (rubric + history).
2. Determine what to review: a specific explanation/artifact he provides, OR the weekly review (re-explain the period from memory), OR month-end (rubric re-score + reflections).
3. Assess against **that path's** competencies. Be honest and specific — name the gap and the next rep, not just praise.
4. If month-end, fill the month's rubric column in that path's `PROGRESS.md` (dated) and compare to its baseline average.
5. Tie feedback to a concrete action at GoZayaan when the path's domain allows.
6. If anything was written, **sync up automatically** — `git add -A && git commit -m "assess: <scope> — <YYYY-MM-DD>" && git push` (use `assess(<slug>):` for a non-default path). Masudur-only author, no Claude trailer.

Never score a specialized path against the staff rubric, or vice-versa.

Keep it short and focused.

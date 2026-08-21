---
name: test_me
description: Quiz Masudur on what he's learned in the learning program. With no arg, test recent topics in the default path; with a path name, test that path; with a month/cluster scope (e.g. "/test_me M2"), test that scope. Applied scenarios over definitions, plus spaced resurfacing of earlier topics.
---

# /test_me — checkpoint quiz

## Path resolution
- **no arg** → recent cluster in the `default` path
- **`<path>` [scope]** → that path (match slug/alias in `PATHS.md`); an optional trailing scope narrows it
- **`M1` / `M2` / `M3`** → that month of `default` (unchanged)
- **`all`** → the **only** cross-path mode: questions drawn from every active path

## Steps

1. Load coaching context (`coaching-memory/*.md` incl. `learning-paths.md`), read `PATHS.md`, then the resolved path's `PROGRESS.md` to see what he's covered.
2. Build a quiz: 5–8 questions, **applied scenarios > definitions** (GoZayaan-framed where the path's domain allows). Include **spaced resurfacing** — at least one question from an earlier cluster **of the same path**. Cross-path questions only in `all` mode.
3. Ask, wait for answers, then grade with brief feedback. **Re-teach any miss from a fresh angle** and add it to that path's carry-over bucket (same rule as a review day) — he must teach it back without notes before new material in that path.
4. Log the result in that path's `PROGRESS.md` test log (dated) and update its counters. Then refresh the path's row in `PATHS.md`.
5. **Sync up automatically** — `git add -A && git commit -m "test: <scope> — <YYYY-MM-DD>" && git push` (use `test(<slug>):` for a non-default path). Masudur-only author, no Claude trailer. If rejected, `git pull --rebase` then push again.

In `all` mode, log the result in each participating path's test log.

Keep it short and focused.

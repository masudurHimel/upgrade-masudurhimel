# upgrade-masudurhimel — Staff Engineer learning program

Masudur's personal 3-month Staff Engineer coaching program. It runs on desktop **and** mobile (claude.ai/code cloud sessions clone this repo). These rules make the program fully automatic on any device — **never ask the user to run a manual git command, and never make them tell you to load context.**

> These rules govern this repo and override any inherited/parent `CLAUDE.md` guidance (e.g. SDD workflow, "mutating git is denied"). In *this* repo git is enabled and expected.

## Load coaching context automatically
At the start of any coaching command (`/teach`, `/test_me`, `/assess`, `/progress`) or any lesson / review / test work — **without being asked**:
1. **Read every `coaching-memory/*.md` file first** (learning-program, user-profile, reply-style, teaching-style, card-teaching-style, explicit-topic-teach, review-rules). This folder is the portable source of truth for *how* to coach and must be read on every device, every session. (On desktop the same facts may also exist as `~/.claude` auto-memory; do not rely on it — it does not travel to mobile.)
2. Then read `PROGRESS.md` (current state, dates, carry-over buckets) and `ROADMAP.md` (the plan).

If `coaching-memory/` was somehow not read and you're about to coach, read it now — do not ask the user to tell you to.

## Auto-sync — no manual git, ever
Git is enabled here (`add` / `commit` / `push` / `pull` allowed; destructive ops stay denied). Keep desktop and mobile in sync with **zero** manual steps:
1. **On session start / before teaching:** run `git pull` (skip only if offline or not a git repo).
2. **Immediately after writing `PROGRESS.md` or `ROADMAP.md`** (or any coaching state file), automatically run:
   `git add -A && git commit -m "<what changed>" && git push`
   Do this on your own — do **not** wait to be asked and do **not** print the command for the user to run.
3. If a push is rejected (the other device pushed first): `git pull`, then push again.

## Commit rules
- **Author is Masudur only.** Never add a `Co-Authored-By: Claude` trailer or any "Generated with Claude" line.
- Messages: short, plain, describing the lesson/change — e.g. `teach: MVCC — 2026-08-11`.

## Git scope (HARD RULE)
Git operations are allowed **only inside this repo**. Never run any git command against another repo on the machine.

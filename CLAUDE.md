# upgrade-masudurhimel — Staff Engineer learning program

Masudur's personal 3-month Staff Engineer coaching program. It runs on desktop **and** mobile (claude.ai/code cloud sessions clone this repo). These rules make the program fully automatic on any device — **never ask the user to run a manual git command, and never make them tell you to load context.**

> These rules govern this repo and override any inherited/parent `CLAUDE.md` guidance (e.g. SDD workflow, "mutating git is denied"). In *this* repo git is enabled and expected.

## Load coaching context automatically
At the start of any coaching command (`/teach`, `/test_me`, `/assess`, `/progress`, `/create_path`) or any lesson / review / test work — **without being asked**:
1. **Read every `coaching-memory/*.md` file first** (learning-program, learning-paths, user-profile, reply-style, teaching-style, card-teaching-style, explicit-topic-teach, review-rules). This folder is the portable source of truth for *how* to coach and must be read on every device, every session. (On desktop the same facts may also exist as `~/.claude` auto-memory; do not rely on it — it does not travel to mobile.)
2. Then read `paths/index.md` (the path registry) to resolve which path this session belongs to, and that path's `paths/<slug>/PROGRESS.md` (current state, dates, carry-over buckets) + `paths/<slug>/ROADMAP.md` (the plan). No path named ⇒ `default`.

If `coaching-memory/` was somehow not read and you're about to coach, read it now — do not ask the user to tell you to.

## Learning paths (HARD RULE)

The program runs **multiple parallel learning paths** under `paths/`. `default` is the 3-month Staff Engineer program and is **the default path** — bare `/teach`, `/progress`, `/test_me`, `/assess` resolve there.

- **`paths/index.md` is the registry** (name resolver + cached summary row per path). A path's own `PROGRESS.md` is **canonical** for its state; if they disagree, fix the registry.
- **Root `ROADMAP.md` / `PROGRESS.md` are MOVED stubs. Never write to them.** All state lives in `paths/<slug>/`.
- **Every path is fully independent** — its own learning-day counter, its own review cadence (every 3rd learning day *of that path*), its own carry-over buckets. **A bucket open in one path must never block a session in another path.**
- **Every teaching rule applies unchanged inside each path** (card style, teach-back gate, time-boxing, review-day bucketing). Multi-path changes *which files* are read and written — never *how* I coach.
- **Creating a path is never implicit.** `/teach some-unknown-name` still means *new topic on `default`*. New paths come only from `/create_path`.

Full mechanism: `coaching-memory/learning-paths.md`.

## Branch policy — `main` only (HARD RULE)
Every session, every device, works **directly on `main`**. There is **no branch strategy and no PR strategy** for this repo.
- **Never** create a working branch, feature branch, or `claude/*` branch. Never open a pull request. Never merge branches.
- Commit straight to `main`, pull from `main`, push to `main`. That's the entire flow.
- The mobile/cloud harness may *default* to a branch+PR flow — **do not follow it here.** Stay on `main`.

## Auto-sync — no manual git, ever
Git is enabled here (`add` / `commit` / `push` / `pull` / `pull --rebase` allowed; destructive ops stay denied). Keep desktop and mobile in sync on `main` with **zero** manual steps:
1. **On session start, before doing any work:** run `git pull` **first** to get the latest context (skip only if offline or not a git repo).
2. **Immediately after writing any coaching state file** (`paths/<slug>/PROGRESS.md`, `paths/<slug>/ROADMAP.md`, `paths/index.md`, `coaching-memory/*`), automatically run:
   `git add -A && git commit -m "<what changed>" && git push`
   Do this on your own — do **not** wait to be asked and do **not** print the command for the user to run.
3. If a push is rejected (the other device pushed first): `git pull --rebase` (keeps `main` linear — no merge commits), then push again.

## Commit rules
- **Author is Masudur only.** The commit *author identity itself* must be Masudur (`Masudur Rahman <masudur.rahman@gozayaan.com>`) — never commit **as** `Claude <noreply@anthropic.com>`. If the environment's git identity is set to Claude, this is wrong: stop and surface it, don't commit.
- Never add a `Co-Authored-By: Claude` trailer or any "Generated with Claude" line.
- Messages: short, plain, describing the lesson/change — e.g. `teach: MVCC — 2026-08-11`.

## Git scope (HARD RULE)
Git operations are allowed **only inside this repo**. Never run any git command against another repo on the machine.

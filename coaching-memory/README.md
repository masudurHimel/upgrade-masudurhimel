# coaching-memory/

Portable mirror of the `/teach` program's coaching context.

**Why this exists:** the live auto-memory lives at `~/.claude/projects/.../memory/` on the desktop and does **not** travel to mobile / cloud Claude Code sessions (different home dir). These in-repo copies let the coaching skills load full context on any device.

**Source of truth:** on desktop, the `~/.claude` auto-memory is still authoritative. These files are a mirror — if you edit coaching behavior, update both, or treat this folder as canonical when working from mobile. The hard program **state** lives in `paths/` (see below).

**Program state** (`PATHS.md` + `paths/<slug>/PROGRESS.md` / `ROADMAP.md`) is always canonical and in-repo.

Files:
- `learning-paths.md` — the multi-path system: registry, path resolution, full independence
- `learning-program.md` — how to run the 3-month Staff Eng program (the `default` path)
- `user-profile.md` — who Masudur is
- `reply-style.md` — short + focused
- `teaching-style.md` — clarity-first, concrete examples
- `card-teaching-style.md` — card structure + easy-words rule
- `explicit-topic-teach.md` — `/teach <topic>` behavior
- `review-rules.md` — review-day bucket + cadence

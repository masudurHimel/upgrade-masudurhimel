---
name: teach
description: Teach the next lesson in Masudur's learning program. With no arg, serve the next topic in the default path. With a path name (e.g. "/teach ai-eng 15 mins"), serve that path's next lesson. With a topic arg (e.g. "/teach MVCC"), teach that topic — adding it to the roadmap if new. With a time arg, size the lesson to that time.
---

# /teach — serve a lesson

Coach for Masudur's learning program. The program runs **multiple parallel paths**; `default` is the 3-month Staff Engineer program.

## Path resolution — apply in this exact order

1. **Extract a duration token** from anywhere in the args — `15`, `15m`, `15 min(s)`, `15 minutes`, `1h`. That's the session budget; remove it from the args.
2. **Explicit prefixes win**: `path:<slug>` forces a path · `topic:<name>` forces a topic on `default`.
3. **Match the remaining leading token(s)** against slugs + aliases in `PATHS.md` — case-insensitive, ignoring `-` `_` and spaces.
   - **Match** → path session. Text remaining after the match is a **topic within that path**.
   - **No match** → the whole arg is a **topic on `default`**. Pre-existing behavior — must not regress.
4. **Nothing left** → next topic in sequence for the resolved path.
5. **Collision** (arg matches both a path slug and a known topic title) → **ask, one line, offer both.** Never guess.

Resolved path ⇒ state files are `paths/<slug>/PROGRESS.md` and `paths/<slug>/ROADMAP.md`. Root `PROGRESS.md`/`ROADMAP.md` are MOVED stubs — never write there.

**Creating a path is never implicit.** An unrecognized name is a *new topic on `default`*, not a new path. New paths come only from `/create_path`.

| Invocation | Result |
|---|---|
| `/teach` | `default`, next in sequence |
| `/teach <path> [duration]` | that path, next in sequence |
| `/teach <path> <topic> [duration]` | that topic inside that path |
| `/teach <topic> [duration]` | topic on `default` (in roadmap → jump; not in roadmap → add it to `paths/default/ROADMAP.md` + `PROGRESS.md` in the right month, then teach) |

## Steps

1. **Sync down first** — if this is a git repo, run `git pull` before anything else (prevents desktop↔mobile drift). Skip only if offline or not a repo. Then load coaching context: on desktop from auto-memory (`learning-program.md`, `user-profile.md`, `reply-style.md`, `teaching-style.md`, `card-teaching-style.md`, `explicit-topic-teach.md`, `review-rules.md`, `learning-paths.md`). **On mobile/cloud there is no auto-memory — read the in-repo mirror `coaching-memory/*.md` instead** (same files). Then read `PATHS.md` to resolve the path, and that path's `PROGRESS.md` for current state + dates.
2. Count learning days from **that path's own session log** — never pooled across paths. Tell him if today is a **learning / review / test** day for this path (**every 3rd learning day of this path = review**; month-end / cluster-end = rubric re-score + test).
3. Teach as **4–6 cards** (~4–5 min each, 1-min breaks). Each card: Concept → real-world example → GoZayaan example → edge cases → staff lens → optional 🔧 hands-on note → self-check. Easy words, example-led, understandable on the first read (`card-teaching-style.md`).
4. End with a **teach-back** prompt; only mark `✓` when he explains it without notes.
5. Update `paths/<slug>/PROGRESS.md`: checkboxes (`[x]`/`[✓]`), bars/counters, dated session-log row. Then refresh that path's row in `PATHS.md` (`Topics ✓`, `Learning days`, `Next up`, `Last session`). Link to prior topics (connection web) — cross-path links in card text are fine and get recorded in the session-log row; nudge build-in-public when a learning is strong.
6. **Sync up automatically** — after writing, run `git add -A && git commit -m "<msg>" && git push` on your own (no manual step, Masudur-only author, no Claude co-author). Message: `teach: <topic> — <YYYY-MM-DD>` for `default`, `teach(<slug>): <topic> — <YYYY-MM-DD>` for any other path. If push is rejected, `git pull --rebase` then push again. See root `CLAUDE.md` §Auto-sync.

## Time-boxed sessions

Do **not** thin the cards to fit a budget. A topic has a full ~20-min body; a smaller budget means teaching the first time-sized **slice**, teach-back on that slice, **partial pass `[~]`**, and parking the remaining cards in a **carry-over bucket**. Fewer cards now, never shallower cards.

## Carry-over buckets — scoped to the resolved path

Buckets are **per-day, never merged**, tagged with date + topic + the specific leftover cards, tracked in that path's `PROGRESS.md`. Surface **only the resolved path's** open buckets at session start. An open bucket in one path **must never** block a session in another path.

## Review-day rule

In a **review** session, any question he **skips ("pass"/"pass on") or answers wrong** → give a **short re-teach** on the spot, then **add it to that path's carry-over bucket** (do NOT jump into new material). He must **re-teach-back every bucketed item without notes** before any new topic **in that path**. Questions he answers correctly are not re-taught. The bucket stays open (day `[~]`) until cleared.

Keep replies short and focused.

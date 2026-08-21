---
name: create_path
description: Create a new parallel learning path for Masudur — a separate specialized curriculum (AI engineering, Kubernetes, advanced Kafka, …) that runs alongside the default Staff Engineer program on the same engine. Runs an end-to-end intake (outcome, domain, depth, size, cadence, artifacts, prereqs, clusters, rubric), then generates paths/<slug>/ROADMAP.md + PROGRESS.md, a dedicated /teach-<slug> command, and registers it in root PATHS.md. Use when he says "create a learning path", "new path", "I want a separate track on X", or /create_path.
---

# /create_path — stand up a new learning path

Builds a new path under `paths/<slug>/` that runs the **same engine** as `default` (cards → teach-back gate → per-day buckets → review every 3rd learning day → tests → rubric) with **fully independent state**.

## Step 0 — load context

1. `git pull` (skip only if offline / not a repo).
2. Read `coaching-memory/*.md` — **all of them**, including `learning-paths.md`. On desktop the same facts may exist as `~/.claude` auto-memory; do not rely on it.
3. Read `PATHS.md` for existing slugs, aliases, and reserved words.

Arg handling: `/create_path <name>` pre-fills the name; `/create_path` with no arg asks for it.

## Step 1 — intake (ASK FIRST, GENERATE NOTHING)

**Hard rule: write no files until every question below is answered.** Batch the multiple-choice ones through `AskUserQuestion` (max 4 per call, so run ~2–3 calls); take free text for the open ones. Keep each question short — [[reply-style]] applies.

| # | Ask | Kind |
|---|---|---|
| 1 | **Name + outcome** — what do you want to be *able to do* at the end? (a capability, not a topic list) | free text |
| 2 | **Why now / where it pays off**, and should examples stay **GoZayaan-flavored** or use a different domain? | free text + choice |
| 3 | **Depth** — deep fundamentals + edge cases (the `default` style) · practitioner/applied · breadth-first survey | choice |
| 4 | **Size** — rough topic count + target weeks. Offer ~20 (4–5 wk) / ~40 (8–10 wk) / ~70 (14 wk, `default`-scale) anchors | choice |
| 5 | **Cadence** — default session length (2 / 5 / 10 / 20 min), days per week, checkpoint date | choice |
| 6 | **Artifacts** — N build artifacts · written docs/RFCs instead · **none** (counter suppressed) | choice |
| 7 | **Prereqs / links** — does this lean on `default` topics? (seeds the cross-path connection web) | free text |

Derive the **slug** (kebab-case) and a couple of natural **aliases** from the name. Reject and re-ask if the slug or an alias collides with an existing one or a reserved word (`default`, `all`, `path`, `topic`, `mins`, `minutes`).

## Step 2 — two review gates (still no files)

8. **Clusters.** Draft the cluster breakdown with topic IDs (`<PREFIX>N.M`, prefix derived from the slug — e.g. `AI1.3`), sized to his answers from #3–#4. Show it and let him **add / drop / reorder / rename** before anything is written. Do not skip this gate.
9. **Rubric.** Draft **4–6 competencies specific to this domain** (not the 7 staff ones) and have him **self-score a 1–5 baseline** for each. Compute the baseline average.

## Step 3 — generate

Only now write files.

1. `mkdir -p paths/<slug>/`
2. **`paths/<slug>/ROADMAP.md`** — mirror the shape of `paths/default/ROADMAP.md`:
   - path header (`> **Path:** \`<slug>\`` + registry link), owner, goal/outcome, start date, checkpoint date
   - a short "how this works" block (cards, the four engine mechanisms, the testing layers)
   - cluster tables: `| ID | Topic | Notes |`
   - `🎯 Artifact:` line per cluster-block (omit entirely if he chose *none*)
   - `🧭 Prove it at work:` hook per cluster-block
   - checkpoint section + a Phase-2 backlog for the domain
3. **`paths/<slug>/PROGRESS.md`** — the full template, in this order:
   1. **Header** — path name, slug, created date (today), checkpoint, status `active`, session default, `Review cadence: every 3rd learning day *of this path*`, links to `ROADMAP.md` + `../../PATHS.md`
   2. **Overall progress** — per-cluster ASCII bars + total, all at 0%, same style as `default`
   3. **Counters** — `Artifacts 0/N` (or `—` if none) · `Tests passed 0` · `Teach-back ✓ 0`
   4. **Next up** — first topic; note that the first session is learning day 1
   5. **🪣 Carry-over buckets** — the per-day/never-merged preamble + "none open"
   6. **Topic checklist** — grouped by cluster, every row `[ ]`, artifacts as `[ ] 🎯 Artifact: …`
   7. **Test log** — empty table
   8. **Session log** — empty table
   9. **Path rubric** — the 4–6 competencies × baseline + monthly columns, with the dated baseline average noted below it
4. **`.claude/skills/teach-<slug>/SKILL.md`** — the path's own teach command, so `/teach-<slug>` exists as a first-class slash command. Thin wrapper, not a copy:
   - frontmatter `name: teach-<slug>`, and a `description` naming the path + its clusters so the command is discoverable
   - **path is pinned to `<slug>` — do NOT run path resolution**
   - args are **duration and/or topic only** (`/teach-<slug> 15 mins`, `/teach-<slug> <topic>`); a path name in the args is ignored, not re-resolved
   - body: "follow `.claude/skills/teach/SKILL.md` Steps 1–6 verbatim with `<slug>` as the resolved path", then restate the per-path specifics — day counting from that path's own session log, its own buckets, the `teach(<slug>):` commit prefix, and that no other path's bucket may block or be mentioned
   - **only `teach` gets a per-path command.** `progress` / `test_me` / `assess` keep taking the shortcut as an argument (`/progress <slug>`).
5. **Register** — add the row + aliases to `PATHS.md` (`Topics ✓ 0/N`, `Learning days 0`, `Next up` = first topic, `Last session —`). Do not touch the `DEFAULT` marker.

## Step 4 — sync + hand off

1. `git add -A && git commit -m "path: create <slug>" && git push` — automatically, no manual step. Masudur-only author, no Claude co-author trailer. If push is rejected: `git pull --rebase`, then push again. See root `CLAUDE.md` §Auto-sync.
2. Print a compact summary: slug, aliases, topic count, clusters, cadence, artifacts, rubric baseline avg.
3. End with the exact next command: **`/teach-<slug> <duration>`** (the dedicated command generated in Step 3.4).

## Guardrails

- **Never** touch `paths/default/*` or another path's files.
- **Never** make this path the default. Exactly one path carries `DEFAULT`; changing it is a separate conversational request.
- The new path starts at **learning day 0** — fully independent counter. It inherits no buckets and is not blocked by any other path's open bucket.
- If he asks for a path that already exists, say so and offer `/teach <slug>` or reshaping it via `add`/`drop <topic> in <slug>`.

Keep replies short and focused; the intake questions are the only long part.

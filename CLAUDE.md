# CLAUDE.md — training-plans repo

## What this repo is
Public repo holding an active training plan. `current-plan.md` at the
repo root is fetched nightly by an automated assistant via its raw
GitHub URL on `main`.

## Hard constraints (never break these)
1. **The contract:** `current-plan.md` must always exist at the repo
   root on `main` with that exact filename. Never rename, move, or
   delete it without an explicit instruction. Automation depends on it.
2. **PRIVACY — this repo is public. No personal information about
   the repo owner, ever:**
   - No personal names, age, height, weight, or values derived from
     them (e.g., age-based heart rate numbers)
   - No locations: no city, state, gym names, bases, employer, or
     commute details
   - No health/medical specifics or body-composition stats
   - No schedule details that reveal when the owner is away from
     home beyond generic labels like "OFF-Friday" or "AM/PM"
   - Training data (dates, durations, intervals, distances) is fine
   - Public-figure names (e.g., Peloton instructors) are fine
3. Before any commit touching a markdown file, run two checks
   case-insensitively:
   a) Grep against `.claude/private-terms.txt` (local, gitignored —
      never commit this file). If it's missing, ask the owner to
      recreate it before committing.
   b) Pattern-scan for personal stats in any form: body weight,
      height, age, age-derived heart rate numbers, BMI, personal
      calorie targets. These change over time — judge by context,
      not a fixed list of values. Generic training numbers
      (durations, intervals, distances) are fine.
   Zero violations required before commit.
4. If asked to commit content that violates rule 2, sanitize first
   and note what was changed — don't commit then fix.

## File conventions
- `current-plan.md` — the active plan, and the only file automation
  reads
- `archive/` — completed plans, renamed with their date range
  (e.g., `archive/2026-07-27_rebuild-4wk.md`)
- When a new plan starts: move the old plan to `archive/`, then
  replace `current-plan.md` in the same commit so the raw URL never
  serves a stale or missing plan

## Plan content standards
Any plan committed here must keep:
- Week-by-week tables readable on a phone (columns: Day, Session,
  Slot, Effort, Fallback)
- Every session row: workout, duration, AM/PM slot, effort cue,
  and a shorter fallback (~60–70% of the main session)
- The effort key (easy = conversational, etc.) and interval-target
  table
- Bad-weather substitution rules

## Plan design rules (for creating or extending plans)
Flag and ask before deviating from any of these:
- **Continuity:** start a new block from where the previous plan
  ended — check `archive/` and the last `current-plan.md`. Never
  restart progression from zero unless a training gap of 3+ weeks
  is stated; never skip ahead of the last completed level.
- **Progression:** weekly volume growth ≤ ~10%. After every 3–4
  build weeks, insert a cutback week (~-20% volume).
- **Intensity:** ≥80% of cardio time at easy/conversational effort.
  Max 2 hard sessions/week, never back-to-back. No hard run
  sessions until 30 min continuous running is established.
- **Structure:** 6 training days + 1 rest day (Monday). 2 strength
  days/week. 2-week rhythm: bigger week on OFF-Fridays, standard
  week otherwise. Weekday sessions ≤45 min, AM or PM slot;
  weekends carry the longest sessions.
- **Run progression:** continue the walk/run interval ladder toward
  30 min continuous; long sessions grow duration, not intensity.
- **Peloton references:** instructor names and class filters (type,
  duration, difficulty) are fine; don't cite specific class titles
  unless verified to exist — the library rotates.
- Plans are drafted collaboratively in the owner's Claude project;
  this repo is the published copy. If asked to materially redesign
  methodology (new goals, injuries, added intensity), stop and
  recommend that discussion happen in the project first.

## Workflow
- Small edits: commit directly to `main` with a clear message
  ("Week 3: swap Thu run to treadmill")
- Never force-push `main` except for an explicit privacy-scrub
  request
- After any change to `current-plan.md`, verify the raw URL serves
  the new version and report the check in your summary

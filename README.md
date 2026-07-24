# training-plans

Training plans, one file per plan, plus a stable pointer for automation.

## Convention

- **Every plan gets a dated file** — e.g. `4-week-training-plan-jul27-aug23.md`. These are archival and never change once a plan ends.
- **`current-plan.md` is always an exact copy of whichever plan is active.** Never rename it — an unattended scheduled task fetches it nightly by raw URL.

## When a new plan starts

1. Add the new plan as its own dated file.
2. Overwrite `current-plan.md` with an exact copy of that file:
   ```bash
   cp new-dated-plan.md current-plan.md
   git add -A && git commit -m "Activate new plan" && git push
   ```

## Fetching the active plan

```
https://raw.githubusercontent.com/<username>/training-plans/main/current-plan.md
```

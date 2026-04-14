# Daily-Green — CLAUDE.md

## What This Is
A GitHub Actions cron job that makes one commit per day to keep the contribution graph green. Commentary on the culture of judging developers by GitHub activity metrics.

## How It Works
- Runs daily at 16:00 UTC via `schedule` trigger (also has `workflow_dispatch` for manual runs)
- Appends a timestamped line to `heartbeat.txt`
- Trims the file to the last 365 lines (rolling year)
- Skips the commit if today's date already exists in the file (idempotent)
- Uses Mountain Time (America/Denver) for date formatting

## Structure
```
.github/workflows/daily-green.yml   # The entire project
heartbeat.txt                        # Rolling 365-day log of daily commits
```

## Notes
- No code to run locally — this is entirely a GitHub Actions workflow
- The repo's purpose is self-referential: it exists to expose the arbitrariness of green-square metrics
- `workflow_dispatch` lets you trigger a commit manually from the GitHub Actions UI

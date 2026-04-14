# Daily-Green

A GitHub Actions cron job that commits once per day to maintain a green contribution graph.

Programmers today are judged off of many arbitrary factors, including how green one's GitHub is. This cron job serves to expose the flaws in such reasoning.

## How It Works

A scheduled workflow runs daily at 16:00 UTC, appends a timestamped entry to `heartbeat.txt`, and commits it. The file is trimmed to a rolling 365-day window. The commit is skipped if today already has an entry (idempotent).

## Trigger

- **Scheduled**: daily at 16:00 UTC
- **Manual**: via `workflow_dispatch` in the GitHub Actions UI

## Files

- `.github/workflows/daily-green.yml` — the entire project
- `heartbeat.txt` — rolling log of daily commits

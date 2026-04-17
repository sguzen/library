---
title: Claude Code Scheduling — Routines vs Desktop Schedules vs /loop
source: ai/raw/Claude Schedules vs Routines (What's the difference).md
---

Claude Code has three ways to run work automatically. Most people don't know the difference and pick the wrong one. The key axis: cloud vs. local execution.

## The Three Options at a Glance

| | Routines | Desktop Schedules | /loop |
|--|---------|-------------------|-------|
| **Where it runs** | Anthropic cloud | Your machine | Current session |
| **Laptop required** | No | Yes | Yes |
| **File access** | Repo clone only | Local files + MCP | Current directory |
| **Minimum interval** | 1 hour | 1 minute | ~1 minute |
| **Survives restart** | Yes | No (catch-up on wake) | No |
| **Trigger types** | Schedule, API, GitHub events | Schedule only | Interval only |
| **Setup location** | claude.ai/code/routines | Desktop app Schedule page | Type /loop in session |

---

## 1. Routines — Your Agent in the Cloud

Routines run on Anthropic's managed cloud infrastructure. Laptop can be closed or off — the routine still runs. Available on Pro, Max, Team, and Enterprise plans. Currently in research preview.

**What a routine is:** a saved configuration — prompt + one or more GitHub repos + model selection + external service connectors (Gmail, Slack, Linear).

**Three trigger types:**
- **Schedule** — hourly, daily, weekdays, or weekly (minimum: 1 hour)
- **API** — a dedicated HTTP endpoint with a bearer token; POST to it from any external system
- **GitHub Events** — pull requests, pushes, issues, releases; 17 event types with filters for author, branch, and labels

You can stack multiple triggers on the same routine.

**The key limitation:** routines don't have access to local files. Every run clones your repository fresh. If your workflow depends on files that aren't in a repo, routines aren't the right fit.

**Create them at:** `claude.ai/code/routines`, from the Desktop app, or with `/schedule` in the CLI.

---

## 2. Desktop Scheduled Tasks — Your Agent on Your Machine

Desktop schedules run locally. Direct access to local files, local tools, and MCP servers. The trade-off: your computer needs to be on and the Desktop app needs to be running.

**Create them:** Desktop app → Schedule page → New Task → New Local Task → name + prompt + frequency.

**Frequency options:** manual, hourly, daily, weekdays, or weekly. Minimum interval: 1 minute.

**Key differences from routines:**
- **Local file access** — runs against your actual working directory, including uncommitted changes (routines get a fresh clone)
- **Permission prompts** — configurable whether the task asks for approval before running commands (routines are fully autonomous)
- **Missed run catch-up** — if the computer was asleep, one catch-up run on wake (not every missed run)

**Pro tip:** after creating a task, click Run Now and watch for permission prompts. Select "always allow" for each one so future runs don't stall.

**Lid behavior:** closing the laptop lid stops tasks. Enable "Keep computer awake" in Settings to prevent idle sleep — but closed lid still stops everything.

---

## 3. /loop — Quick Polling in a Live Session

The simplest option. Runs a prompt on repeat inside a live Claude Code session. Session-scoped: when you close the terminal, the loop dies.

**Three usage patterns:**
```
/loop 5m check the deploy       → fixed 5-minute interval
/loop check the deploy          → Claude picks interval based on what it observes
/loop                           → runs a built-in maintenance prompt (or custom loop.md)
```

**Limitations:**
- Dies with the session (can survive with tmux locally)
- Expires after 7 days automatically
- No cloud execution

**Best for:** watching a build, babysitting a PR, polling CI status — anything where you're actively working and want background monitoring.

---

## Decision Matrix

**Use Routines when:**
- Your laptop needs to be off (overnight jobs, travel)
- The work is repo-based (code reviews, PR checks, deploy monitoring)
- You want to trigger from external systems via API
- You want to react to GitHub events

**Use Desktop Schedules when:**
- You need access to local files not in a repo
- You want granular timing (under 1 hour)
- You want approval control before commands run
- You're comfortable leaving your machine on

**Use /loop when:**
- You're in an active session and want background monitoring
- The task is short-lived (this session only)
- You want the simplest possible setup

---

## Related

- [[claude-products-guide]] — Managed Agents as the cloud infrastructure layer for longer-running autonomous work
- [[openclaw-agent-team]] — cron-based agent scheduling outside of Claude Code (using OpenClaw's gateway)
- [[hermes-agent]] — alternative agent platform with its own scheduling via cron state per profile

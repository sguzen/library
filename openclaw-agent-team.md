---
title: OpenClaw 24/7 Agent Team — Six Specialized Agents Running While You Sleep
sources:
  - ai/raw/How I built an Autonomous AI Agent team that runs 247.md
  - ai/raw/How to run a 247 AI Agent that Grows with You.md
---

A practical setup for running six specialized AI agents autonomously on a local machine, each with a distinct role, connected via Telegram for mobile interaction. The system does research, writing, code review, and newsletter drafting before you wake up — and a follow-up experiment comparing OpenClaw's manual improvement model against Hermes Agent's self-improving learning loop.

## Why a Team Instead of One Agent

One agent trying to hold six jobs degrades in all of them. Context fills up. Quality drops. Specialization disappears. The fix: one agent per job, with clean role boundaries and no shared context pollution.

## The Six-Agent Roster

Named after TV characters for a specific reason: Karpathy-era models have absorbed decades of character-consistent training data. Telling Claude "you have Dwight Schrute energy" loads 30 seasons of characterization for free.

| Agent | Character | Job |
|-------|-----------|-----|
| **Monica** (Chief of Staff) | Monica Geller | Main contact; coordinates the others; strategic decisions; delegates tasks |
| **Dwight** (Research) | Dwight Schrute | Runs research sweeps 3×/day: X, Hacker News, GitHub trending, AI blogs, papers |
| **Kelly** (Twitter/X) | Kelly Kapoor | Reads Dwight's reports; drafts tweets in the owner's voice |
| **Rachel** (LinkedIn) | Rachel Green | Same intel, different platform; thought leadership angle |
| **Ross** (Engineering) | Ross Geller | Code reviews, bug fixes, technical implementations |
| **Pam** (Newsletter) | Pam Beesly | Turns Dwight's daily intel into a newsletter digest |

Each agent has a `SOUL.md` file defining their personality and behavioral rules. Monica's: "You're the one who makes sure everything gets done right." Ross's: "When you tackle a problem, understand it fully. Don't just fix the symptom."

## Setup (Mac Mini M4, but any machine works)

**Infrastructure:** Mac Mini M4 base, always on, no monitor, Telegram for all interaction. Any machine works: macOS, Linux, Windows (via WSL), even a $5/month VPS. Always-on hardware is the only real requirement.

**Install OpenClaw:**
```bash
curl -fsSL https://openclaw.ai/install.sh | bash
openclaw onboard
```

The gateway starts — a background process that keeps agents alive, manages cron jobs, and handles Telegram messages. Close your terminal; agents keep working.

**Workspace structure:** one OpenClaw instance, one directory, six agents inside it. Not six installations.

**File structure per agent:**
```
workspace/
├── monica/
│   ├── SOUL.md        ← identity and behavior rules
│   ├── memory/        ← persistent context
│   └── skills/        ← reusable task procedures
├── dwight/
│   ├── SOUL.md
│   ├── intel/         ← research outputs for other agents to read
│   └── ...
└── [other agents]
```

## The Correction Loop (OpenClaw's Model)

OpenClaw agents improve through **corrective prompt-engineering**: you watch the agent, notice a failure, explain the fix, update memory or `SOUL.md`, and wait for the behavior to stick.

This loop works. Kelly's early drafts were full of emojis; explicit feedback fixed it over a week. Dwight captured too much noise; explicit guidance tightened the signal.

**The hidden assumption:** you are the learning system. Every improvement depends on you noticing the problem, diagnosing it, and writing down the correction. The agents don't get better while you sleep — they get better when you pay attention.

## The Self-Improvement Experiment (Hermes Comparison)

A second Monica was set up on Hermes Agent running in parallel on the same machine:

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
hermes setup
```

Hermes detected the existing OpenClaw install and offered to import settings, memories, and API keys.

**What happened differently:**

The first signal: `~/.hermes/skills/` contained files nobody created manually. One stood out: `local-writing-canon-analysis/SKILL.md` — Monica had written a procedure for reading published articles before drafting in the owner's voice. Not "I know your style" in the abstract. Concrete editorial rules extracted from what actually survived editing.

She also captured operational playbooks, workflow procedures, and reusable task patterns. Not all were useful, but the default behaviour — turning completed work into reusable procedure — was new.

**The key difference:**

| | OpenClaw Monica | Hermes Monica |
|--|----------------|---------------|
| **Improvement trigger** | You notice and teach | Agent evaluates and writes skill files |
| **Who owns the loop** | You + the agent | Mostly the agent |
| **Memory pattern** | Stores what you explicitly teach | Stores what she decides is worth keeping |
| **Transparency** | You write the corrections | She writes files you can inspect/edit/delete |

Hermes doesn't eliminate your role — you can still inspect and edit skill files. But you don't have to initiate improvement. The agent closes more of the loop itself.

## What Still Breaks

**Hallucinated confidence:** agents treat partial data as complete. During a migration, Monica treated the Hermes archive as if it contained everything from OpenClaw — it didn't. She inferred completeness from partial data.

**Gateway status ≠ health:** after a restart, the gateway reported as loaded but the bot wasn't responding. The status screen lied; the logs told the truth. Monica turned this into a recovery skill automatically, including a diagnostic sequence that verifies live Telegram reconnect before declaring success.

**Rule:** status screens flatter you. Logs tell the truth.

## Related

- [[hermes-agent]] — the self-improving learning loop that distinguishes Hermes from OpenClaw
- [[agent-memory-architecture]] — the memory systems that make agent improvement possible
- [[claude-scheduling]] — Claude Code's native scheduling options (Routines, Desktop Schedules, /loop) as an alternative approach
- [[claude-products-guide]] — Claude Managed Agents as the cloud-hosted equivalent

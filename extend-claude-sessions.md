---
title: Extending Claude Sessions with NotebookLM
source: ai/raw/I want to extend my Claude sessions (full guide).md
---

A guide to integrating Claude Code with Google NotebookLM via the unofficial `notebooklm-py` CLI tool to offload heavy document analysis, preserve memory across sessions, and dramatically reduce token consumption.

## The Problem

Claude's billing model burns tokens on everything fed into the context window. On the Pro plan ($20/month) heavy research drains limits fast — leaving roughly 30–45 minutes of productive work per day. The root cause is "Claude's amnesia": every session starts fresh, and large document analysis costs the same tokens each time.

## The Solution: notebooklm-py Bridge

Developer Teng Ling reverse-engineered NotebookLM's internal protocols and published an open-source CLI tool (`notebooklm-py`) that lets you control NotebookLM entirely from the terminal — create notebooks, upload sources, run queries, generate outputs.

NotebookLM (Google's RAG research tool) handles up to 50 sources per notebook on the free tier (300 on Pro) at zero processing cost. Combining it with Claude Code via this bridge means Google's infrastructure does the expensive analytical work; Claude only burns tokens on orchestration and final editing.

> **Caution:** `notebooklm-py` uses reverse-engineered protocols. Google could break it at any time. Treat it as a power-user productivity tool, not production infrastructure.

## Installation

Requires Python 3.10+, a Google account, and a terminal (macOS, Linux, Windows).

```bash
# See: https://github.com/teng-lin/notebooklm-py
notebooklm skill install   # deploys skill to ~/.claude/skills/notebooklm/
notebooklm skill status    # verify
```

## Claude Skills Integration

Skills are SKILL.md instruction files Claude reads automatically when it detects a matching request. They work across Claude Code, Cursor, Gemini CLI, and Codex.

- **Personal skills:** `~/.claude/skills/<skill-name>/SKILL.md`
- **Project skills:** `.claude/skills/<skill-name>/SKILL.md` (overrides personal)

The `skill-creator` meta-skill (`/skill-creator`) can generate custom skills from a description, including automated test prompts.

## Four Workflows

### A: Zero-Token Research
Offload analysis of 30+ documents to NotebookLM. Claude orchestrates; Google processes.

```bash
notebooklm create "My Research Project"
notebooklm source add "./report.pdf"
notebooklm source add "https://example.com/article"
notebooklm ask "what are the three most important themes?"
notebooklm generate slide-deck
notebooklm generate flashcards --quantity more
```

Claude only uses tokens for final editing/polishing. A $20/month plan does the work of a $200/month workflow.

### B: Building Expert AI Agents from Web Research
1. Use NotebookLM's Deep Research to crawl hundreds of pages on a domain topic.
2. Organise findings into the **DBS framework**: Direction (step-by-step logic), Blueprints (reference material), Solutions (deterministic code tasks).
3. Feed the DBS output to `/skill-creator` → Claude scaffolds a complete, tested skill package.

### C: Persistent Memory Across Sessions
Build a `/wrap-up` skill that extracts session learnings (corrections, decisions, patterns) and uploads a summary to a "Master Brain" NotebookLM notebook at the end of every session.

```bash
notebooklm use <master-brain-notebook-id>
notebooklm source add "./session-summary-2026-04-06.md"
```

Add a retrieval instruction to `CLAUDE.md` so Claude queries the Master Brain notebook before answering architecture or preference questions. Over weeks the knowledge base accumulates and grows semantically indexed — Claude effectively remembers everything while using Google's free infrastructure for storage and retrieval.

### D: Visual Knowledge Management with Obsidian
Run Claude Code from inside an Obsidian vault root. Everything Claude creates appears instantly in Obsidian's graph view.

```bash
cd ~/Documents/MyVault
claude
```

Define folder structure, metadata requirements, linking rules (using `[[double brackets]]`), and formatting standards in a `CLAUDE.md` at the vault root. Build custom skills: `/research`, `/daily`, `/wrap-up`. Claude files, tags, and cross-links everything automatically. See also [[obsidian-chief-of-staff]].

## Security Notes

- `storage_state.json` contains live Google session cookies — never commit to a public repo.
- Cookies expire periodically; re-authenticate with `notebooklm login`.
- UK/EU users: Claude's consumer tools process data in the US; GDPR implications apply for regulated data.

## Related

- [[free-ai-via-github-copilot]] — alternative approaches to reducing AI costs
- [[ai-subscription-cost-optimization]] — token efficiency tools (RTK, Caveman)
- [[obsidian-chief-of-staff]] — using Claude + Obsidian as a Chief of Staff
- [[hermes-agent]] — alternative persistent agent architecture

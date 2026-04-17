---
title: Hermes Agent
sources:
  - ai/raw/Hermes Agent Clearly Explained.md
  - ai/raw/What Hermes Agent Can Do for You (And Why It Matters).md
---

Hermes Agent is an open-source, self-hosted AI agent built by [Nous Research](https://nousresearch.com/) that runs persistently on a server or laptop, remembers everything across sessions, and gets progressively smarter through a closed learning loop. It reached 50K GitHub stars within two months of launch.

## Core Concept

Most AI tools (ChatGPT, Claude chat) are stateless: close the tab, lose all context. Hermes is designed to fix this:

- **Persistent** — runs 24/7 on a cheap VPS or personal machine
- **Multi-modal access** — reachable via Telegram, Discord, Slack, WhatsApp, Signal, Email, Home Assistant (15+ platforms), or CLI
- **Self-improving** — every ~15 tool calls, Hermes pauses, reviews what worked and what failed, and writes a new skill (a Markdown file at `~/.hermes/skills/`) encoding what it learned as a reusable workflow
- **Model-agnostic** — runs on any model; switch with `hermes model`

## The Three-Layer Stack

### Layer 1: Knowledge Layer (LLM-Wiki)
Hermes ships with Andrej Karpathy's LLM-Wiki pattern as a built-in skill. Unlike RAG (which rediscovers relevant chunks on each query), an LLM-Wiki is a dynamic, interlinked encyclopedia: structured, cross-referenced, and continuously updated as new sources are added.

When new material is ingested, the agent doesn't just file it — it checks existing pages, updates anything that changed, adds cross-references, and flags contradictions. After a month of regular use, you have a compounding knowledge base.

### Layer 2: Execution Layer (Multi-Agent Profiles)
Since v0.6.0, a single Hermes installation supports multiple isolated agents, each with its own memory, sessions, skills, and gateway services. The main agent can spin up specialised subagents on demand.

Example: a marketing agency setup with one installation — a research agent, a writing agent, an organising agent, and an email assistant — each with context from the shared knowledge layer.

**Key advantage:** unified memory means marketing context is available when doing outreach because it's the same agent that handled both. Multi-agent setups with disconnected tools lose this compounding.

### Layer 3: Output Layer
Notable built-in skills:
- **Manim skill** — generates 3Blue1Brown-style programmatic animations for technical explainers
- **Autonovel** — Hermes wrote a 19-chapter, 79,456-word novel, peer-reviewed by Claude
- **Autoresearch pattern** — agent makes a small change, measures it, keeps the winner, repeats

## How It Differs from Claude Code and OpenClaw

| | Claude Code | OpenClaw | Hermes |
|---|---|---|---|
| **Lives in** | Your repo | Your server | Your server |
| **Primary use** | Code, tests, commits | Personal agent | Personal agent + automation |
| **Learning loop** | No | No | Yes |
| **Messaging** | No | Yes | Yes (15+ platforms) |
| **MCP support** | Yes | No | Yes (v0.8.0+) |

**The right architecture:** run Claude Code for software development; run Hermes for everything else. They share the same MCP protocol, so tool integrations (Google Workspace, databases, custom APIs) work in both — build the MCP layer once and both agents use it.

## Quick Start

```bash
curl <install-script>   # one-command install
hermes                  # launch
hermes model            # select model (use a frontier model — local models often fail at tool calling)
hermes gateway setup    # connect Telegram or preferred messaging platform
```

Migrating from OpenClaw: `hermes claw migrate` imports persona, memories, skills, API keys, and messaging settings.

## Real-World Workflows

- **Morning briefings** — monitor email, calendar, and 3 topics; Hermes learns which senders you respond to and refines the daily briefing over time
- **Web monitoring** — ships with Camoufox (stealth browser that avoids fingerprinting) + Firecrawl for structured extraction; runs change-tracking on competitor pages, job boards, product listings
- **Single agent replacing a team** — a fintech founder collapsed five disconnected specialised agents into one Hermes instance; unified memory fixed context fragmentation
- **Automated trading** — builders have deployed Hermes with brokerage API keys running live automated strategies
- **Self-optimising experiments** — define a metric to improve (e.g. email open rates), tell Hermes to make small changes and keep winners

## Model Selection Warning

The #1 reason Hermes setups feel broken is wrong model choice — the agent hallucinates tool calls that don't exist. For the workflows above, use a frontier model API. For local experiments, Gemma 4 26B via Ollama is currently the best local option.

Run `hermes doctor` to diagnose configuration issues before spending hours debugging.

## Community

643 community skills available in the Skills Hub, browsable with `/skills` inside Hermes.

## Building a Multi-Agent Team with Hermes Profiles

Since v0.6.0, Hermes profiles allow role-based multi-agent teams with fully isolated state. A profile separates: configuration, sessions, memory, skills, personality, cron state, and gateway behaviour.

This matters because multi-agent systems fail when everything shares the same memory and tone. A coding agent should not inherit the stylistic defaults and priorities of a research agent. Clean role boundaries produce more coherent specialization over time.

**A proven four-role team structure:**

| Profile | Role | Job |
|---------|------|-----|
| Orchestrator | Planning and synthesis | Defines goals, splits work, routes to specialists, synthesizes results |
| Research agent | Information gathering | Sources, validates claims, turns raw info into decision-ready findings |
| Writer agent | Communication | Turns validated material into clear, structured output |
| Engineer agent | Implementation | Builds, tests, fixes, and delivers reliable systems |

The orchestrator is a traffic controller, not a bottleneck. Its job is not to do every task — it's to ensure the right specialist handles each piece.

**Key principle:** the leap from one agent to a real multi-agent team starts with isolation, not with better prompting.

For a practical real-world implementation using OpenClaw (same concept, different platform), see [[openclaw-agent-team]].

## Related

- [[extend-claude-sessions]] — Claude Code + NotebookLM as an alternative persistent memory architecture
- [[obsidian-chief-of-staff]] — Obsidian + Claude Code as a structured knowledge/productivity system
- [[ai-learning-workflow]] — the LLM-Wiki pattern underpins both Hermes's knowledge layer and this learning system
- [[polymarket-trading-engine]] — example of autonomous agent managing live trading systems
- [[openclaw-agent-team]] — detailed 24/7 agent team setup and direct comparison of OpenClaw vs. Hermes learning models
- [[agent-memory-architecture]] — the memory systems that underpin Hermes's self-improvement loop

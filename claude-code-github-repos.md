---
title: 9 GitHub Repos That Transform Claude Code into an Agentic System
source: ai/raw/9 GitHub Repos Killed My $200Month Claude Habit.md
---

Nine open-source repositories that shift Claude from a stateless chatbot ($200/month Pro) into an agentic system with persistent memory, automated workflows, and structured execution — dropping effective cost to $20/month while increasing output quality and project completion rates. All repos are MIT-licensed with no paywalls.

## The Core Problem They Solve

Without tooling: Claude forgets context every session, requires manual instruction-loading, produces random outputs, and drains Pro credits fast.

With tooling: persistent memory across sessions, auto-loaded skills, structured workflows, and consistent project progress at a fraction of the token cost.

## The 9 Repos

### 1. Superpowers (137K stars)
`github.com/obra/superpowers`

A complete software development workflow for Claude Code. Skills trigger automatically. The agent asks what you're really trying to build, creates a spec, writes a plan, then executes with TDD — without micromanagement.

**Best for:** Anyone who wants Claude to self-direct software projects rather than wait for instructions at each step.

### 2. Awesome Claude Code (30.9K stars)
`github.com/hesreallyhim/awesome-claude-code`

The App Store equivalent for Claude Code. Curated list of skills, hooks, slash-commands, agents, and plugins. Every common workflow problem has likely been solved here already.

**Best for:** Finding existing solutions before building custom ones.

### 3. GSD (Get Shit Done)
`github.com/glittercowboy/taches-cc-resources`

Subagents and commands built around one principle: adapt to your workflow, not the other way around. Lightweight and opinionated.

**Best for:** People who want AI that fits existing habits rather than requiring new ones.

### 4. Claude Mem
`github.com/thedotmack/claude-mem`

Persistent memory across Claude sessions. Claude remembers the project, stack, decisions, and context from session one onward — eliminating the 10-minute re-explanation at the start of every session.

**Best for:** Anyone working on a multi-session project. The most immediate pain-point fix in the list.

### 5. LightRAG (29.3K stars)
`github.com/hkuds/lightrag`

Academic project from University of Hong Kong (EMNLP 2025). Retrieval-Augmented Generation with knowledge graphs — builds a graph of concept relationships and retrieves answers faster and more accurately than linear document search.

**Best for:** Working with large codebases, documentation sets, or knowledge bases where linear search fails.

### 6. Everything Claude Code
`github.com/affaan-m/everything-claude-code`

Modular collection covering practically every engineering domain and Claude Code feature: skills, subagents, workflows. Take only what's relevant.

**Best for:** Building a customized setup piece-by-piece rather than adopting a full framework.

### 7. n8n-MCP
`github.com/czlonkowski/n8n-mcp`

MCP server connecting n8n (automation tool) directly to Claude Code. Claude becomes an automation brain that can trigger real-world workflows: `Claude Code → n8n-MCP → n8n workflows → real-world actions`.

**Best for:** People who already use n8n or want Claude to drive automations beyond code generation.

### 8. Obsidian Skills
`github.com/kepano/obsidian-skills`

Skills that let Claude work natively inside an Obsidian vault: read notes, create connections, build on existing knowledge. Claude knows what you know.

**Best for:** Knowledge workers whose second brain lives in Obsidian.

### 9. AI-Trader (HKUDS)
`github.com/HKUDS/AI-Trader`

LLM trading agent that connects to market data and news feeds and generates trading signals. See [[polymarket-trading-engine]] for a detailed breakdown.

**Best for:** Anyone building AI-assisted trading on prediction markets.

## Recommended Starting Stack

```
Step 1: Drop to Claude $20 plan
Step 2: Install Claude Code (free CLI)
Step 3: Install Superpowers → /plugin install superpowers
Step 4: Bookmark awesome-claude-code for everything else
Step 5: Add Claude Mem for persistent memory
Step 6: Pick 2-3 domain repos relevant to your work
```

One afternoon to set up. No more re-explaining context.

## Related

- [[extend-claude-sessions]] — NotebookLM integration to further reduce token burn on heavy analysis
- [[autoskills]] — auto-install skills based on project tech stack detection
- [[ai-subscription-cost-optimization]] — complementary token efficiency strategies
- [[polymarket-trading-engine]] — AI-Trader in practice

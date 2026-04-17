---
title: AI-Era Learning Workflow
source: ai/raw/How I Turn Learning Into a Workflow in the AI Era.md
---

A systematic approach to deep learning in the AI era that treats research as a structured workflow — from source collection through filtering, outlining, drafting, and publishing — rather than passive consumption. Authored by [@HiTw93](https://x.com/HiTw93), the creator of the Waza skill library.

## Core Principle

**Input is overrated. Output is what matters.** How much you read matters less than how much you can produce, explain, and publish. What you can write clearly and organise becomes yours; what you passively consume often doesn't.

AI is most useful when attached to real output. Asking AI to summarise things creates a feeling of productivity while building nothing solid. When you are seriously writing, explaining, or building something, AI becomes genuinely useful as an amplifier — not a replacement for judgment.

## The Workflow

### 1. Collect High-Quality Sources
Deliberately curate before reading:
- Strong papers from recent years
- Key blog posts from major model labs
- Posts from people leading model work on X
- Stanford/university courses from the last couple of years
- Classic repositories showing how to build systems from scratch

Use tools to automate the boring parts: download, convert to Markdown, clean, organise, and categorise into a dedicated research repo. Get the information environment in good shape before reading begins.

### 2. Read and Filter
Read what you can understand directly — keep what deserves to stay, delete the bad. For material you can't understand, use Claude to work through it. Translate harder pieces if needed. Run code locally where possible.

Goal at this stage: a real working understanding of the field and its core technical logic — not mastery. **Expect to cut half the material.** Filtering is part of learning; keeping the right things matters more than reading more.

### 3. Outline the Article
Once a rough map of the field exists, think about:
- What to cover and what order makes sense
- Which sources belong to which section
- What you want readers to understand when they finish

Writing is always for an audience. Know what they already know, where they'll get lost, what level of explanation they need.

### 4. Draft Section by Section
Fill in every section completely. The result will be long and wordy — that's expected and normal.

### 5. Refine with AI
Use AI to tighten the draft — not to replace thinking, but to:
- Remove useless repetition
- Fix weak transitions
- Identify where logic is incomplete
- Flag missing background knowledge

The AI is editing and exposing gaps in your reasoning, not writing the article. Much of the actual learning happens at this stage because missing pieces only become obvious after the draft exists.

### 6. Final Self-Review
Read the draft yourself, keep editing, and adjust. AI stays a tool; once you let it take over your judgment, the output becomes less meaningful. Two passes is usually enough to know whether it's ready.

## The /learn Skill (Waza)

The author built **Waza** — an open-source set of Claude Code skills organised around this workflow. The `/learn` skill encapsulates the full research → filter → outline → draft → refine → publish pipeline as a single command.

Waza on GitHub: [github.com/tw93/waza](https://github.com/tw93/waza)

## On Depth

Depth still doesn't come for free in the AI era. AI can help with collecting, translating, cleaning, organising, comparing, and refining. The ceiling is dramatically higher and the process is much faster. But:

> Real depth still depends on your judgment, your patience, your standards, and most of all, your willingness to turn input into output. That part has not changed. Now it matters even more.

## Related

- [[claude-learning-mode]] — Claude's built-in tutoring mode for step-by-step learning
- [[hermes-agent]] — Hermes's LLM-Wiki pattern (Layer 1) implements a similar principle: structured, accumulated knowledge rather than RAG rediscovery
- [[obsidian-chief-of-staff]] — Obsidian + Claude as an environment where research output is automatically structured and linked
- [[extend-claude-sessions]] — managing Claude token limits during intensive research sessions

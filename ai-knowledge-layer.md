---
title: The AI Knowledge Layer — Two-Layer Infrastructure for Agents That Know You
source: ai/raw/AI Knowledge Layer (and why your agents are useless without it).md
---

A two-layer system that makes every AI agent you run smarter: a dynamic Knowledge Base Layer (KBL) that the agent maintains and grows from raw sources, and a static Brand Foundation (BF) that captures your voice, rules, and positioning for agents to read before producing anything. 20-minute setup. Gets better every day. The infrastructure for context engineering — the third phase of RAG evolution.

## Why Agents Fail Without It

Without a knowledge layer, agents have no context about you. Every conversation starts from zero. You re-explain your business, your voice, your goals. Output is generic because input has no memory.

Inspired by Karpathy's observation that he's shifted most of his token spend from code to knowledge management — using LLMs to build personal knowledge bases across research interests, with the compiled approach outperforming RAG at ~100 articles.

## The Two-Layer Architecture

```
+-------------------------------------------------------+
|                    YOUR AGENTS                        |
|  (writer, researcher, strategist, analyst)            |
+---------------------------+--------------------------+
      |  reads from               |  reads from
      v                           v
+------------------+   +------------------+
|  KNOWLEDGE BASE  |   | BRAND FOUNDATION |
|  LAYER (KBL)     |   | (BF)             |
|                  |   |                  |
|  dynamic         |   |  static          |
|  agent-maintained|   |  human-edited    |
|  grows over time |   |  your voice,     |
|  wiki pages,     |   |  rules,          |
|  sources, index  |   |  positioning     |
+--------+---------+   +------------------+
      |
compiles from
      |
+--------+----------+
|     raw/ inbox     |
|  tweets, articles  |
|  bookmarks, PDFs   |
|  notes, ideas      |
+--------------------+
```

### Layer 1: The Knowledge Base Layer (KBL) — Dynamic

The KBL is what this knowledge base itself is: raw sources go into a folder (tweets, articles, bookmarks, PDFs, notes, voice memos); an AI agent reads all of it, classifies each source, builds structured wiki pages with cross-references, and maintains a master index with one-line summaries.

Every question you ask gets filed back as a new page. Every compiled answer becomes searchable context for the next question. The wiki gets richer over time without manual effort.

**What the agent does automatically:**
- Reads new files in `raw/`
- Classifies source type and topic
- Writes a structured wiki page with a summary paragraph
- Adds cross-links to related existing pages
- Updates the master `INDEX.md`

### Layer 2: The Brand Foundation (BF) — Static

The BF is the layer only you edit. Agents read it before producing anything but never rewrite it. It's the anchor that keeps output sounding like you.

**What to include:**
- Voice rules: sentence structure, vocabulary level, things you never say
- Visual style: if agents produce designed output
- Positioning: how you describe what you do and for whom
- Audience definition: who you're talking to, what they care about
- Hard constraints: topics you don't cover, stances you hold, formats you reject

This is not a style guide written for humans — it's a context document written for agents. Be specific and prescriptive: "Never use em-dashes. Write in second person. Keep paragraphs to 3 sentences maximum."

## Why Not RAG?

RAG (Retrieval-Augmented Generation) chunks documents and searches at query time, re-deriving answers from scratch. The knowledge layer compiles once and keeps current.

**Performance comparison:**
- At ~100 articles: compiled approach outperforms RAG for Q&A (Karpathy's finding)
- **71.5× fewer tokens per query** vs. searching raw files (Graphify measurement)

The evolution:
1. One-shot RAG (2020–2023) — retrieve then generate
2. Agentic RAG (2023–2024) — multi-hop retrieval
3. **Context engineering (2025+)** — agent builds its own context from multiple compiled sources

The knowledge layer is infrastructure for the third phase.

## Three Application Contexts

**For content creation:** KBL holds your published articles, ideas, research, and audience feedback. BF captures your editorial voice. Agents produce drafts that sound like you from day one.

**For a company:** KBL holds product documentation, customer conversations, competitive research, and internal wikis. BF captures the company's positioning and tone. Every agent interaction is grounded in real company context.

**For personal use:** KBL holds your notes, bookmarks, conversations, and learning. BF captures your decision-making principles. Your research agent knows your intellectual interests before you explain them.

## Connection to This Knowledge Base

This knowledge base is itself a KBL implementation. The `raw/` folder contains source material. The `wiki/` folder is the compiled output. The `INDEX.md` is the master index. The `/kb-compile` skill is the agent that processes new raw files into wiki pages.

The same architecture scales from a personal knowledge base to a full company intelligence layer.

## Related

- [[obsidian-research-skill-graph]] — a specialized research-focused KBL implementation using 6 analytical lenses
- [[agent-memory-architecture]] — the underlying memory systems that store and retrieve knowledge layer content
- [[hermes-agent]] — Hermes's learning loop is essentially an automated KBL that grows from completed work
- [[extend-claude-sessions]] — NotebookLM as a lightweight external knowledge store

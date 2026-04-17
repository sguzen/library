---
title: Building a Local Research Engine with Claude Code + Obsidian + Skill Graph
source: ai/raw/claude code + obsidian + skill graph. how to build a local research engine.md
---

A folder of 20 interconnected markdown files that transforms Claude from a "genius with amnesia" into a multi-angle research department. One research question goes in; an analysis that would normally take a team two weeks comes out. Four clients tested this and cut research costs by ~60%; one replaced three junior researchers with the system plus one senior editor.

## The Core Idea

Most AI research interactions fail because the AI has zero structure: no methodology, no evaluation criteria, no framework for approaching the topic from different angles. Giving Claude a single prompt produces a Wikipedia-style summary — shallow and quickly outdated.

A **research skill graph** is a folder of `.md` files where each file is one "knowledge node" linked to others with `[[wikilinks]]`. When Claude reads this folder before answering a research question, it doesn't just summarize — it follows your methodology, applies your source evaluation criteria, and analyzes the topic through 6 distinct lenses before synthesizing.

The difference: a prompt gives you a summary. A skill graph gives you a research department.

## The 6 Research Lenses

Instead of asking "research topic X," the system forces the AI to approach the same question 6 times from fundamentally different angles:

| Lens | Focus |
|------|-------|
| **Technical** | What do the numbers actually say? Data only. |
| **Economic** | Follow the money. Who pays, who profits, what incentives drive behavior? |
| **Historical** | What patterns repeat? What's been tried before? What context is everyone forgetting? |
| **Geopolitical** | Zoom out to the global chessboard. Which countries, which power dynamics? |
| **Contrarian** | What if the consensus is wrong? Who benefits from the current narrative? |
| **First Principles** | Forget everything. Rebuild from fundamental truths only. |

Each lens produces findings that often contradict the others. The tension between lenses is where the real insight lives.

*Example: "Why are birth rates collapsing globally?" — Technical lens says "crisis: the math is brutal." Contrarian lens says "Japan has had low fertility for 50 years and hasn't collapsed." Neither is wrong. The truth lives in the tension.*

## Folder Structure

```
/research-skill-graph
├── index.md                    ← command center: who you are, how to execute
├── research-log.md             ← running log of all research questions
├── methodology/
│   ├── research-frameworks.md
│   ├── source-evaluation.md    ← criteria for credibility, bias, recency
│   ├── synthesis-rules.md      ← how to combine conflicting sources
│   └── contradiction-protocol.md
├── lenses/
│   ├── technical.md
│   ├── economic.md
│   ├── historical.md
│   ├── geopolitical.md
│   ├── contrarian.md
│   └── first-principles.md
├── projects/
│   └── [one subfolder per research topic]
├── sources/
│   └── source-template.md
└── knowledge/
    ├── concepts.md
    └── data-points.md
```

20 files. 6 folders. That's the complete system.

## The index.md (Command Center)

The most important file. Every research session starts here. It's not a table of contents — it's a briefing document telling Claude:
- Who you are and what kind of research you do
- Which methodology files to read before starting
- The exact execution protocol (read lenses → run analysis → synthesize)
- Output format requirements

Without a strong `index.md`, Claude reads the files but doesn't know how to use them.

## How to Use It

1. **Build the structure** — create the folder and empty `.md` files
2. **Fill the methodology files** — define your source evaluation criteria and synthesis rules; these are the most important files and take the most thought
3. **Write each lens file** — brief: what this perspective looks for, what questions it asks, what assumptions it challenges
4. **Set up in Obsidian** — the `[[wikilinks]]` format works natively; Claude Code can also read the folder directly
5. **Run research** — point Claude at the `index.md` and ask your question. It reads the methodology, applies all 6 lenses, then synthesizes.

## Why This Beats RAG

RAG re-derives answers at query time by searching chunked documents. The skill graph compiles a methodology once and applies it consistently. The difference: RAG finds relevant content; the skill graph applies a thinking framework. For research questions requiring judgment and synthesis rather than fact retrieval, the skill graph produces qualitatively different output.

## Related

- [[ai-knowledge-layer]] — the broader two-layer system (Knowledge Base Layer + Brand Foundation) that this graph can plug into
- [[extend-claude-sessions]] — managing context across long research sessions
- [[obsidian-chief-of-staff]] — Obsidian as an AI operations hub (same vault, different use case)
- [[llm-council-stress-test]] — complementary approach: multiple models for decision analysis vs. multiple lenses for research

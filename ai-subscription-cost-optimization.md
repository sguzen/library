---
title: AI Subscription Cost Optimisation
source: ai/raw/You're Overpaying for AI by $1,200. Here's the exact math and how to fix It.md
---

A practical breakdown of two separate cost leaks in AI subscriptions — token inefficiency and zero cashback — with concrete tools to fix both. The claim: same subscriptions, 3× more output per dollar.

## The Real Cost

A typical developer setup:

| Subscription | Cost |
|---|---|
| Claude Pro | $20/month |
| ChatGPT Plus | $20/month |
| Gemini Advanced | $20/month |
| Cursor | $20/month |
| Perplexity | $20/month |
| **Total** | **$100/month → $1,200/year** |

Upgrading to Claude Max ($100–$200/month) multiplies costs 10×. Most devs run 3–4 subscriptions: $80–$120/month minimum.

## Leak 1: Token Inefficiency

A typical 30-minute Claude Code session burns ~150,000 tokens — most of it noise: terminal output, passing tests, verbose logs, progress bars, ANSI codes.

### RTK — Rust Token Killer

RTK sits between your terminal and Claude, filtering output before it hits the context window.

```
cargo test:   155 lines → 3 lines    (98% reduction)
git status:   119 chars → 28 chars   (76% reduction)

30-min session: 150,000 → 45,000 tokens (70% reduction)
```

Works with Claude Code, Cursor, Gemini CLI, Copilot, Windsurf, and 5 more tools. Install:

```bash
curl -fsSL https://rtk-ai.app/install.sh | bash
rtk init -g
# restart Claude Code
```

### Caveman Skill

Addresses the output side: Claude's verbose responses (explanations, summaries, clarifying questions, filler) add significant token cost.

```
explain React re-render bug:           1,180 → 159 tokens  (87% savings)
fix auth middleware:                     704 → 121 tokens  (83% savings)
configure PostgreSQL connection pool:  2,347 → 380 tokens  (84% savings)
Average:                                           75% savings
```

```bash
/plugin marketplace add JuliusBrussee/caveman
/plugin install caveman
```

Three modes: `lite` (removes filler), `full` (removes articles/fragments), `ultra` (telegraph style).

**Combined:** input −70%, output −75%. A 150,000-token session becomes ~30,000 tokens.

### Behavioural Fixes (No Tools Required)

**Edit instead of reply:** Every follow-up message stacks on all previous context.

```
5 messages:   7,500 tokens
30 messages:  232,000 tokens  ← message 30 costs 31× more than message 1
```

Hit Edit on the original message and regenerate instead of replying.

**Batch questions:** Three prompts = three full context loads. One prompt with three questions = one load.

**Upload files to Projects once:** A 100-page PDF uploaded 5 times = 375,000 tokens. In Projects = 75,000 once, then free.

## Leak 2: Zero Cashback

The average developer pays $960–$1,440/year on AI subscriptions and gets nothing back.

**Bleap** is a self-custodial finance app (free virtual and physical card) offering 20% cashback on AI subscriptions automatically:

```
Claude Pro $20/month     → $4 back
ChatGPT Plus $20/month   → $4 back
Gemini Advanced $20/month → $4 back
Total: $12/month → $144/year

Claude Max $100/month    → $20 back → $240/year
```

## Full Maths

```
BEFORE:
AI subscriptions:   $100/month
Token efficiency:   0% optimised
Cashback:           $0

AFTER:
AI subscriptions:   $100/month (same)
Token consumption:  −70% with RTK + Caveman
Sessions before limit: 3× longer
Cashback from Bleap: $20/month on $100 in subscriptions
Net monthly cost:   $80 instead of $100
Net annual savings: $240 back + 3× more output per dollar
```

## Related

- [[extend-claude-sessions]] — offloading heavy analysis to NotebookLM to further reduce Claude token consumption
- [[free-ai-via-github-copilot]] — accessing AI models at zero cost via GitHub Copilot + OmniRoute

---
title: Karpathy's CLAUDE.md Rules — Reducing Claude Code Violations by 93%
source: ai/raw/Google engineer automated 80% of his work with Claude Code. here's the exact system he built.md
---

A single `CLAUDE.md` file in your repository root, structured around four principles originally documented by Andrej Karpathy, reduces Claude Code's most common failure modes from ~40% of cases to ~3%. Five minutes to set up. Works at the project level, affecting every Claude Code interaction in that codebase.

## The Problem it Solves

LLMs making code changes have predictable failure modes:
- Over-engineering simple tasks
- Adding dependencies nobody asked for
- Ignoring existing patterns in favour of "better" approaches
- Touching code that wasn't part of the request
- Making assumptions instead of asking for clarification

These aren't random errors — they're systematic biases. If mistakes are predictable, they can be prevented with the right instructions.

## The Four Principles

```
Think Before Coding    → stops wrong assumptions and missed tradeoffs
Simplicity First       → stops over-engineering and bloated abstractions  
Surgical Changes       → stops touching code nobody asked to touch
Goal-Driven Execution  → tests first, verified success criteria
```

**Think Before Coding:** Before writing any code, state your understanding of the task, list any tradeoffs or ambiguities, and get confirmation. Never start coding from an assumption you could have checked.

**Simplicity First:** The simplest solution that works is the right solution. Avoid new abstractions unless they're clearly necessary. Don't introduce frameworks, patterns, or dependencies beyond what the task requires. If it can be done with existing code, use existing code.

**Surgical Changes:** Only touch the code that needs to change. Don't refactor adjacent code because you noticed something. Don't "improve" things that weren't part of the request. Scope creep in AI code generation is a real problem.

**Goal-Driven Execution:** Define what success looks like before writing code. Write tests or acceptance criteria first. When done, verify against those criteria — don't just report that you're finished.

## Auto-Generating Your CLAUDE.md

This command reads your codebase and creates a CLAUDE.md adapted to your actual architecture:

```bash
claude -p "Read the entire project and create a CLAUDE.md based on:
Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution.
Adapt to the real architecture you see." --allowedTools Bash,Write,Read
```

The resulting file will incorporate your actual tech stack, naming conventions, and architectural patterns rather than generic rules.

## The Everything Claude Code Repo

Alongside a CLAUDE.md, the `everything-claude-code` repo (`github.com/affaan-m/everything-claude-code`, 153K+ stars) provides a complete AI operating system layer:

- **30+ specialized agents:** `planner.md`, `architect.md`, `tdd-guide.md`, `code-reviewer.md`, `security-reviewer.md`, `loop-operator.md`
- **180+ skills** covering TDD, security, research, content
- **AgentShield:** 1,282 security tests built into the config

**Install:** `/plugin marketplace add affaan-m/everything-claude-code`

**Warning:** Don't load everything at once. 27 agents and 64 skills active simultaneously will drain context limits before you type your first prompt. Take only what your current project actually needs.

## Real-World Impact

A Google engineer with 11 years of experience applied these principles and automated 80% of his work, dropping from 8-hour days to 2–3 productive hours. The leverage comes from two things together: behavioral constraints (CLAUDE.md) + specialized agent ecosystem (everything-claude-code).

**Before CLAUDE.md:** Claude breaks conventions in ~40% of cases  
**After Karpathy CLAUDE.md:** violations drop to ~3%

## Related

- [[claude-code-github-repos]] — the broader collection of repos that extend Claude Code's capabilities
- [[ai-engineer-projects]] — production-grade projects where these rules prevent quality degradation
- [[extend-claude-sessions]] — managing long-running sessions where rule adherence matters most

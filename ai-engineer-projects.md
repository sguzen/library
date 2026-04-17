---
title: Five Production-Grade Projects to Prove AI Engineering Skills
source: ai/raw/the 2026 ai engineer roadmap.md
---

The gap between a prompt engineer and a systems architect is roughly $150K in 2026. These five projects are ranked by complexity and designed to prove you can handle production-level AI challenges — not just call an API. Each project forces you to solve a real problem the market cares about.

## The Core Argument

The market is flooded with thin wrappers over GPT. They're not businesses — they're features waiting to be replaced by the next model update. To be indispensable, you need to understand orchestration, memory, and local inference. These projects force those skills.

---

## Project 1: AI-Powered Mobile App with SLM — Beginner

**What it proves:** Edge AI + resource optimization

**The challenge:** Build an offline-first mobile app using small language models. Zero API costs. Complete privacy. Teaches optimization for restricted hardware.

**Key architectural decisions to solve:**
- **Model management:** lazy-load on demand, unload inactive models under memory pressure, preload frequently used models during idle
- **Context window:** sliding window with semantic chunking; use embedding similarity to determine what stays vs. gets archived
- **Quantization strategy:** dynamic based on device capabilities (4-bit for pre-2020 hardware, 8-bit for newer)
- **Battery optimization:** batch inference to reduce wake cycles; throttle during low battery; defer non-critical processing until charging
- **Offline-first sync:** local encrypted storage; sync only on connection with user permission; local-first conflict resolution

**Why it matters:** Proves you understand constraints beyond "call an API." Quantization and memory pressure are production realities.

---

## Project 2: Self-Improving Coding Agent — Intermediate

**What it proves:** Agentic loops + production debugging

**The challenge:** An agent that writes code, runs tests, and learns from failures. Doesn't stop until the code is functional.

**Key architectural decisions:**
- **Execution loop:** Plan → Execute → Test → Reflect cycle with max iteration limit and circuit breaker to stop infinite loops
- **Sandboxing:** isolated execution per task; CPU/memory/time limits; filesystem restricted to project directory
- **Memory hierarchy:** short-term (last 5 iterations) + long-term (indexed successful patterns by problem type) + failure memory (error signatures + solutions)
- **Reflection:** after each failure, extract error pattern, compare against past failures via vector similarity, generate hypothesis and fix
- **Learning from mistakes:** store failed attempts with full context; on similar future tasks, retrieve relevant failures before attempting

**Why it matters:** Introduces real agentic loops. Shows you understand production debugging and iterative refinement, not just one-shot prompting.

---

## Project 3: AI-Assisted Video Editor — Advanced

**What it proves:** Multimodal AI + complex tool integration

**The challenge:** Fork an open-source editor (e.g., Shotcut) and build an AI agent that understands editing intent. "Make this cinematic" → agent handles cuts, transitions, colour grading.

**Key architectural decisions:**
- **Multimodal understanding:** vision model per frame (composition, lighting, subject) + audio model (dialogue, music, ambient) combined to understand narrative flow
- **Intent translation:** "cinematic" → slow pacing (80% speed) + desaturated colours + shallow focus simulation + dramatic music cues
- **Scene detection:** frame-difference analysis for hard cuts; embedding similarity for soft boundaries; story beat detection from combined audio/visual
- **Incremental preview:** don't re-render entire video after each change; preview affected sections only; cache unchanged segments
- **Undo/redo with reasoning:** every edit stores what changed AND why; user can ask "why did you cut here?" and get explanation based on detected story beat

**Why it matters:** Sets you apart from 99% of chatbot builders. Multimodal AI + real tool integration are the frontier.

---

## Project 4: Personal Life OS Agent — Expert

**What it proves:** Deep context + privacy-first architecture

**The challenge:** An agent that manages calendar, finances, and health. Plans months ahead and detects burnout by analyzing sleep patterns and meeting density.

**Key architectural decisions:**
- Long-horizon planning across multiple data domains
- Privacy-first: all processing local or encrypted; user controls data boundaries
- Cross-domain correlation: health data + calendar density + financial stress = burnout prediction
- Memory architecture that learns preferences without explicit instruction
- Graceful degradation when data is missing

**Why it matters:** The hardest category is agents that know your actual life. Deep context + privacy constraints at scale is a real engineering problem.

---

## Project 5: Autonomous Business Intelligence Agent — Expert

**What it proves:** Production orchestration + multi-tool integration

**The challenge:** An agent that monitors business metrics, identifies anomalies, traces root causes, and delivers executive-ready reports — autonomously, on a schedule.

**Key architectural decisions:**
- Multi-tool orchestration (database queries, API calls, web search, report generation)
- Anomaly detection that distinguishes signal from noise
- Causal reasoning to trace anomalies to root causes rather than just flagging them
- Report generation calibrated to audience (technical vs. executive)
- Failure recovery: if one data source fails, degrade gracefully rather than producing a broken report

---

## The Progression

| Project | Main Skill Unlocked |
|---------|-------------------|
| Mobile SLM | Edge AI, resource constraints |
| Self-improving agent | Agentic loops, persistent memory |
| Video editor | Multimodal AI, complex tool integration |
| Personal OS | Deep context, privacy architecture |
| BI agent | Production orchestration, multi-tool coordination |

Build them in order. Each one builds on skills from the last. By Project 3 you're differentiated from 99% of AI developers. By Project 5 you're at systems architect level.

## Related

- [[ai-engineer-roadmap]] — the learning path (Python → APIs → RAG → agents) that prepares you for these projects
- [[agent-memory-architecture]] — the memory patterns required for Projects 2 and 4
- [[claude-code-karpathy-rules]] — CLAUDE.md principles that improve code quality throughout the build process

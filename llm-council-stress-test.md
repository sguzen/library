---
title: LLM Council and the Stress Test Skill — Multi-Model Decision Analysis
source: ai/raw/Stop using LLM council with Claude. Do this instead.md
---

The LLM Council pattern routes a decision through multiple AI perspectives for peer review and synthesis. The single-model version (Claude playing multiple roles) suffers from documented self-preference bias; the research-backed version combines real multi-model diversity, customizable analytical lenses, and verbalized sampling for 2–3× more diverse insights.

## The Evolution of the Pattern

**Karpathy's original (Nov 2025):** Send the same question to GPT, Claude, Gemini, and Grok simultaneously. Each responds independently, then reviews the others anonymously. A chairman model synthesizes. Result: 17K GitHub stars, called "a blueprint for enterprise AI orchestration" by VentureBeat.

**Ole Lehmann's single-model version:** Rebuilt to run entirely inside Claude using five thinking-style personas (Contrarian, First Principles Thinker, Expansionist, Outsider, Executor). Each responds → anonymous peer review → chairman synthesizes. Gained: customizable analytical lenses. Lost: real model diversity.

**The three-layer upgrade:**

1. **Between-model diversity** — use Model Council (Perplexity Computer) routing to GPT-5.4, Claude Opus 4.6, and Gemini 3.1 Pro simultaneously
2. **Within-model diversity** — verbalized sampling (Stanford, 2025) unlocks each model's suppressed insights
3. **Analytical diversity** — domain-specific lenses you define per decision type

## Why Single-Model Councils Have a Ceiling

Self-preference bias is documented in three papers:

- **NeurIPS 2024** ([arxiv.org/abs/2404.13076](https://arxiv.org/abs/2404.13076)): LLMs score their own outputs higher than identical-quality outputs from other models. Linear correlation: better self-recognition → stronger bias.
- **ICLR 2025** ([arxiv.org/abs/2410.21819](https://arxiv.org/abs/2410.21819)): Models favor outputs stylistically familiar to them (lower perplexity = higher scores).
- **arXiv 2026** ([arxiv.org/abs/2604.06996](https://arxiv.org/abs/2604.06996)): Bias persists even with objective rubrics. Models were up to 50% more likely to incorrectly mark their own outputs as correct.

The critical point: the bias is in the **evaluation step**, not the generation step. Claude playing five personas produces different outputs, but Claude reviewing Claude's five outputs can't meaningfully differentiate because they all "feel" equally familiar.

## Verbalized Sampling

Stanford research ([arxiv.org/abs/2510.01171](https://arxiv.org/abs/2510.01171)) addresses mode collapse after alignment training. RLHF/DPO trains models to converge on the most typical ("safest") responses. The non-obvious, high-value insights get suppressed.

**The technique:** Ask the model to generate multiple candidate responses and assign probability scores to each. Then explicitly instruct it to select responses with probability < 0.10 — the tail of the distribution.

Result: **1.6–2.1× diversity improvement** in creative and analytical tasks while maintaining quality. Training-free. Stacks on top of temperature settings.

When combined with multi-model routing, each model explores a different distribution's tails — the diversity compounds.

## The Stress Test Skill

Built for Perplexity Computer with Model Council active. Paste this as a skill named "Stress Test":

```
# Stress Test

You are a structured decision analysis system. When the user says "stress test this", run the full protocol.

## Phase 1: Diverse perspective generation (with Verbalized Sampling)

For each analytical perspective, generate 3 candidate responses with estimated probability scores. Select the response with the LOWEST probability (the tail of the distribution) as the primary perspective.

Use different models if available (Model Council). If single model, make perspectives maximally different: one quantitative, one strategic, one risk-focused, one unconventional.

Per perspective:
- state recommendation clearly (not "it depends")
- provide single strongest evidence
- flag what this perspective is NOT considering
- prioritize the non-obvious angle over the expected one

## Phase 2: Customizable analysis lenses

Default lenses (replace with your own):

Risk scan: most likely failure mode? most expensive failure mode? same or different?
Opportunity map: adjacent upside user isn't seeing? what if this works 3x better?
Execution audit: fastest path to test with real data? actual bottleneck?
Assumption check: what is user assuming without stating? what changes if wrong?

## Phase 3: Decision brief

THE QUESTION: [restate — reframe if wrong question]
WHERE PERSPECTIVES AGREE: [2-3 convergence points]
WHERE PERSPECTIVES DISAGREE: [tensions with both sides' reasoning]
RISK: [failure mode, one sentence]
BLIND SPOT: [unquestioned assumption, one sentence]
OPPORTUNITY: [unseen upside, one sentence]
VERDICT: [clear recommendation, 2-3 sentences — not "it depends"]
TEST IT THIS WEEK: [specific action + metric + threshold]

Under 500 words. Verdict must be real.
```

**Customize Phase 2 lenses per use case:**
- Investor: Bull Case / Bear Case / Macro Factors / Portfolio Fit
- Founder: Customer Demand / Technical Feasibility / Market Timing / Competitive Edge
- Creator: Audience Fit / Distribution Strategy / Monetization Path / Longevity Test

## When to Use Which

| Scenario | Tool |
|----------|------|
| Quick brainstorm, low stakes | Ole's single-model council (free, fast) |
| High-stakes decisions | Model Council + Stress Test Skill + verbalized sampling |

Requirements for the full stack: Perplexity Computer ($200/month Max or $20/month Pro with Model Council access).

## Related

- [[ai-learning-workflow]] — systematic workflow for research and synthesis, complementary to structured decision-making
- [[hermes-agent]] — another approach to multi-step AI reasoning with a persistent agent loop

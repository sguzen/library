---
title: Building a Polymarket BTC Trading Engine with Claude
source: ai/raw/Building a Polymarket BTC Trading Engine with Claude- Full Guide.md
---

A detailed account of building an automated BTC prediction market trading engine on Polymarket using Claude Code for architecture planning, covering Polymarket's internals, engine design, simulation, and strategy development.

## Polymarket's Technical Architecture

Polymarket runs on **Polygon** (Ethereum L2, near-zero transaction costs). Each binary market uses the **Gnosis Conditional Token Framework (CTF)**:

- For every $1 USDC locked, two ERC-1155 tokens are minted (one per outcome, e.g. UP/DOWN)
- A complete set always redeems for exactly $1 USDC — arbitrage keeps prices rational
- **5-minute BTC markets** resolve via Chainlink price feeds (automatic, trustless, no human involvement)
- Event-based markets use UMA's Optimistic Oracle (propose → challenge window → decentralised vote if disputed)

**Trading layer:** Polymarket uses a hybrid **Central Limit Order Book (CLOB)**, not an AMM. Orders go to an off-chain matching engine; matched pairs are settled on-chain via EIP-712 signed transactions to the CTF Exchange contract. All orders are limit orders — there are no market orders. Shares are not immediately sellable after purchase because on-chain settlement must complete first (MATCHED → MINED → CONFIRMED).

## Engine Design

### v1: "Late-Entry" (Event-Driven)
- Subscribed to Polymarket's order book WebSocket for real-time updates
- Used indicators (RSI, ATR, cross-source price divergence from Binance/Coinbase/Chainlink) to detect whale dumps/pumps and trigger buy signals
- Strategy: one buy → hold to market resolution
- Problem: 5% of trades caused disproportionate losses; no intermediate sell capability

### v2: "Early-Bird" (Lifecycle-Based, Designed with Claude)

Architecture designed in collaboration with Claude Code (Opus 4.6), using the [Plannotator](https://plannotator.ai/) plugin for iterative planning.

**Core design:**
- Always starts in a future market slot (minimum one slot ahead of current) — never enters a live market mid-run
- Each market is a **lifecycle**: `start → run → end`
- One strategy per market lifecycle; strategy is instantiated at `start`, executes during `run`, monitored until completion, then `end` computes PnL
- Engine provides a strategy API; strategies are simply functions that call `buy()` and `sell()` through that API

**Key additions over v1:**
- Buy-and-sell capability (not just hold-to-resolution)
- Simulation mode with a paper wallet that accurately mirrors real-world conditions: latency, partial fills, unexpected cancellations, on-chain confirmation delays
- Chart visualisation tool: takes log files and renders interactive charts per market window for post-hoc strategy analysis

## Strategy Notes

The author found edge in specific time-of-day patterns — certain order book signatures that only appear during particular windows. The principle: **don't try to win every round; optimise exit signals to minimise losses when wrong**.

AI won't write a strategy for you directly. It needs to be trained on specific metrics (order book movements, gap behaviour, price divergence). Testing strategies using context from those metrics is a future research direction.

The engine is open-source: [github.com/KaustubhPatange/polymarket-trade-engine](https://github.com/KaustubhPatange/polymarket-trade-engine)

## Claude's Role

Claude Code (Opus 4.6) was used for:
1. **Architecture planning** — iterative back-and-forth to design the lifecycle-based engine structure
2. **Skeleton generation** — initial code scaffold from the approved architecture
3. **Simulation design** — structure for paper wallet and test harness
4. **Logging and visualisation** — suggested the chart visualisation system for debugging strategy failures

## AI-Trader: Alternative LLM Trading Agent Approach

A second approach to AI-powered Polymarket trading uses the open-source **AI-Trader** repo (`github.com/HKUDS/AI-Trader`) from the University of Hong Kong — the same team behind LightRAG. This approach connects an LLM directly to market data and news feeds and generates trading signals.

**How it works:**
> Market data + news → LLM analysis → trading signal → order execution

The agent reads news in real time, analyzes sentiment, cross-checks with price dynamics, and outputs a buy/sell/hold signal with reasoning.

**Benchmark results from the repo:**
- vs. buy-and-hold: +31% better results
- vs. random strategy: +47% better results
- Sharpe ratio: 1.8 (strong risk-adjusted performance)
- Winning signal rate: 64%

**Polymarket Python client:** The official `py-clob-client` (`github.com/Polymarket/py-clob-client`) gives full programmatic access to order books, positions, market data, and order placement via three commands.

This contrasts with the custom BTC engine above: AI-Trader is a general-purpose LLM signal generator; the BTC engine is a lifecycle-based system purpose-built for 5-minute binary markets.

See also [[claude-code-github-repos]] — AI-Trader appears in the broader list of repos that extend Claude's agentic capabilities.

## Related

- [[hermes-agent]] — another use case of AI agents managing autonomous systems, including live trading
- [[claude-code-github-repos]] — broader collection of agentic GitHub repos including AI-Trader

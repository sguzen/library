---
title: The Four Claude Products — Chat, Code, Cowork, Managed Agents
source: ai/raw/Claude The Ultimate Guide (April 2026).md
---

"Claude" is four distinct products with four different jobs. Using the wrong one either overcomplicates simple tasks or leaves major productivity on the table. As of April 2026, all four are generally available to paid subscribers.

## Claude Chat — The Starting Point

**What it is:** The conversational interface at claude.ai. General Q&A, writing, editing, brainstorming, document analysis (PDFs, images, spreadsheets), and research. Projects allow saving reusable context and instructions.

**Critical limitation:** Claude Chat cannot take action in other tools. It can't send an email, update a spreadsheet, or commit code. You are the copy-paste middleman between Claude and every other app.

**Who:** Anyone who needs a thinking partner — writers, researchers, students, business owners.

**Where:** Web, desktop app, mobile. No setup.

**Pricing:** Free tier + Pro at $20/month.

---

## Claude Code — The Developer's Workhorse

**What it is:** Claude with hands, specifically for software. Reads your entire codebase, edits files directly, runs terminal commands, handles git workflows (commits, PRs, branches), spawns Agent Teams for complex multi-step tasks, and integrates with GitHub, GitLab, and Slack via MCP connectors.

**Critical limitation:** Purpose-built for software development. Won't organize files, draft emails, or manage calendars. Not beginner-friendly — if you've never opened a terminal, the learning curve is real.

**Who:** Developers of any language or framework.

**Where:** Terminal, VS Code, Cursor IDEs, browser-based environments.

**Pricing:** Same tiers as Chat. Pro $20/month, up to Ultra $200/month.

---

## Claude Cowork — The Non-Developer Unlock

**What it is:** Claude that takes actions directly on your computer and inside your apps. As of April 2026, generally available on macOS and Windows for all paid subscribers.

**Capabilities:**
- Connects to Google Drive, Gmail, Excel, PowerPoint, Slack, Zoom, and more
- Organizes files, renames documents, deletes duplicates
- Generates reports, spreadsheets, and presentations
- Runs batch operations (format conversions, image compression, naming standardization)
- Automates browser tasks via Chrome extension
- Uses customizable plugins for specific workflows

**Critical limitation:** Requires the desktop app running during tasks. Uses more tokens than regular chat. Learning curve around understanding what it can/can't do across your specific tool stack.

**Who:** Knowledge workers, solo operators, small business owners, agency teams — anyone drowning in repetitive computer tasks who doesn't write code.

**Where:** Claude Desktop app (macOS and Windows).

**Pricing:** Any paid plan ($20/month+).

---

## Claude Managed Agents — The Platform Play

**What it is:** Hosted infrastructure for building and deploying autonomous AI agents at scale. Launched public beta April 2026. This is not a consumer product — it's a backend service you deploy.

**Capabilities:**
- Runs Claude as a long-running autonomous agent in cloud infrastructure
- Pre-built agent harness (the loop that calls Claude and routes tool calls)
- Secure sandbox with bash, file operations, web search, and code execution
- MCP server support for external service connections
- Session persistence — agents pick up where they left off after interruption
- Multi-agent coordination for complex workflows
- Built-in prompt caching, context compaction, and performance optimizations

**Architecture:** Three decoupled components:
1. **The brain** (Claude + harness) — reasoning and next-step decisions
2. **The hands** (sandboxes + tools) — actual execution
3. **The session** (event log) — durable record; any component can fail and recover independently

OAuth tokens and API keys live in a secure vault outside the sandbox — credentials never touch the execution environment.

**Who:** Developers and businesses embedding Claude into their own products. Companies like Notion, Asana, and Sentry use it.

**Where:** Cloud via Claude Platform API. No chat interface.

**Pricing:** Usage-based (tokens consumed). Available to all API accounts.

---

## How to Choose

| Situation | Product |
|-----------|---------|
| Thinking, writing, research | Claude Chat |
| Writing and shipping code | Claude Code |
| Repetitive tasks across business apps, no coding | Claude Cowork |
| Building a product that needs Claude running autonomously | Managed Agents |

**The natural progression:** Chat → Cowork (or Code for developers) → Managed Agents when scaling beyond personal use.

The four products are layers of the same platform, not competitors. The right question is "which Claude fits this specific task?" not "which Claude is best?"

## Related

- [[extend-claude-sessions]] — extending Chat and Code sessions via NotebookLM
- [[claude-code-github-repos]] — repos that enhance Claude Code's agentic capabilities
- [[obsidian-chief-of-staff]] — Cowork-adjacent: using Claude Code to build a Chief of Staff in Obsidian

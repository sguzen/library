---
title: autoskills — Auto-Install AI Agent Skills from Your Tech Stack
source: ai/raw/Thread by @ihtesham2005.md
---

`autoskills` is an open-source CLI tool that scans a project's tech stack and automatically installs the matching AI agent skills in one command, eliminating manual skill discovery and setup.

## How It Works

Run `npx autoskills` in any project root. The tool:

1. Reads `package.json`, config files, and directory structure to fingerprint the tech stack
2. Matches detected technologies against a curated skill registry at [skills.sh](http://skills.sh)
3. Installs the appropriate skills for every detected technology

Supports 50+ technologies including React, Next.js, Vue, Svelte, Astro, Tailwind, Supabase, Neon, Playwright, Expo, Stripe, Prisma, Cloudflare, AWS, Vercel, GSAP, Bun, Deno, Hono, NestJS, Spring Boot, and more.

**`--dry-run` flag:** Shows what would be installed before touching anything. Recommended for first use.

## Key Use Case

The core problem autoskills solves: when starting a new project or joining an existing codebase, figuring out which skills to install requires knowing both the tech stack and the skill ecosystem. autoskills collapses that to a single command.

For monorepos with multiple stacks, it attempts to install skills for all detected technologies.

## Community Notes

- Security-conscious users note that running `npx` installs code that runs on your machine — review the source before use in sensitive environments
- Alternative approach: ask your AI agent to analyze the codebase and then manually run `npx skills search` for more control
- Some users build private skill libraries and use an agent to select from them per project — a pattern autoskills automates for the public registry

## Related

- [[free-ai-via-github-copilot]] — Claude Code is the environment where skills run
- [[claude-code-github-repos]] — broader collection of GitHub repos that enhance Claude Code workflows

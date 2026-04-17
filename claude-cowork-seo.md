---
title: Claude Cowork as Chief of SEO — Local SEO Audit System
source: ai/raw/My Chief of SEO, Claude Cowork.md
---

A 20-part prompt system built inside Claude Cowork that audits a business's entire Google presence, maps competitor gaps, and produces a prioritized execution plan — collapsing what used to take half a day per client into minutes.

## The System Architecture

The key that separates a generic AI interaction from a real system: **pre-loaded business context**. Before running any prompt, Claude is given everything it needs to produce specific output rather than generic recommendations:

- A folder with business name, address, phone number, website, GBP URL, service areas, and target keywords — loaded once, never repeated
- A file for every competitor with their Google Business Profile URLs
- The current GBP details uploaded (categories, attributes, photos, services)
- A library of task-specific prompts, each pre-loaded with business context

Without this setup, Claude produces generic output. With it, every prompt feels purpose-built for the specific business.

## What the Audit Covers

The 20-part prompt stack surfaces and addresses:

- **Competitor category analysis:** maps competitor GBP categories against map pack rankings, highlighting every category the business is missing
- **Citation audit:** finds citations with wrong phone numbers, inconsistent NAP data, or missing directories
- **Review velocity analysis:** benchmarks review frequency against top map pack competitors
- **GBP attribute gaps:** identifies attributes competitors have enabled that the business hasn't
- **Photo and service completeness:** compares the business's GBP content against top-ranked competitors

Output is a prioritized spreadsheet with specific actions sorted by impact — not vague recommendations.

## Example Prompt Workflow

The workflow runs as a sequence where each prompt builds on the previous:

1. Load business context (one-time setup, never repeated)
2. Pull competitor GBP data and map against map pack rankings
3. Run category gap analysis: which categories do map pack leaders use that this business doesn't?
4. Audit citation consistency across directories
5. Benchmark review velocity: how many reviews/month do top competitors gain?
6. Generate ranked action plan sorted by estimated ranking impact

## Why Cowork vs. Regular Claude Chat

Claude Chat requires copy-pasting results between the AI and the tools that will act on them. Cowork can pull data from Google Drive, write directly to spreadsheets, and run the full analysis without the user acting as a middleman. The analysis that used to require switching between 5+ browser tabs and manual spreadsheet updates runs in a single session.

## Business Application

This system is primarily useful for:

- Local SEO agencies running audits for multiple clients
- Solo operators managing their own Google Business Profile
- Consultants who want to productize a local SEO audit as a service (see [[ai-workflow-setup-service]] for the service-productization pattern)

The analyst who built this runs it at a marketing agency ([alventramarketing.com](https://alventramarketing.com/)) as part of a paid service.

## Related

- [[claude-products-guide]] — full breakdown of Claude Cowork's capabilities
- [[obsidian-chief-of-staff]] — another "Chief of X" system built with Claude, focused on business operations
- [[ai-workflow-setup-service]] — productizing AI workflow setups as a $500 service

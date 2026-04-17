---
title: Claude + Obsidian as an AI Chief of Staff
source: ai/raw/Thread by @RoundtableSpace.md
---

A pattern for using a single Claude Code prompt to build an Obsidian-based "Chief of Staff" — a structured vault with automation rules that turns Claude into a persistent, organised business assistant.

## The Core Idea

Most people who set up Claude + Obsidian copy the vault folder structure and stop there. The folder structure alone is just a chatbot with folders. The part that actually matters is the **automation rules**: instructions in `CLAUDE.md` that govern how Claude classifies, files, and cross-links every piece of raw information it encounters.

The key principle: *never leave raw information unstructured*. The agent's job is to immediately process any input into the right place in the vault, with the right tags and cross-references.

## What the Prompt Does

A single "Chief of Staff" prompt fed to Claude Code generates:
- A full Obsidian vault folder structure (meetings, projects, tasks, reference, daily notes, etc.)
- A `CLAUDE.md` with operating rules: where things go, required metadata, linking conventions, formatting standards
- Skills for recurring operations: `/daily`, `/research`, `/wrap-up`

## Key Configuration Points in CLAUDE.md

- **Folder structure** — explicit paths for research notes, meeting notes, task logs, and output files
- **Metadata requirements** — dates, tags, source links on every new note
- **Linking rules** — wrap significant concepts in `[[double brackets]]` to power Obsidian's graph view
- **Formatting standards** — headings, callout types, table conventions

## Limitations to Know

- This setup consumes significant tokens, especially on initial vault setup or large batch processing
- The quality of the Chief of Staff depends entirely on how well the `CLAUDE.md` rules are tuned — the prompt is a starting point, not a finished product
- Works best when Claude Code is run from the vault root directory so it has full read/write access

## Related

- [[extend-claude-sessions]] — Workflow D covers this pattern in depth, including integration with NotebookLM for zero-token research within the vault
- [[ai-learning-workflow]] — a structured approach to managing research input and output, compatible with an Obsidian vault setup

---
title: Claude Learning Mode
source: ai/raw/Thread by @FutureStacked.md
---

Claude has a built-in "Learning Mode" accessible from the web and app interfaces that turns Claude into an interactive, step-by-step personal tutor rather than a question-answering tool.

## What It Does

Instead of returning a direct answer, Learning Mode walks through concepts progressively — checking for understanding before moving on, much like a patient tutor sitting beside you. It adapts pace to the learner: slows down when you struggle, speeds up when you're breezing through.

**Features:**
- Structured lessons broken into digestible steps
- Multimedia support (images, videos)
- Interactive quizzes to test understanding
- Adaptive pacing based on responses

## How to Access It

Open Claude on the web or app, start a conversation, and select "Learning Mode" from the interface options. Then ask a question or upload a document.

## Practical Notes

The "Learning Mode" framing is essentially a system-level prompt that enforces a Socratic teaching style. The same effect can be replicated with a manual prompt like:

> "Act as a tutor. Ask one question at a time. Don't give the final answer until I try. Give hints and quick quizzes. Adjust difficulty."

The distinction matters for token usage: Learning Mode sessions generate significantly more back-and-forth, which burns context faster. Users on limited plans should be aware of this.

## Related

- [[ai-learning-workflow]] — a deeper, systematic approach to AI-assisted learning that produces publishable output
- [[extend-claude-sessions]] — techniques for extending Claude session limits when deep learning sessions drain tokens quickly

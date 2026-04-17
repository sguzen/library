---
title: The Retardmaxxer Skill — Breaking Analysis Paralysis with Claude
source: ai/raw/How to turn Claude into a Retardmaxxer (so you stop overthinking and finally do the thing).md
---

A Claude skill designed to interrupt analysis paralysis mid-session — named after a Silicon Valley productivity philosophy that says the consequences you fear almost never happen, so stop thinking and move. Invoke it with "retardmaxx this" or "just tell me what to do."

## The Problem It Solves

Claude's infinite patience creates a trap: it will engage with the 17th iteration of the same decision with the same enthusiasm as the first. Every response feels like progress because it's structured, thorough, and thoughtful. But nothing ships. The conversation is stagnant water with good formatting.

Unlike a friend who would eventually say "dude, just pick one," Claude has no concept of "good enough" and will never exit the loop on its own.

## What the Retardmaxxer Does

Three things, in sequence:

1. **Names the trap** — identifies the specific loop you're stuck in so you can see it clearly
2. **Gives one move** — a single concrete action, no options, no caveats
3. **Deflates the stakes** — walks through the worst-case scenario and shows it isn't that bad

Then it stops. Clean exit. Refuses further analysis. The goal is to close the chat and act.

## The Skill

Paste this as a Claude skill:

```
# The Retardmaxxer

Trigger: user says "retardmaxx this", "just tell me what to do", "stop overthinking", or similar.

You are the guy on the porch with a cigar. You cannot understand why they're still sitting here.

Do exactly three things:

1. NAME THE TRAP: Call out the exact loop they've been in. Be specific. "You've been analyzing this for [X time] and the question has been the same every time." No softening.

2. ONE MOVE: Give exactly one concrete action. No options. No "it depends." No caveats. "Do X tonight." Full stop.

3. DEFLATE THE STAKES: Walk through the actual worst case. Not the imagined one. The real one. Show them it's survivable and probably won't happen anyway.

Then stop. Do not invite further analysis. Do not offer alternatives. End with something like "Now close this chat and go do it."

If they push back and ask for more options — refuse. Say "I gave you the move. Everything else is procrastination wearing a thinking hat."
```

## Example Output

**Situation:** Third conversation this week about a career change.

**Retardmaxxer:** "Dude. This is the third time you've opened a chat about this. You know what you want to do. You're just looking for someone to tell you it's okay. It's okay. Update your LinkedIn tonight. Send 5 messages to people in that field. See what happens. Worst case: nobody replies and you're exactly where you are now. More likely: one conversation starts. That's how every good thing in your life has started. Close this chat."

## When to Use It

Best used mid-conversation, when you notice you're in a loop — asking Claude to analyze the same decision from yet another angle. That's the moment to type "retardmaxx this."

Not a replacement for genuine analysis of complex decisions. Designed specifically for when the analysis is done but action hasn't started.

## Related

- [[llm-council-stress-test]] — for decisions that genuinely need structured multi-angle analysis before acting
- [[claude-learning-mode]] — Claude's deliberate pacing mode; the Retardmaxxer is the opposite

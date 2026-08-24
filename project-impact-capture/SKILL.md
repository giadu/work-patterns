---
name: project-impact-capture
description: Turn a completed feature, project, issue, or delivery slice into reusable evidence before the details fade. Use when a project just shipped, a meaningful milestone closed, or you need interview stories, resume bullets, self-review notes, promotion evidence, or public-safe summaries grounded in real work rather than vague memory.
---

# Project Impact Capture

## Overview

Use this skill right after a meaningful piece of work ships, stabilizes, or teaches you something important. The goal is to capture decisions, tradeoffs, impact, and your actual contribution while the details are still fresh, then convert that into reusable career evidence.

## Core rule

Do not write a vanity summary. Capture what was actually hard, what you actually decided, what shipped, and what evidence still needs to be collected.

## When to use it

Use this skill when:
- a feature or project just shipped
- a difficult issue or migration is now stable enough to reflect on
- you finished a meaningful slice and want to preserve the story before memory degrades
- you need grounded input for interviews, CV bullets, promotion/self-review, compensation discussions, or a public-safe post

Do not use it for:
- unfinished work with no stable outcome yet
- pure brainstorming before implementation
- rewriting company strategy documents

## Workflow

### 1. Start from raw facts

First collect the concrete inputs that still exist:
- issue, ticket, PR, or spec links
- your notes or chat summaries
- shipped behavior
- screenshots, metrics, logs, or user feedback if available

If the available evidence is thin, still capture the story now and explicitly mark what evidence is missing.

### 2. Separate the real problem from the implementation

Write down:
- what problem existed before the work
- who felt that problem
- why it mattered to users, operations, revenue, or team leverage

Avoid starting with implementation details. Start with why the work mattered.

### 3. Isolate your actual contribution

Be precise about:
- what you owned directly
- what decisions you made
- where you influenced direction without being the sole implementer
- what depended on other people or teams

Do not inflate ownership. Clear partial ownership is stronger than vague full ownership.

### 4. Capture what was genuinely difficult

Name the real hard part. Usually it is not "I wrote the code."

Examples:
- unclear problem framing
- weak domain assumptions
- AI output quality
- rollout and trust concerns
- data consistency
- operational failure handling
- scope control under ambiguity
- getting something shippable without overengineering

### 5. Record decisions and tradeoffs

Capture:
- what you chose to include now
- what you explicitly postponed
- which alternatives you rejected
- why your chosen shape was the right one for that moment

This is often the most valuable part for interviews and seniority evidence.

### 6. Capture impact and missing proof

Record impact in whatever form is honest and available:
- user impact
- business impact
- team leverage
- operational improvement
- risk reduction
- speed/reliability gains

If metrics are unknown, capture qualitative evidence and write down what you should still gather later.

### 7. Produce reusable output variants

Convert the same work into multiple forms:
- interview story
- resume bullet drafts
- self-review / promotion note
- public-safe summary
- substack or portfolio angle if appropriate

Use `references/capture-template.md` as the main output structure.
Use `references/evidence-prompts.md` if the story feels thin or fuzzy.
Use `references/output-variants.md` when converting the same project into different surfaces.

## Output rules

- Be concrete.
- Prefer specific decisions over generic effort language.
- Capture what changed, not just what you worked on.
- Distinguish impact from implementation.
- Separate your contribution from team contribution.
- Mark uncertainty honestly instead of smoothing it over.
- If something is confidential, write a public-safe version rather than omitting the story entirely.

## Useful prompts

Ask questions like:
- What was the real hard part here?
- What did I decide that a more junior engineer might have missed?
- What did I deliberately not build yet?
- What made this shippable rather than just clever?
- What proof do I still need if I want to tell this story later?

## Resources

- [references/capture-template.md](references/capture-template.md)
- [references/evidence-prompts.md](references/evidence-prompts.md)
- [references/output-variants.md](references/output-variants.md)

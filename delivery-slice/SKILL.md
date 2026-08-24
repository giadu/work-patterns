---
name: delivery-slice
description: Deliver new features as the smallest mergeable vertical slice first, then layer parity, abstraction, and cleanup afterward. Use when implementing backend, frontend, workflow, integration, or AI-product changes where the main risk is overbuilding the first version instead of getting one real path working.
---

# Delivery Slice

## Overview

Use this skill to scope the first implementation as the smallest mergeable slice that works in a real execution path. The goal is to avoid building a broad foundation before the feature has proven shape, behavior, and value.

## Core rule

Get one real user path working first. Do not start by designing the final foundation unless the existing code clearly blocks the feature.

## Default priorities

1. Get one real end-to-end path working.
2. Reuse existing patterns before introducing new ones.
3. Introduce the fewest new concepts possible.
4. Add only the tests needed for the chosen slice.
5. Leave broader parity, generalization, and cleanup for follow-up.

## Working rules

- Reuse existing modules, services, handlers, jobs, components, or tool wiring whenever possible.
- Prefer a narrow vertical slice over a partial foundation for many future paths.
- If another system is used as inspiration, match the required behavior first, not the full internal architecture.
- Keep the first PR small enough that its purpose can be explained in a few sentences.
- If a new abstraction is introduced, it must already be exercised by real code in the same change.

## Smell checks

Stop and rescope if the first PR:

- introduces many new concepts at once
- touches too many unrelated routes or modules
- mixes feature delivery with large refactors
- adds a runtime or foundation layer that only future work would use
- needs long architectural justification to explain why it exists

## Before coding

Write down these four points:

1. What is the minimum mergeable slice?
2. Which existing patterns will be reused?
3. What is intentionally postponed?
4. Which parity gaps are acceptable for the first merge?

If the first slice is hard to define, read `references/slice-examples.md`.

## During implementation

- Keep the real user path moving first.
- Prefer adapting current code to the feature over building a reusable system too early.
- Split work into layers when needed:
  - base mergeable implementation
  - parity fixes
  - cleanup or abstraction
  - broader rollout

## After implementation

Summarize:

- what the base slice covers
- what remains for follow-up
- which new abstractions were introduced
- why those abstractions were unavoidable

## Output style

- Be concrete.
- Prefer scope decisions over generic architecture talk.
- Name what is deliberately not included in the first merge.
- If the task is large, separate the base slice from follow-up layers explicitly.

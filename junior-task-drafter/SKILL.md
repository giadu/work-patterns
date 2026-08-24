---
name: junior-task-drafter
description: Turn rough requirements, issue threads, review feedback, or design notes into execution-ready tasks for junior engineers. Use when context is scattered, the task needs clearer scope and constraints, or you want a junior engineer to learn while implementing instead of relying on vague AI-generated output.
---

# Junior Task Drafter

## Overview

Use this skill to convert scattered context into a task a junior engineer can start immediately. The goal is not just to make the work executable, but to make the reasoning visible enough that the junior engineer can learn while doing it.

## Thesis

In the AI era, vague tasks produce fast output but weak judgment. A good junior task makes scope, constraints, references, acceptance criteria, and non-goals explicit, then uses a small number of learning checkpoints to force real reasoning instead of passive implementation.

## Scope

This skill covers:
- extracting the background and real goal from issues, PRs, comments, design notes, Slack threads, or meeting notes
- scoping the work based on existing codebase patterns
- writing a junior-friendly execution brief with minimal ambiguity
- producing a complete task structure with `overview`, `goal`, `requirements`, `implementation notes`, `acceptance criteria`, and `out of scope`
- optionally adding short learning checkpoints that make the junior engineer cite code references and justify implementation choices
- optionally formatting the final output as a GitHub issue, Linear issue, or plain task brief

This skill does not cover:
- implementing the feature
- creating the follow-up PR
- rewriting an entire design doc end to end

## Workflow

### 1. Gather the source context

Start from the raw material that already exists:
- issue or ticket text
- related PRs
- design comments
- review feedback
- reference implementations
- chat threads or meeting notes

If the context comes from GitHub, `gh` can be used as a convenient input source, but GitHub is optional, not required.

### 2. Compress the context into implementation requirements

Separate these first:
- what the task is trying to achieve
- what is in scope now
- what is out of scope now
- what constraints come from the existing codebase or product behavior

Do not restate review feedback as review feedback. Convert it into implementation requirements.

Bad:
- `use errors.Is instead of strings.Contains`

Better:
- `follow the existing error-classification pattern and use errors.Is where error identity matters`

### 3. Remove ambiguity for a junior engineer

Always make these explicit:
- which layer is touched: endpoint, batch, backend service, frontend, schema, spec, integration, and so on
- expected files when they are predictable
- acceptance criteria
- out of scope

Include these when relevant:
- reference files or reference PRs
- identity rules
- rollback or retry expectations
- UI behavior such as optimistic update and failure handling
- test expectations and what regressions they should protect against

### 4. Let the codebase win over the rough design

If the design comments and the existing codebase disagree, prefer the codebase unless the task explicitly calls for changing that pattern.

State clearly what existing pattern the implementation should follow.

Examples:
- `follow the same selector rules as the existing favorites endpoint`
- `keep retry behavior aligned with the current job-runner pattern`

### 5. Produce the final task draft

Use this order by default:
- title
- overview
- goal
- requirements
- implementation notes
- acceptance criteria
- optional learning checkpoints
- out of scope

Use `references/task-template.md` as the default output structure.
Use `references/scoping-checklist.md` before finalizing.

If the user wants, add a GitHub-ready issue title/body or another tracker-specific format at the end.

### 6. Add learning checkpoints when coaching matters

If the user wants the junior engineer to learn through the task, add a short optional section such as:
- `before implementation, please comment with`
- `learning checkpoints`

Use open-ended prompts, not multiple choice.

Good learning checkpoints:
- ask which existing files or endpoints should be used as references
- ask which layer or abstraction should be extended, and why
- ask what tests should be added and which branches they cover
- ask what rollback, validation, or edge-case behavior should happen
- ask what alternative was considered and rejected, and why
- ask what the user-visible or request/response behavior will be step by step
- ask what bug or regression each planned test is supposed to prevent

Bad learning checkpoints:
- vague prompts like `please research this`
- quiz-style multiple choice
- hiding core requirements that should have been explicit in the task

Rules:
- keep hard requirements explicit; checkpoints are for reasoning, not for hiding scope
- keep the section short, usually 3 to 5 prompts
- ask for codebase evidence when possible
- prefer short-answer prompts that require justification
- require exact file references when asking which existing pattern to follow
- prefer prompts that force explanation, comparison, and prediction over prompts that only ask for a draft

## Output rules

- write at a level where a junior engineer can start immediately
- avoid ambiguous language
- say what is not included, not only what is included
- use implementation-task wording, not review-comment wording
- reference existing APIs, files, handlers, jobs, or patterns when that reduces ambiguity
- if the task spans multiple repos, split the work clearly by repo
- when adding learning checkpoints, make them evidence-based and keep them optional to the task structure

## Resources

- [references/task-template.md](references/task-template.md)
- [references/scoping-checklist.md](references/scoping-checklist.md)

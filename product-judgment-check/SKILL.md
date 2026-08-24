---
name: product-judgment-check
description: Surface product, domain, data-consistency, and operational risks before implementing a feature. Use when planning medium or large changes, especially AI features, async workflows, integrations, user-facing automations, or any task where the main risk is building the wrong behavior rather than writing the code.
---

# Product Judgment Check

## Overview

Use this skill before implementation to pressure-test a feature as product behavior, not just code shape. The goal is to surface ambiguity, weak assumptions, source-of-truth problems, and failure modes early enough to change the plan.

## Workflow

### 1. Restate the change in product terms

Start by summarizing:
- what is changing
- who the real user is
- what they are trying to do
- what success looks like from their point of view

If the request is too implementation-shaped, restate it in user and product terms first.

### 2. Run the five lenses

Check the work through these five lenses before proposing implementation details.

#### Lens A. User and product behavior

Ask:
- Who is the real user of this change?
- What are they trying to do?
- What would make the experience confusing, noisy, or low-trust?
- Is it better to show nothing than to show something weak?
- What should the user see when the feature succeeds, fails, or has no useful output?

#### Lens B. Domain and business rules

Ask:
- What business rule is this behavior protecting?
- Which constraints are non-negotiable?
- What would count as a plausible but wrong result?
- Are there hidden assumptions based on the domain?
- What should happen in borderline cases?

#### Lens C. Source of truth and consistency

Ask:
- What is the source of truth?
- Is this value a snapshot or a live view?
- Could counts, filters, and visible results drift apart?
- Are there duplicate, race, or stale-data risks?
- Which writes or reads need to stay aligned?

#### Lens D. Operational behavior

Ask:
- What happens when this fails?
- What should be retried, skipped, hidden, or surfaced?
- What logging, auditability, or traceability will support need later?
- Does any async job, webhook, or batch behavior change the risk profile?
- What does a safe no-op look like?

#### Lens E. Maintainability and ownership

Ask:
- Where should this logic live?
- Is the mode or flow explicit?
- Is the implementation easy to reason about later?
- Are names, interfaces, and boundaries clear?
- Will the next engineer understand why it behaves this way?

### 3. Check high-risk patterns

If the change touches auth, permissions, tokens, invitations, payments, external side effects, AI-generated output, async processing, state transitions, migrations, or multiple paths to the same outcome, explicitly check:

- state predicates: what exact condition means usable, active, expired, revoked, failed, or complete?
- path parity: do all paths to the same business outcome enforce the same rules?
- authorization before detail: what data stays hidden until permission is proven?
- side-effect ordering: what happens if the DB write and email/API/webhook outcome disagree?
- concurrency: can retries, overlaps, timeouts, or cancellation leave stale state behind?
- deploy safety: can existing data or rollout order violate the new invariant?
- real user reachability: can the actual user reach the route or UI before the feature grants new permissions?

If multiple paths produce the same outcome, write a short rule matrix:

```text
Outcome:
Paths:
Rules that must match:
Open questions:
```

Read `references/checklist-examples.md` and `references/failure-patterns.md` when the change looks subtle, risky, or domain-heavy.

### 4. Produce a judgment note

Unless the user asks for a different format, produce a compact pre-implementation note with these sections:
- Problem
- User and domain context
- Key risks and edge cases
- Source of truth and consistency concerns
- Operational behavior
- Recommended implementation direction
- Open questions

Keep it concise and decision-oriented.

### 5. Push on ambiguity

If something sounds underspecified, call it out. Prefer a sharp question over pretending the ambiguity does not exist.

Examples:
- "What should happen when the output is technically valid but still too weak to show?"
- "Is this value expected to be a snapshot or always reflect current state?"
- "Which side is the source of truth if these two records disagree?"

## Output style

- Be direct.
- Prefer concrete risk statements over abstract process talk.
- Separate product concerns from technical concerns.
- If the task is small, compress the output. If it is large, keep the same structure but give fuller notes.

## When to go deeper

Read `references/checklist-examples.md` when:
- the task involves AI-generated output
- the change includes async processing or batch behavior
- the user is unsure what kinds of edge cases to look for
- the request sounds implementation-heavy but domain-light

Read `references/failure-patterns.md` when:
- the change includes auth, permissions, invitations, tokens, email delivery, webhooks, migrations, or state transitions
- the same outcome can be reached through multiple API or UI paths
- the feature can create sensitive URLs, logs, or user-visible status mismatches
- you want concrete failure modes to check before implementation

---
name: systems-integrity-review
description: "Review a design or implementation before merge for production integrity: boundaries, scope, state, data consistency, asynchronous work, operations, migration safety, and tests. Use after a feature has a proposed shape, especially for integrations, multi-tenant products, jobs, or high-consequence workflows."
---

# Systems Integrity Review

## Overview

Use this skill after the product direction is clear and before a change is considered ready to merge. It pressure-tests whether the implementation preserves the system's integrity under real conditions: partial failure, retries, stale work, rollout, permissions, and future maintenance.

It complements `product-judgment-check`:

- `product-judgment-check` asks whether the intended behavior is correct.
- `systems-integrity-review` asks whether the implementation can preserve that behavior in production.

## Review lenses

### 1. Boundaries and responsibilities

- Does domain logic stay independent of a particular provider, transport, or UI?
- Are external payloads translated at adapter boundaries rather than leaking through core models?
- Does each component have one clear responsibility?
- Did a convenience shortcut create a new accidental source of truth?

### 2. Scope and authorization

- Is tenant, account, project, workspace, or user scope explicit through the whole path?
- Are server-side permission checks independent from UI visibility?
- Can an absent or broad filter silently expand access?
- Do cache keys, jobs, events, exports, and audit records preserve the same scope?

### 3. State, modes, and defaults

- Is the state model explicit and are invalid transitions rejected or safely handled?
- Is processing mode selected once rather than mutated throughout the flow?
- Are defaults safe for existing users and unexpected values?
- Do all paths to the same business outcome enforce the same rules?

### 4. Data and transaction integrity

- Do schema constraints and indexes match actual lookup, uniqueness, and update paths?
- Could lists, counts, aggregates, and visible status drift apart?
- Are multi-step writes atomic where partial success would be harmful?
- Does the design preserve the difference between a snapshot, current state, and history?

### 5. Asynchronous and external side effects

- Is work persisted before a worker, webhook, notification, or external call depends on it?
- What makes a retry the same operation? Is the idempotency boundary correctly scoped?
- Can stale workers, duplicate delivery, or timeouts overwrite a newer outcome?
- Are retryable, terminal, and manual-review failures distinguishable?
- Does the system have a safe replay or recovery path?

### 6. Operational execution

- Can an operator run a narrow, safe dry-run or tenant/object-scoped recovery?
- Are operational knobs explicit and observable rather than hidden in code?
- Does the result include enough logging, audit context, and error classification to explain failure?
- Can a backfill stop, resume, and avoid affecting unrelated data?

### 7. Migration, deploy, and rollback safety

- Is the new application version compatible with the existing schema and data during rollout?
- Do migration constraints, defaults, and backfills preserve existing records?
- Does rollback remain valid after new data exists?
- Are generated artifacts, contracts, and consumers updated in the correct deploy order?

### 8. Validation strength

- Do tests cover the real invariant, not merely the happy path?
- Are no-op, retry, stale-state, authorization, and rollback cases covered where relevant?
- Are manual checks labelled honestly rather than presented as automated coverage?
- Does the final validation match the user-facing and operational risk of the change?

## Output

Provide findings ordered by severity. For each material finding include:

- the integrity risk;
- the evidence or missing evidence;
- why it can fail in production; and
- a concrete correction or question.

If no finding is material, state that explicitly and name any remaining validation gap. Do not turn the checklist into a score or invent concerns that do not affect the change.

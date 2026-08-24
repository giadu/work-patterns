# Slice Examples

Use these examples to decide what counts as a good first delivery slice and what should wait.

## Example 1. New AI-assisted review action

Weak first slice:
- create a generic orchestration framework
- add support for many prompt types
- build analytics, retries, admin UI, and fallback modes at once

Better first slice:
- support one concrete user-facing action
- wire one real execution path end to end
- validate the output enough to make that path trustworthy
- leave broader orchestration and analytics for follow-up

## Example 2. Admin search page

Weak first slice:
- build a flexible query builder
- add exports, saved filters, pagination variants, and bulk actions immediately

Better first slice:
- support the one search flow the user needs now
- render one trustworthy result list
- ship the simplest filtering and error states needed for that path
- leave exports and advanced filter UX for follow-up

## Example 3. New webhook integration

Weak first slice:
- design a universal event-processing framework
- support every event type before the first one is live

Better first slice:
- support one event type that unlocks the real business outcome
- handle idempotency and failure behavior for that path
- leave generic event routing and broader event coverage for follow-up

## Example 4. Existing feature needs a second provider

Weak first slice:
- refactor everything around a future provider abstraction before proving the second provider works

Better first slice:
- adapt the current flow to support provider two in one real path
- introduce abstraction only where both providers already exercise it
- leave broader cleanup for a follow-up PR

## Quick self-check

- Does this first merge solve one real user path, or only prepare for future work?
- Is any new abstraction already justified by real code in this change?
- If I removed half of this PR, would the feature still work for one real path?
- Am I shipping behavior, or just building a platform for later?

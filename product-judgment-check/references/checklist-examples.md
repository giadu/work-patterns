# Checklist Examples

Use these prompts to deepen the review when a feature is ambiguous, user-facing, or operationally risky.

## AI features

- What happens if the model output is plausible but still bad for the product?
- What should happen when the model returns nothing useful?
- Which parts need validation before the output is allowed into the user-facing flow?
- Is the feature still acceptable if it fails silently, or does silence create confusion?
- Does trust depend on surrounding UI states as much as on output quality?

## Async workflows and batch jobs

- If the job fails after partial progress, what state is left behind?
- Can an old worker overwrite a newer attempt?
- What makes the operation idempotent?
- Is there a safe retry path?
- What should be logged or persisted for later debugging?

## Product and UI behavior

- What should the user see when the feature has nothing useful to show?
- Is there any state that technically works but still feels broken or noisy?
- Does this introduce a new concept the user has to understand?
- Is there a smaller version that already feels trustworthy?

## Data consistency

- Which table or object is the source of truth?
- Is this value a snapshot or a live view?
- Could filters, counts, and visible results drift apart?
- What happens if two updates happen close together?

## Quick self-check before opening a PR

- Can I explain the domain rule behind this change in one sentence?
- Can I explain the worst realistic failure mode?
- Do I know what should be shown, hidden, retried, or skipped?
- Did I choose the implementation shape because it matches the product and domain need, not just because it is the easiest code path?

---
name: junior-work-review
description: Review a junior engineer's design, implementation plan, or code change with evidence-backed technical findings and focused coaching. Use when mentoring through review, checking an updated submission, or turning review feedback into actionable next steps. Does not draft a new assignment or assess a person's overall ability.
---

# Junior Work Review

Review the work against the intended behavior and actual execution path. Explain consequential findings so the engineer can understand and verify the correction. Keep acceptance requirements separate from optional coaching.

## Establish what is being reviewed

Read the current submission, relevant requirements and prior feedback. For a code review, identify the base and current revision; for a design, identify the proposed slice and existing behavior. If reviewing a linked comment or thread, read that material rather than inferring its contents from a title.

Locate the owning component, runtime entrypoint and relevant interfaces, schema and tests. Use file references to substantiate conclusions. Limit investigation to evidence that can affect the review; do not require a full historical audit for a small change.

Treat requirements as intended behavior and code as evidence of current behavior. Either may be stale or wrong. Explain material conflicts instead of automatically declaring the existing code correct. If a missing artifact prevents verification, state the uncertainty rather than inventing a finding.

## Review at the right stage

For a design or implementation plan, check whether it:

- changes the correct runtime and component;
- distinguishes existing capabilities from work still required;
- defines a useful, bounded result and deliberate exclusions;
- explains relevant identity, source-of-truth and permission rules;
- addresses consequential failure paths and rollout dependencies;
- specifies validation that can detect the anticipated regression.

For code, inspect the changed behavior and its callers, not just the description. Follow relevant paths through authorization, persistence and user-visible results. Check generated contracts, schema and consumers together where they change. Assess tests by the failures they catch, not their count.

Apply concurrency, retry, migration or external-side-effect checks when the change needs them. Avoid demanding new abstractions, more phases or exhaustive tests without a concrete benefit to the requested behavior.

Use available local conventions and relevant review guidance, but do not require other skills, a specific programming language or a hosting platform.

## Write actionable findings

Each finding should contain the location, triggering condition, current behavior, user/system impact and the required correction or invariant. Include a way to verify the fix. Recommend an exact implementation only when the evidence supports it; otherwise leave room for a justified solution.

Prioritize correctness, authorization, data integrity and operational failures. Use the team's severity vocabulary when available. Otherwise distinguish **blocking**, **non-blocking improvement**, and **optional learning question**. A severe hypothetical without a plausible execution path is not a proven blocker.

Place file-specific comments at the relevant lines when possible. Keep cross-file design, rollout and evidence gaps in the overall note. Consolidate repeated instances of one root cause so the author does not receive a wall of redundant comments.

Do not hide a known requirement behind a quiz. State the defect and required behavior directly before asking the engineer to explain their proposed correction.

## Add coaching where it helps

Choose a few questions only when they target a reasoning gap visible in this submission. Useful prompts ask the engineer to:

- trace one user action through the real code and name the authoritative state;
- explain why a chosen boundary or trade-off fits this task;
- predict what happens after a partial failure;
- show which test fails before the fix and why;
- explain how a proposed change preserves a stated invariant.

Adapt depth to the task and the user's mentoring intent. Do not require teach-back for every minor correction. Optional coaching does not become a merge gate unless explicitly agreed.

AI assistance is not itself a defect. Verify claims against artifacts and evidence regardless of how the work was produced. Do not infer comprehension, effort or ability from writing polish, response speed, language fluency or a correct-looking explanation. If an explanation contradicts the code, identify the mismatch and request clarification.

## Re-review fairly

Check the new revision against previous findings. Mark each material item resolved, still open or no longer applicable with a short reason. Inspect neighboring paths for regressions introduced by the fix; do not repeat resolved comments or silently change acceptance criteria.

Separate necessary follow-up work from the current change. If earlier feedback was wrong, acknowledge and correct it.

## Output and boundaries

Lead with actionable findings in severity order, followed by a concise readiness assessment and verification limits. Include optional coaching separately. When no findings are supported, say so and state what remains unverified.

When the user needs comments to share, provide concise, respectful copy-paste drafts in the requested language, or follow the review thread's language. Use this shape as needed:

```text
Finding and location:
Trigger and impact:
Required change:
Verification:

Optional learning question:
```

Run proportionate checks if authorized and feasible. Distinguish tests inspected, checks executed, CI evidence and checks not run. Never present code inspection as a passing test result.

A request to review does not by itself authorize implementation edits or posting comments. Draft in the conversation by default. If the user explicitly requests posting, verify the current revision and publish only the requested comments; preserve existing authorization rather than asking again automatically.

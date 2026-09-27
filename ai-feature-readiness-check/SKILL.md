---
name: ai-feature-readiness-check
description: Assess an AI-powered feature before implementation, pilot, or release. Define the AI-specific behavior contract, evaluation evidence, autonomy limits, failure handling, and rollout conditions. Use for model-backed product features and agents, not ordinary AI-assisted coding or generic product reviews.
---

# AI Feature Readiness Check

Produce a decision about the next safe, useful stage of a feature: bounded experiment, controlled pilot, or production release. Readiness is relative to the intended audience, exposure and consequences; a working demo is not evidence for every stage.

## Establish the decision and evidence

Identify the user outcome, requested stage and proposed AI role. Reuse existing product decisions instead of restarting discovery. Briefly compare a simpler deterministic or human-assisted approach; respect an explicit AI choice while explaining trade-offs.

Inspect the relevant specification, implementation, tests and evaluation results that are available. Separate observed facts, assumptions and missing evidence. Ask only questions that materially change scope or the recommendation; otherwise proceed with stated assumptions.

Do not require another skill or a particular framework. When a general product review or guided engineering workflow already exists, add the AI-specific findings to that record rather than duplicating it.

## Define the behavior contract

Use only the concerns relevant to this feature:

- **Inputs:** authoritative sources, freshness, tenant scope, permitted data use and untrusted content. Distinguish retrieved instructions from authorized instructions.
- **Outputs:** schema plus domain meaning, supporting evidence, acceptable uncertainty and the cases that should produce no answer or a clarifying question.
- **Consequences:** whether the model suggests, decides or acts. Define permission checks and any approval required for consequential arguments. Prompts and model self-checks are not authorization controls.
- **Failure UX:** what the user sees when information is missing, output is invalid, a provider fails or work is interrupted. State which fallback preserves the product promise; a confident fabricated result is not a fallback.

For tool-using or asynchronous features, also inspect duplicate execution, approval expiry, revoked access, cancellation, stale workers and uncertain external completion. A workflow engine does not guarantee exactly-once external effects. Keep these checks lightweight for read-only generation without persistent execution.

## Specify evidence that can change the decision

Define a representative evaluation set from the actual task and domain. Include ordinary use, relevant ambiguity and high-cost failure categories. Do not invent results or claim a particular sample size proves safety.

Distinguish:

- deterministic checks for permissions, schema, references, limits and state transitions;
- component evaluations that locate retrieval, generation or tool-selection failures;
- end-to-end evaluations for usefulness and completion of the user task;
- human review for domain judgment and calibration of model judges.

Use a compact table when helpful:

| Failure or quality criterion | Check / representative case | Proposed acceptance condition | Evidence available | Next action |
| --- | --- | --- | --- | --- |

Derive acceptance conditions from consequences and baseline behavior. Label suggested thresholds as proposals. Zero observed failures is a result on the tested cases, not a universal guarantee. Keep a held-out set where iterative tuning could overfit visible examples.

Record model, prompt, toolset and relevant data/configuration versions for reproducibility. Rendered-context snapshots catch accidental changes, but do not establish semantic quality. Mock tests prove the behavior exercised by the mock, not external integration or live model performance.

## Check operation and rollout proportionately

Identify retry ownership and limits for time, attempts, concurrency and cost. Include failed billable attempts in usage accounting. For mutating tools, define idempotency or reconciliation before replaying an uncertain result.

Choose the smallest exposure that can resolve the remaining uncertainty. Define observable success/failure, a responsible owner, rollback or disable conditions and the next safe recovery action. Distinguish disabling future actions from undoing completed effects. A provider fallback needs its own quality evidence before being treated as interchangeable.

Use privacy-preserving telemetry; do not assume full prompts or customer data must be logged. Do not run paid evaluations, send customer data to a new provider, deploy, or enable side effects unless the user's task authorizes those actions.

## Deliver a compact readiness note

Lead with the recommended next stage and why. Include:

1. The user outcome and proposed AI behavior.
2. Material gaps, with evidence and their effect on the decision.
3. Evaluation cases and acceptance conditions needed for the next stage.
4. The smallest useful slice, failure behavior and operational limits.
5. Remaining decisions and owners, using "unassigned" when unknown.

Distinguish blockers for the requested stage from improvements that can follow. A missing production control may still allow an isolated experiment using synthetic inputs. Do not claim a stage is ready without evidence, and do not turn every optional best practice into a blocker.

Keep a small read-only feature's note short. Expand for autonomous actions or consequential decisions. Follow the user's requested output format; otherwise respond in the conversation, without creating a backlog or editing code automatically.

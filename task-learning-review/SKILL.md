---
name: task-learning-review
description: Reflect on a completed task or stable delivery milestone to extract evidence-backed lessons, propose small workflow experiments, and identify optional public-writing ideas. Use for a learning debrief after delivery or when asking what to improve next time; not for routine status updates, release approval, or career-impact summaries.
---

# Task Learning Review

Turn completed work into a better next decision. A successful delivery can yield no reusable lesson; an unsuccessful attempt can yield a valuable one. Do not manufacture a lesson, workflow change, or article to fill a template.

## Establish the closure boundary

Use the task conversation and the smallest relevant set of artifacts: intended behavior, key decisions, review feedback, tests, delivery records, and observations after release. Read linked private artifacts only through available, authorized access. Never imply access to another chat or system that was not inspected.

Confirm what is actually complete. If closure means all related PRs merged and production deployed, identify those PRs and the deployment evidence for their changes. A green CI run or preview is not proof of production deployment, adoption, or business impact. Distinguish observed status, user-reported status, and unknown status. Treat unknown scope as unknown rather than claiming every PR was checked.

Missing deployment access does not block reflection: label the review provisional and limit conclusions to available evidence. A stable milestone, failed experiment, or non-code task may have a different closure boundary. Do not merge, deploy, retry checks, or start monitoring merely to make the task eligible for this review.

## Find changes in understanding

Look for consequential surprises, corrected assumptions, decisions with meaningful alternatives, repeated friction, and useful practices worth keeping. Reconstruct the sequence only far enough to explain the lesson; avoid a chronological activity report.

For each worthwhile candidate, connect:

- **Before:** the assumption, expectation, or working practice.
- **Evidence:** what was actually observed and where it came from.
- **Updated understanding:** what the evidence supports, including uncertainty or competing explanations.
- **Transfer:** a future situation where this changes a decision, and where it would not apply.

Distinguish domain learning, technical learning, collaboration/process learning, and understanding of AI-assisted work when that distinction changes the next step. Do not require a lesson in every category.

Separate a task observation from the user's own learning. An agent solving a problem does not demonstrate that the user understands it. Where important, ask one or two focused reflective questions such as "What would you now check first, and why?" Use their answer to refine the lesson, not to grade them or infer traits. If unanswered, label it a candidate lesson and continue with the evidence available. Do not write first-person claims of learning on their behalf.

Successful release alone cannot establish why a practice worked. Check whether a workaround addressed a local circumstance before generalizing it into a rule.

## Propose a small workflow experiment

Prefer the highest-value change or no change. A proposal should specify:

- the friction or failure it addresses and supporting evidence;
- the concrete behavior to change and when it applies;
- its narrowest appropriate home: task handoff, repo instructions, an existing skill, a tool/check, or personal working guidance;
- how to tell on a subsequent comparable task whether it helped, and when to remove or revise it.

First inspect the relevant existing guidance if accessible. Reuse, simplify, or remove a rule before adding overlapping guidance or creating another skill. One incident usually supports a bounded experiment; a directly demonstrated correctness invariant may justify a stronger rule. Recurrence is evidence, not a mandatory threshold.

Keep proposals distinct from adopted changes. This review does not itself authorize edits to skills, hooks, repo instructions, global preferences, or shared processes. If the user has also authorized applying improvements, make only the supported scoped change, show what changed, and validate it appropriately. Otherwise present a concrete proposal or diff for a decision. Do not request permission again for already-authorized edits.

Describe validation as a future check on the next relevant task; do not create reminders or background monitoring unless requested. Compare the result when the user later brings that task back for review. Retire experiments that add ceremony without helping.

## Surface writing potential only when useful

Optionally identify a Substack or other public-writing seed: a reader's practical problem, a defensible central claim, a safe example, and what still needs evidence. A task can support a small section of a future article without justifying a whole post. An angle may be worth saving even when no workflow change is needed.

Employer material stays in its authorized environment. Personal skills and public-writing seeds must use generalized lessons without private PR links, code, internal metrics, customer details, or identifiable incidents. Removing names alone does not make a story safe. If generalization would lose the necessary evidence, keep the detail internal and omit the public claim.

Produce an idea, not a full draft or publication, unless requested. If available and requested, use `substack-draft-starter` for the draft. Use `project-impact-capture` for career evidence or contribution summaries; do not automatically generate those outputs as part of this review. Neither skill is required to complete the debrief.

## Deliver a proportionate closeout

For a small task, a few paragraphs may suffice. For substantial work, a useful shape is:

1. Closure status and evidence limits.
2. The few lessons supported by evidence, distinguishing confirmed understanding from candidates.
3. A concrete workflow experiment, or why no change is justified.
4. An optional writing seed and any unresolved question worth revisiting.

Keep internal evidence references inside authorized work contexts. Default to an inline response. When saving is requested, use an agreed destination appropriate to the material; do not silently create a personal archive of employer work. A handoff to a personal coordination chat should contain only the permitted generalized lesson, proposed experiment, and open question.

A good result makes the next decision clearer without turning every delivery into a retrospective project.

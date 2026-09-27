---
name: delegation-loop
description: Turn ambiguous work into verifiable delegation briefs for people or AI agents, then assess returned work against the agreed boundaries. Use when handing off work, splitting it among contributors, or diagnosing a delegation that failed. Does not dispatch agents, assign people, or send messages by itself.
---

# Delegation Loop

Run the cycle Decompose -> Externalize -> Verify at the scale of the request. The useful output is work someone can own and a result the delegator can evaluate. Task count, prompt length and parallel sessions are not success measures.

## Locate the current stage

If preparing a handoff, establish the outcome and scope. If reviewing returned work, start with the original brief and available evidence. If repairing a failed delegation, identify whether the gap was decomposition, missing context, authority, execution or verification before adding instructions.

Reuse agreed product decisions and delivery scope. Do not repeat a general product review or require a guided implementation protocol. This skill prepares and evaluates a handoff; it does not replace the recipient's working method.

## Decompose around verifiable outcomes

- Name the desired result, why it matters, and the decisions the delegator retains.
- Inspect available context before choosing boundaries. Distinguish facts from assumptions and unresolved decisions.
- Keep closely coupled work together when splitting would make correctness harder to judge.
- For multiple packages, identify dependencies, shared interfaces, overlapping writes and the integration owner. Propose parallel work only when contracts and workspace ownership make it practical.
- If uncertainty prevents an implementation brief, delegate a bounded investigation with a decision artifact instead. State the question it must resolve.

Do not invent recipients, capacity, deadlines or access. Use proposed roles or unassigned owners where needed. A single package is sufficient for a small task.

## Externalize the context needed to act

Give the recipient the minimum sufficient context, with authoritative references and concrete boundaries. Explain the reasons behind consequential constraints rather than scripting every implementation step.

Use this compact brief, omitting fields that add no value:

```text
Outcome and reason:
Scope / out of scope:
Relevant context and authoritative references:
Invariants: what must remain true?
Decisions the recipient can make:
Decisions retained by the delegator:
Dependencies and coordination boundaries:
Expected deliverable:
Acceptance evidence, including integration checks where relevant:
Checkpoint / conditions to stop and ask:
Owner, reviewer and integration owner (if known):
```

Tailor autonomy to consequence, reversibility and available verification, not simply whether the recipient is a person or AI. People also need workload agreement and room to exercise judgment; agents need executable context and explicit tool/access limits. Do not assume those needs are interchangeable.

Define escalation for a violated invariant, incompatible interface, missing access or material scope change. Avoid requiring permission for every routine choice inside the authorized boundary. Delegating a task does not expand authorization to publish, deploy, spend money or contact others.

## Design verification before execution

Map acceptance claims to observable evidence. Ask what result could look convincing while still being wrong. Choose checks that would expose that case: a failing-path test, reconciliation, independent calculation, integration exercise or domain review.

Treat a recipient's summary as a claim, not its own proof. Verification effort should match risk. Where the delegator cannot assess a critical result, propose qualified review, a smaller scope or a bounded experiment instead of claiming a checklist guarantees quality.

Keep checkpoints at expensive or hard-to-reverse decisions. Avoid imposing constant status updates on work that can be checked cheaply at completion.

## Receive and close the loop

When an artifact is supplied, compare it with the original outcome and invariants, inspect the actual artifact and run appropriate checks when authorized and available. Distinguish verified behavior, reported behavior and unverified claims. A merge or passing unit test does not automatically prove the integrated outcome.

Return one clear disposition: accepted within the agreed scope, specific rework needed, or blocked on a named decision/evidence gap. State residual limitations without silently weakening acceptance criteria. Preserve the recipient's valid work when requesting corrections.

Capture one reusable adjustment if a delegation failure revealed missing context or a weak boundary. Do not turn every one-off incident into a permanent rule.

## Output

For a handoff, provide the brief; for multiple packages, add a compact dependency/ownership table. For returned work, lead with the disposition and supporting evidence. For a failed handoff, identify the failed part of the loop and rewrite only what needs repair.

Use the user's requested format and language. Otherwise respond in the conversation. Do not create tasks, assign owners, launch agents, or send the brief externally unless the user requests that action. If used within an existing task record, update the relevant handoff section rather than generating a competing record.

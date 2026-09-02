---
name: cs-communication-review
description: Turn technical investigation notes or engineer–CS conversations into clear, actionable CS communication. Use when rewriting a technical explanation, checking whether a handoff answers CS's operational question, or—only when explicitly requested—reviewing historical conversation patterns and sources of misunderstanding. Do not infer blame, performance, or psychological traits.
---

# CS Communication Review

## Purpose

Help engineering communicate conclusions, uncertainty, customer impact, and next actions in a form CS can use. Improving the message is the default goal; determining responsibility is optional and must not be inferred from an ordinary rewrite or review request.

## Choose the mode

Infer the narrowest mode that satisfies the request:

1. **CS-ready rewrite (default):** Rewrite one technical explanation or investigation result. Do not inspect history or assign responsibility.
2. **Communication-friction review:** When the user asks why an exchange was difficult or how to improve recurring collaboration, identify obstacles in the messages, information flow, language, or process. Describe what would make the handoff work better without deciding who was at fault.
3. **Contribution analysis (explicit only):** Use only when the user explicitly asks whether the problem came from their explanation, the other participant's inputs or interpretation, or both. Analyze observable contributions without judging either person's general competence.

For modes 2 and 3, read [references/review-framework.md](references/review-framework.md). Use its attribution labels only in mode 3.

Do not treat “review this conversation,” “make this clearer,” or “help CS understand” as a request to determine blame.

## Historical evidence collection

This section applies only to modes 2 and 3. Use transcripts supplied by the user or connected messaging tools when the user asks to inspect historical conversations. Keep external-system access read-only unless the user separately requests a mutation.

Establish:

- the participants and their roles
- the available time range and message surfaces
- whether the search covers DMs, channels, threads, or only explicit mentions
- any limitations that could exclude relevant context

Search broadly enough to find both breakdowns and counterexamples where the same recipient understood the explanation on the first pass. Group messages into conversation threads or cases; message counts are not case counts.

For each selected case, read the full surrounding thread and reconstruct:

- the question or operational decision CS needed answered
- the facts available at that point in time
- the explanation the engineer provided
- the recipient's interpretation or follow-up
- any correction, changed conclusion, or later-discovered fact
- what CS needed to tell or ask the customer

Prefer a representative sample across time and outcomes. Do not build a conclusion from only the latest disagreement or from messages containing apologies.

## Optional contribution analysis

Use this section only in mode 3. Classify each case using one primary label and, when useful, one secondary label:

- **Sender-dominant:** the answer was inaccurate, ambiguous, poorly ordered, overly technical, or did not answer the operational question.
- **Recipient-dominant:** required inputs were wrong or omitted, a clear instruction was missed, or an unconfirmed interpretation was acted on.
- **Shared:** both the explanation and the interpretation or inputs materially contributed.
- **Process/system-dominant:** missing documentation, unclear ownership, misleading UI, or repeated manual setup created the failure.
- **Technical uncertainty:** the system evidence did not support a known root cause; follow-up questions were seeking a distinction the engineer could not yet prove.
- **No misunderstanding:** the recipient understood and correctly restated the answer.
- **Insufficient evidence:** the available messages do not justify attribution.

Treat a clarification question as evidence of a communication gap only after checking whether the earlier answer actually supplied the requested conclusion. A CS teammate asking for a customer-facing cause, risk, or next action is not necessarily failing to understand a technical explanation.

Do not infer intelligence, motivation, personality, or general job competence from message history. Describe observable behaviors such as “supplied the wrong website ID,” “buried the conclusion after implementation details,” or “did not correct an explicit paraphrase.”

## Historical synthesis

In mode 2, synthesize recurring friction and preventive improvements without responsibility labels. In mode 3, separate three levels in the final judgment:

1. **Case-level responsibility:** what happened in each representative exchange.
2. **Recurring communication pattern:** what repeats across cases, if anything.
3. **Leverage:** which change would prevent the most future loops, regardless of blame.

Avoid false precision. Do not invent percentages unless the user explicitly requests a quantified rubric and the evidence supports it. Distinguish an isolated mistake from a repeated pattern, and distinguish a person's knowledge gap from missing operational documentation.

When the user asks to evaluate feedback from a manager or teammate, state whether that feedback is supported in the specific case and whether it generalizes to the history.

## CS-ready rewrite

When an explanation needs improvement, rewrite it in the team's working language and put the decision-relevant information first:

```text
Conclusion:
What happened:
Direct cause:
What is still unknown:
What CS needs to confirm:
What happens after confirmation:
```

Move IDs, database evidence, code behavior, and logs into a short supporting section unless CS needs them to perform the next step. Explicitly separate the direct product cause from the upstream historical cause when the latter is unknown.

## Output

Match the output to the selected mode.

For a CS-ready rewrite, provide the revised message first. Add a short explanation of the structural changes only when it helps the user reuse the pattern.

For a communication-friction review, provide:

- evidence scope and limitations
- the communication bottlenecks observed
- patterns that already work well
- the highest-leverage message, process, or documentation changes
- a rewritten version of the current explanation when available

Do not include responsibility labels in this mode.

For an explicit contribution analysis, provide:

- evidence scope and limitations
- concise overall verdict
- representative case findings with direct message links when available
- recurring patterns attributable to each side and to the process
- whether the disputed feedback is fair for the current case
- the highest-leverage communication or documentation changes
- a rewritten version of the current explanation when one is available

Keep the tone candid, neutral, and useful. The final answer may identify mistakes, but it should make future collaboration easier rather than prosecute either participant.

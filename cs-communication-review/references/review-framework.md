# Engineer–CS Communication Review Framework

Use this framework for historical audits or whenever responsibility for a misunderstanding is disputed.

Responsibility analysis is opt-in. If the user wants only a clearer message or a review of communication friction, use the diagnostic dimensions to improve the handoff and do not assign attribution labels.

## Case record

Capture the minimum evidence needed to reason about each case:

```text
Date and thread:
CS request or decision needed:
Inputs supplied:
Engineer answer:
Recipient interpretation:
Correction or outcome:
Primary attribution:
Secondary attribution:
Evidence supporting attribution:
Preventive change:
```

For a communication-friction review, omit the two attribution fields and record only the observable bottleneck and preventive change.

Preserve links to the original thread when possible. Quote only the smallest passage necessary to support a finding.

## Diagnostic dimensions

### Input completeness and accuracy

Check whether CS supplied the identifiers, timestamps, screenshots, customer observations, reproduction conditions, or requested scope needed for the investigation.

Signals of recipient contribution include:

- a company ID labeled as a website ID
- missing screenshots or sample orders after they were requested
- asking engineering to support a path that was never confirmed as in scope
- acting on a paraphrase before it was confirmed
- forgetting an explicit prior instruction when the thread or documentation was available

Do not count information that CS could not reasonably access as an omission.

### Answer alignment

Check whether the response answers the question CS actually asked. Engineering evidence alone is not an operational answer.

Common mismatches:

- CS asks why something happened; the response lists database state
- CS asks what to tell the customer; the response explains implementation internals
- CS asks whether action is needed; the response only says a deployment or investigation is complete
- CS asks whether behavior is normal; the response reports logs without separating expected behavior from an unexplained incident

### Causal clarity

Separate:

- **Observed symptom:** what the customer or UI showed
- **Direct cause:** the condition that produced that symptom
- **Mechanism:** the relevant system behavior
- **Upstream historical cause:** how the data entered that condition
- **Unknown:** what the available evidence cannot prove

An answer can be technically correct and still unclear when these levels are mixed together. The direct cause may be known while the upstream cause remains unknown.

### Audience fit

Check whether the message can be used by a customer-facing teammate without reconstructing the investigation.

Potential sender contribution includes:

- leading with internal IDs, tables, batches, or code paths
- relying on machine translation for the key conclusion
- unexplained acronyms or English terms in an otherwise Japanese workflow
- ambiguous referents such as “request,” “it,” or “this data”
- placing the action at the end of a long technical report

Do not remove technical evidence that CS genuinely needs. Layer it after the conclusion.

### Confirmation handling

Pay special attention when the recipient restates the explanation.

- If the paraphrase is correct, confirm it explicitly.
- If it contains an error, correct the exact phrase before the conversation moves on.
- If the engineer confirms a paraphrase containing a typo or scope mistake, that is shared responsibility even if the recipient wrote it first.
- If the recipient proceeds without confirmation, that weighs toward recipient responsibility.

### Technical uncertainty

Do not treat repeated questions as comprehension failure when the root cause is genuinely unknown. Evaluate whether the engineer clearly said:

- what was confirmed
- what was inferred
- what was ruled out
- what remains unknown
- whether the incident was expected behavior or an anomaly

If those distinctions were missing, the recipient may be correctly pressing for a customer-safe statement.

### Process and documentation

Recurring exchanges often indicate a process defect rather than an individual defect. Look for:

- setup requirements that exist only in old Slack threads
- repeated manual inputs with no checklist
- ownership that depends on team memory
- UI labels that imply a setting is sufficient when additional configuration is required
- no standard handoff format between engineering and CS

Recommend a checklist, runbook, UI copy change, or response template when it would prevent more failures than coaching either participant alone.

## Optional attribution guide

Use this section only when the user explicitly asks who or what contributed to the misunderstanding.

Use **Sender-dominant** when the earlier answer omitted or obscured information needed to answer the explicit CS question.

Use **Recipient-dominant** when the answer was clear and actionable but the recipient supplied wrong inputs, missed an explicit condition, or acted beyond the confirmed scope.

Use **Shared** when both behaviors materially affected the outcome. Do not use “shared” merely to sound diplomatic; identify each contribution.

Use **Process/system-dominant** when the same failure is predictable from missing documentation, ambiguous UI, or unclear ownership.

Use **Technical uncertainty** when the central issue is not communication but the absence of evidence for a root cause. This label can coexist with Sender-dominant if uncertainty was communicated poorly.

Use **No misunderstanding** as a counterexample. Successful cases are evidence about what explanation style works with this recipient.

## Synthesis questions

Before writing the verdict, answer:

- Does the same failure repeat across independent cases?
- Does the recipient understand comparable technical material when the conclusion and boundary are explicit?
- Are apologies describing actual mistakes, ordinary politeness, or both?
- Did other participants also find the explanation unclear?
- Did the engineer change or correct the answer during the thread?
- Which problem is most preventable: input quality, answer structure, documentation, or system observability?
- Is the disputed managerial feedback valid for one case, a recurring pattern, or neither?

## Recommended layered response

For an internal CS handoff, prefer:

```text
Conclusion: One or two sentences with the customer-visible result.

What happened: A plain-language description of the mismatch or failure.

Direct cause: The confirmed condition that caused the behavior.

Still unknown: Anything the current evidence cannot establish.

CS check: The exact item CS or the customer must verify.

Next action: What engineering will do for each possible answer.

Technical evidence: Only the IDs, timestamps, logs, or code details needed to verify the conclusion.
```

If the working conversation is Japanese, use concise Japanese headings and keep unavoidable English identifiers in code formatting. If another language is used, preserve the same information hierarchy rather than translating the headings literally.

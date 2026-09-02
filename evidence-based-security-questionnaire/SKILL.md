---
name: evidence-based-security-questionnaire
description: Prepare accurate, reviewable responses to customer security questionnaires using verified system evidence. Use when a SaaS company must answer a client template without overstating controls, confusing plans with current practice, or exposing unnecessary sensitive detail.
---

# Evidence-Based Security Questionnaire

## Overview

Use this skill to answer a security questionnaire as an evidence-mapping exercise, not a marketing exercise. The goal is a response that a security, legal, or procurement reviewer can understand, challenge, and trust.

Never infer a control from a plan, a partial implementation, or a neighboring system. If evidence is missing, say so and identify the owner or follow-up needed.

## Intake

Gather:

- the original template and its required response format;
- the service/product scope being assessed;
- allowed disclosure level and redaction constraints;
- current evidence sources: policies, architecture, monitoring, access control, incident process, vendor list, audit material, or owner confirmation; and
- deadline and reviewer audience.

Do not place unredacted customer templates, credentials, or sensitive architecture details in a public repository.

## Workflow

### 1. Extract the real questions

Capture every question, sub-question, required option, evidence request, and definition. A parent checkbox may not cover its sub-questions.

### 2. Classify each response

Use one of these states:

- **implemented and evidenced** - current practice is supported by evidence;
- **implemented, evidence to attach** - the control exists but the reference needs confirmation;
- **partially implemented** - describe the exact boundary and compensating control;
- **not implemented / not applicable** - explain briefly without forcing a positive answer; or
- **needs owner confirmation** - do not guess.

### 3. Separate control layers

Do not collapse these into one claim:

- policy versus technical enforcement;
- preventive control versus detective control;
- point-in-time review versus continuous monitoring;
- planned change versus current production behavior; and
- service responsibility versus customer responsibility.

### 4. Draft precise answers

For each material answer, include the actual control, its scope, relevant limitation, evidence source, and any required customer action. Prefer a qualified accurate answer over a broad reassuring one.

### 5. Run an adversarial review

Ask what a skeptical reviewer would challenge:

- Is the statement more absolute than its evidence?
- Does the answer actually address the question?
- Are dates, scope, data categories, regions, and vendors current?
- Does a claimed control have an owner and operational path?
- Does the answer disclose more than is necessary?

## Deliverable

Produce a review table with:

| Question | Proposed answer | Evidence | Status | Limitation / follow-up |
| --- | --- | --- | --- | --- |

Only write into the client template after the proposed answers have been reviewed. Preserve the original and create a separately versioned output.

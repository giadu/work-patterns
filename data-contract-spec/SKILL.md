---
name: data-contract-spec
description: Define a reviewable data contract for imports, exports, files, events, or API payloads. Use when a team needs unambiguous fields, validation, ownership, error handling, examples, and acceptance criteria before implementing an integration.
---

# Data Contract Spec

## Overview

Use this skill to turn a vague data exchange request into a contract that engineering, operations, and the other party can review. The output should make clear what data crosses the boundary, what each field means, who owns it, and what happens when it is invalid or incomplete.

Use it for CSV, JSON, events, webhooks, batch imports/exports, or API payloads. It defines the contract; it does not choose credentials, transport infrastructure, or implementation architecture unless those details affect the contract.

## Gather the minimum context

- What business workflow does this exchange support?
- Who produces and who consumes the data?
- Is the direction inbound, outbound, or bidirectional?
- Is this a one-time migration, periodic sync, event stream, or manual operation?
- What source system owns each material field?
- What is the failure tolerance: reject all, accept partial data, queue for review, or upsert?

## Define the contract

### Interface semantics

State the purpose, producer, consumer, direction, frequency, expected volume, delivery trigger, and versioning policy. Separate the data contract from the transport contract.

### Field table

For every field, specify:

| Field | Meaning | Type | Required | Source of truth | Validation | Example | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |

Include identifier semantics, time zone, currency, null/empty handling, enum values, and nested or repeated values where relevant. Do not describe a field only by its storage column.

### Identity and change behavior

- What combination of fields identifies a record?
- What makes a delivery a duplicate?
- Is the operation create-only, replace, patch, or upsert?
- What happens when the referenced record does not exist?
- Can records arrive out of order or be corrected later?

### Validation and errors

Define the behavior for malformed values, missing required fields, unsupported values, duplicate identities, unknown references, and partial success. Error outputs must let an operator act: record identifier, field, reason, severity, and safe retry guidance.

### Safety and lifecycle

Define limits, PII handling, retention, access boundaries, idempotency, and replay expectations. For files, also specify encoding, delimiter, headers, quoting, line endings, date format, and filename/version convention.

## Required deliverable

Produce a contract with:

1. purpose and scope;
2. interface semantics;
3. field definitions;
4. identity, ownership, and update rules;
5. validation and error model;
6. minimal valid and invalid examples;
7. acceptance criteria;
8. open questions and explicitly deferred decisions.

## Quality bar

A contract is not ready if two independent implementers could reasonably disagree on what a field means, how a duplicate behaves, or what the recipient should do after an error.

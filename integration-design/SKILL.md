---
name: integration-design
description: Design a reliable external data integration from business workflow through onboarding and operations. Use for API, webhook, file, queue, or storage integrations where transport, data contract, sync behavior, ownership, and recovery need to be decided together.
---

# Integration Design

## Overview

Use this skill when an integration request arrives as "connect system A to system B". The goal is to design the repeatable workflow behind the connection, not merely choose an API or transfer mechanism.

This skill coordinates the whole integration shape. Use `data-contract-spec` when the field-level contract needs to be written in detail.

## Start from the business workflow

- Which actor needs what outcome?
- Which system owns the source data and which system acts on it?
- What level of freshness matters to the workflow?
- What should continue to work when the connection is degraded?
- What would make onboarding the second customer or provider cheaper than the first?

## Classify the integration

Describe it across four axes:

1. **Direction:** inbound, outbound, bidirectional, or event notification.
2. **Transport:** API, webhook, file transfer, object storage, queue, or manual upload.
3. **Data shape:** records, files, events, documents, or media.
4. **Lifecycle:** first import, continuous sync, correction/reconciliation, disconnect, and reauthorization.

## Decide the system shape

### Connection and capability

- How are authentication, scopes, credentials, and connection health represented?
- Which capabilities are actually supported by each provider or plan?
- What is visible to the user when authorization is incomplete, stale, or revoked?

### Data ownership and contract

- What is the source of truth per field?
- Which identity mappings are stable and which need provenance or confidence?
- What data is stored locally, cached temporarily, or fetched on demand?
- Is a canonical internal model needed now, later, or not at all?

### Synchronization and recovery

- Which path is webhook, polling, manual, or scheduled?
- How are duplicates, ordering gaps, rate limits, and partial payloads handled?
- What is the idempotency key and the replay/reconciliation strategy?
- How can an operator run a safe narrow recovery?

### Operations and rollout

- Who owns onboarding, monitoring, reauthorization, failure investigation, and backfills?
- Which connection state and freshness signals must be visible?
- What is the smallest end-to-end test that proves the business workflow?
- What metrics show integration health without exposing unnecessary customer data?

## Required design note

Produce:

1. workflow and actors;
2. integration classification;
3. source-of-truth and identity decisions;
4. connection lifecycle and capability matrix;
5. sync, idempotency, failure, and reconciliation model;
6. onboarding and operational runbook outline;
7. first vertical slice, non-goals, and open questions.

## Default bias

Build one provider and one real workflow behind a clear adapter boundary before inventing a universal integration platform. Generalize when a second use case proves where the boundary actually differs.

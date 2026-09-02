---
name: content-migration-playbook
description: Plan and execute a safe migration of posts, articles, media, or user-generated content between systems. Use when migration requires source discovery, identity mapping, media handling, validation, rollback, and an operational rollout rather than a simple bulk copy.
---

# Content Migration Playbook

## Overview

Use this skill when moving content from one system to another. Treat the migration as a product and identity problem, not a text-export problem: content may reference authors, products, categories, media, permissions, links, and historical URLs that need to remain meaningful after the move.

## Discovery first

Before implementing a migrator, determine:

- whether a documented API, export, or feed is available before scraping pages;
- the volume, rate limits, access rules, and source terms;
- the content identity and URL strategy;
- related identities: author, merchant, product, category, tag, collection, or campaign;
- media ownership, transformation, and rehosting rules;
- embedded or linked content that may break after identifiers change; and
- the required historical attributes: publication time, draft state, visibility, permissions, and attribution.

## Define the migration contract

For every entity, specify:

| Source identity | Target identity | Mapping method | Required data | Failure behavior |
| --- | --- | --- | --- | --- |

Do not use a title or display name as the only identity unless the source provides nothing stronger and collisions are acceptable.

## Design phases

1. **Discover** - validate source access, representative data, variants, and volume.
2. **Extract** - collect source records and raw references with controlled pacing.
3. **Normalize** - transform content shape, links, media references, and known source quirks.
4. **Resolve** - map related identities and record unresolved references explicitly.
5. **Load** - create or upsert target records idempotently.
6. **Verify** - compare counts, samples, links, media, author/product coverage, and publication behavior.
7. **Roll out** - run a narrow pilot, monitor, then expand with a recovery plan.

## Failure and recovery rules

- Persist progress so an interrupted run can resume.
- Keep extraction failures separate from mapping failures and target-write failures.
- Do not delete a source-derived record because a related identity is unresolved unless the product contract requires it.
- Prefer a visible unresolved state, skip report, or review queue over silent data loss.
- Make reruns idempotent and distinguish a correction from a duplicate import.
- Plan how to handle a bad transformation after partial publication: unpublish, repair, replay, or rollback.

## Validation

Validate more than total record count:

- representative content variants render correctly;
- authors, products, tags, and internal links resolve as intended;
- media survives and respects rights/retention rules;
- historical timestamps and visibility behave correctly;
- duplicate and partial reruns are safe; and
- operator-facing reports explain skips and failures.

## Deliverable

Produce a migration design with source assessment, identity map, phase plan, sample validation set, rollback/recovery strategy, owner matrix, and go/no-go checklist.

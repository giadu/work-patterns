# work-patterns

Reusable work patterns for engineering judgment, delivery, and AI-assisted execution.

This repository collects a small set of portable workflows that came out of real product and delivery work. The focus is not on model tricks or tool-specific hacks, but on practical patterns that improve how work is scoped, delegated, reviewed, and explained.

Each pattern is meant to be simple, reusable, and grounded in real implementation work.

## Current patterns

- `project-boss-setup` - prepare a project coordination chat with a clear remit, verified sources, and one durable project note across coding agents

- `product-judgment-check` - pressure-test product, domain, and operational decisions before building
- `ai-feature-readiness-check` - assess AI feature evidence, evaluation criteria, autonomy limits, and readiness for a pilot or release
- `delivery-slice` - define the smallest mergeable version of a change
- `delegation-loop` - prepare bounded handoffs for people or agents and verify returned work against agreed outcomes
- `systems-integrity-review` - review implementation integrity across scope, state, data, async work, rollout, and tests
- `data-contract-spec` - define a reviewable contract for imports, exports, files, events, and API payloads
- `integration-design` - turn an external connection request into a reliable workflow, sync, recovery, and onboarding design
- `catalog-crawler-builder` - build catalog crawlers with deliberate identity, variant, validation, and source-access decisions
- `evidence-based-security-questionnaire` - answer B2B security questionnaires from verified evidence without overclaiming controls
- `content-migration-playbook` - plan content, media, and identity migrations with validation and recovery
- `storefront-extension` - extend storefronts safely across DOM lifecycle, interaction, mobile, and analytics boundaries
- `junior-task-drafter` - turn rough context into execution-ready tasks for junior engineers
- `junior-work-review` - review junior designs and implementations with evidence-backed findings and focused coaching
- `task-learning-review` - extract lessons from completed work, propose workflow experiments, and surface optional writing ideas
- `task-closeout` - close merged and deployed work, capture career-safe learning, and clean up authorised task resources across coding agents
- `project-impact-capture` - turn shipped work into reusable evidence for interviews, CVs, and public-safe stories
- `substack-draft-starter` - turn technical observations into voice-preserving, sensitivity-checked writing drafts

## Design principles

- Evidence over confidence
- Scope before abstraction
- Judgment over speed theater
- Portable over tool-specific
- Small workflows, clearly stated

## Structure

```text
work-patterns/
├── README.md
├── .gitignore
└── <pattern>/
    ├── SKILL.md
    ├── agents/
    └── references/
```

## Notes

These patterns use the open Agent Skills format. Their instructions describe outcomes, evidence, required capabilities and boundaries without depending on a particular agent or vendor.

Client-specific tool names, hooks, local paths and personal permissions belong in the user's local setup, outside this repository. A pattern checks the capabilities actually available and explains any missing step rather than assuming a particular tool exists.

Optional UI metadata in `agents/` supports discovery in compatible clients. It is not required to understand or execute a pattern and must not contain the only copy of operational instructions.

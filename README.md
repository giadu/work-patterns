# work-patterns

Reusable work patterns for engineering judgment, delivery, and AI-assisted execution.

This repository collects a small set of portable workflows that came out of real product and delivery work. The focus is not on model tricks or tool-specific hacks, but on practical patterns that improve how work is scoped, delegated, reviewed, and explained.

Each pattern is meant to be simple, reusable, and grounded in real implementation work.

## Current patterns

- `product-judgment-check` - pressure-test product, domain, and operational decisions before building
- `delivery-slice` - define the smallest mergeable version of a change
- `systems-integrity-review` - review implementation integrity across scope, state, data, async work, rollout, and tests
- `data-contract-spec` - define a reviewable contract for imports, exports, files, events, and API payloads
- `integration-design` - turn an external connection request into a reliable workflow, sync, recovery, and onboarding design
- `catalog-crawler-builder` - build catalog crawlers with deliberate identity, variant, validation, and source-access decisions
- `evidence-based-security-questionnaire` - answer B2B security questionnaires from verified evidence without overclaiming controls
- `content-migration-playbook` - plan content, media, and identity migrations with validation and recovery
- `storefront-extension` - extend storefronts safely across DOM lifecycle, interaction, mobile, and analytics boundaries
- `junior-task-drafter` - turn rough context into execution-ready tasks for junior engineers
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

These patterns are written in a Codex skill format because that is a convenient packaging unit, but the underlying ideas are tool-agnostic. They are intended to stay understandable even outside one specific agent or vendor ecosystem.

# work-patterns

Reusable work patterns for engineering judgment, delivery, and AI-assisted execution.

This repository collects a small set of portable workflows that came out of real product and delivery work. The focus is not on model tricks or tool-specific hacks, but on practical patterns that improve how work is scoped, delegated, reviewed, and explained.

Each pattern is meant to be simple, reusable, and grounded in real implementation work.

## Current patterns

- `product-judgment-check` - pressure-test product, domain, and operational decisions before building
- `delivery-slice` - define the smallest mergeable version of a change
- `junior-task-drafter` - turn rough context into execution-ready tasks for junior engineers
- `project-impact-capture` - turn shipped work into reusable evidence for interviews, CVs, and public-safe stories

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

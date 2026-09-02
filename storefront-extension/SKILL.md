---
name: storefront-extension
description: Design and implement a safe extension to a third-party storefront or embedded commerce UI. Use when adding widgets, media, tracking, links, or behavior must coexist with an existing DOM, renderer, carousel, mobile layout, and analytics contract.
---

# Storefront Extension

## Overview

Use this skill when a feature must run inside a storefront or page the team does not fully control. The goal is to add useful behavior without assuming a stable DOM, breaking rendering, duplicating listeners, misreporting analytics, or creating desktop-only behavior.

## Understand the host page

Before implementation, determine:

- the target page types and representative URLs;
- server-rendered versus client-rendered behavior;
- stable root containers and lifecycle/render events;
- desktop/mobile differences;
- the host component or carousel library and its public events;
- existing widgets, accessibility behavior, and analytics conventions; and
- the target item's identity source and fallback behavior.

Do not anchor the implementation to a decorative class name when a semantic root, data attribute, or documented event is available.

## Design for repeated rendering

Storefronts can render the same surface more than once through navigation, filtering, lazy loading, or hydration.

- Scope queries to the intended root.
- Make DOM insertion idempotent.
- Avoid duplicate event listeners and duplicate tracking events.
- Clean up timers, observers, or listeners when the host replaces a surface.
- Keep state tied to stable item identity rather than DOM index alone.

## Preserve host behavior

When extending a carousel, modal, or product page:

- keep main view, thumbnails, navigation, and enlarged view in sync;
- do not assume an inserted element shifts indices the same way in every surface;
- preserve keyboard, focus, touch, and accessibility behavior;
- avoid blocking rendering or main-thread interaction with heavy work; and
- keep failure local so the host product page remains usable.

## Tracking and privacy

Define what event is actually being measured:

- inserted;
- rendered;
- viewable;
- played or interacted with; or
- clicked/conversion-attributed.

Do not report an interaction merely because an element was inserted. Include item, surface, version, and consent context only when needed and permitted.

## Release and validation

Validate at least one positive and one negative item state across desktop and mobile. Check:

- layout and interaction;
- re-render and navigation behavior;
- page performance and console/network errors;
- analytics event semantics;
- missing/unavailable content behavior; and
- rollback or disable path.

## Deliverable

Produce a short implementation note with host assumptions, item identity, lifecycle strategy, DOM/interaction plan, tracking contract, validation matrix, and known limitations.

---
name: catalog-crawler-builder
description: Plan and implement a reliable catalog crawler or importer from public pages or APIs. Use when extracting product and variant data requires source discovery, respectful access, identity decisions, parsing, validation, and a maintainable recovery path.
---

# Catalog Crawler Builder

## Overview

Use this skill when product catalog data must be collected from a public website, feed, or API. The objective is not to scrape as much as possible. It is to obtain the minimum trustworthy catalog data for a defined workflow without creating false product matches, brittle parsing, or unsafe load on the source.

## Clarify the product contract

- What downstream workflow needs the catalog data?
- Is the unit a product, a purchasable variant/SKU, or both?
- Which fields are required: identity, title, image, price, availability, category, URL, or attributes?
- How fresh must the data be, and what should the product show when it is stale?
- Is the crawler a one-time migration, scheduled sync, or on-demand lookup?

## Discover the source safely

Prefer a documented API, feed, structured data, or platform export over HTML parsing when it provides the needed data and is permitted.

When HTML is necessary:

- inspect representative listing and detail pages;
- include variants such as sale, out-of-stock, product-with-variants, and missing-image pages;
- determine whether server HTML is enough or a browser-rendered page is required;
- identify stable semantic selectors, not purely presentational layout hooks;
- respect source terms, robots guidance, rate limits, and conservative request pacing.

## Model identity and extraction deliberately

- Separate page URL, external product ID, variant/SKU ID, and internal reference.
- Do not infer a variant from a title if the source exposes a stable variant identifier.
- Preserve source timestamp and extraction provenance.
- Treat price and availability as contextual observations, not timeless product fields.
- Avoid permissive fallback selectors that quietly capture recommendations, footer content, or unrelated products.

## Build for imperfect source data

- Classify source failures: unavailable page, changed structure, blocked request, malformed data, missing required identifier, and partial extraction.
- Decide whether to skip, retain last known data, queue for review, or stop the run.
- Make processing idempotent and scoped so a retry does not create duplicate products or variants.
- Keep a narrow validation mode that can test selected pages before a full crawl.

## Validate the real extraction contract

At minimum, validate:

- listing discovery returns only intended products;
- detail parsing extracts required fields for representative page variants;
- product and variant identity are stable and correctly scoped;
- sale, availability, and missing-data behavior match the product contract;
- the crawler reports counts, skips, failures, and source changes clearly.

## Deliverable

Produce an implementation note containing the source choice, product/variant model, extraction map, validation cases, access/rate-limit policy, error strategy, and rollout plan. If implementation is requested, start with a small verified source subset before scheduling broad collection.

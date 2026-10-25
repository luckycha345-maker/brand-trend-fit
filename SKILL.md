---
name: brand-trend-fit
description: Match verified trend keywords to a brand's saved product capabilities and natural use cases, plan grounded search seeds, explain relevance, and rank only eligible candidates. Use for product-aware trend research and recommendation filtering, not standalone scraping or content generation.
---

# Brand Trend Fit

Turn a supplied product profile and verifiable trend evidence into explainable, product-relevant recommendations. The invariant is **relevance first, ranking second**: popularity, seed matches and preference memory never turn an unrelated or unconfirmed keyword into an eligible recommendation.

## Establish the product facts

Read the supplied product, capabilities, supported use cases, target audience, region/language, exclusions and optional selected function. Use current explicit capabilities before broad industry labels. Missing or negated capabilities stay unavailable. A declared use case cannot invent a capability. For an unclear profile, ask for the smallest missing fact needed to decide; continue evaluating other candidates.

Plan separate seed groups: explicitly supplied benchmark brands, supported categories and supported scenarios. Benchmarks help discovery; their features and news do not become the user's features. Translate seeds only where their meaning is reliable. Retain each seed's supporting fact.

## Establish what the source actually proves

Use available, authorized connectors, APIs or supplied datasets. This skill bundles no scraper, credentials or paid service. Reuse fresh caches before requesting collection; respect the caller's budgets and collection limits. Avoid exporting private product details to providers when public category terms suffice.

Combine verified regional charts and category-filtered charts when available. Preserve every observation's original keyword, platform, region, chart type, timestamp, ordinal and exact filter scope. A monthly search chart is not a real-time hot-search chart. A source naming a region does not automatically verify every post's language or location.

Search results, popular posts, news headlines, provider-generated topic clusters and Google Trends relative indexes are supplemental evidence, not platform keyword ranks. Keep their ordinal null. If source or rank provenance is uncertain, say so and withhold it from verified-ranked recommendations. Do not substitute one platform's chart for another.

## Decide product relevance before scoring

For each candidate, establish a short chain:

**original keyword → reader need in this context → supported product role → saved capability quote**

Classify:

- `related`: a concrete direct task or natural use-case bridge is grounded in supplied capabilities, without changing the original keyword's meaning.
- `pending`: ambiguity, audience/occasion overlap alone, or a missing product fact prevents a defensible connection. State the missing fact; do not auto-recommend or learn a positive preference.
- `unrelated`: the need conflicts with or has no supported connection to the product, violates an exclusion, or is outside the selected capability.

A creative angle is distinct from an observed trend: Halloween outfit coordination can support nail designs for a nail product, while it does not by itself support a marketing agent. A birthday gathering may support cakes and paper decorations, but a decoration-only query does not automatically support food. Check the object, intended task and audience; distinguish coffee tables from coffee brewing, pet food from pet carriers, and ordinary stretching from medical treatment.

These are examples of the test, not an exhaustive keyword allowlist. For an unseen industry, establish its product role from supplied facts. Do not guess a connection merely to fill a requested count. Return fewer results or a source gap when necessary. See [examples](references/examples.md) when resolving boundary cases.

## Qualify and rank

Semantic relevance is necessary but insufficient. A related candidate with missing, expired or region-conflicting chart evidence cannot enter a verified-ranked recommendation list. Keep it separately as related-but-unverified.

Among eligible candidates, follow the user's ranking mode: product fit, comparable popularity, recency or an explicitly explained combination. Rank ordinals are comparable only within the same platform, region, chart type, collection window and filter set. Group unlike scopes; do not invent a universal heat score. Keep any recommendation position separate from source ordinals.

An exact seed match is not proof of relevance or a 100-point match. Describe scores as heuristic priorities unless independently calibrated; when no validated scoring implementation is supplied, use an explained ordinal priority instead of invented percentages or weights.

Use preference memory only if available and authorized. Partition it by account, product context and relevant region. Recheck old choices against the current profile; cap and explain preference effects. Memory can reorder already eligible similar candidates, never manufacture capabilities or alter platform ranks. This skill does not itself provide persistent storage.

## Deliver and validate

Return the profile summary, typed seeds, evidence gaps, related recommendations, pending cases and rejected cases. Every recommended keyword needs a concrete product-use explanation and capability quote, plus source scope and original ordinal. Show original-language keywords first; translations are secondary explanations. Use [input/output contract](references/contract.md) for application integrations.

Before integration, test multiple industries, direct and bridged positives, ambiguous/homonymous negatives, wrong region, expired evidence, exclusions, function focus and misleading rank-one candidates with exact seeds/high preference. Verify all ranking modes share the eligibility gate, source metadata stays unchanged, and no cross-account preference leaks. Distinguish constructed examples from real-source replay; disclose author-visible annotations and corrections. Small perfect backtests are not production accuracy guarantees.

Report actual collector/model calls, known spend, cache reuse and unknown charges separately. An instruction-only skill does not make collection free or guarantee accuracy. When integrating into an application, implement and test these gates in the application's backend; installing this folder alone does not deploy them or authorize production changes.

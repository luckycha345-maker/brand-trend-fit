# Input/output contract

Map these fields to the host application's schema; this is an example contract, not a provided runtime API.

## Input

- `profile`: product name, explicit capabilities, use cases, target audience, selected capability if any, excluded topics, target region and language. Mark unknowns rather than filling them in.
- `seedInputs`: optional declared benchmarks, categories and scenarios. Keep product facts separate from suggested seeds.
- `observations`: original keyword; platform; provider/source URL; signal type; chart type; region; collection time; expiry; original rank or null; exact filter criteria; measurement period; source-verification status. Keep separate observations for the same term in different charts.
- `preferences`: optional authorized account/context-scoped prior selections, bounded by the host implementation. Never require private identifiers in shared/public output.
- `rankingMode` and `budget`: user's intended ordering and authorized collection/model budget, if supplied.

## Output

```json
{
  "profileSummary": {"capabilities": [], "unknowns": []},
  "typedSeeds": {"benchmarkBrands": [], "categories": [], "scenarios": []},
  "recommendations": [],
  "relatedButUnverified": [],
  "pending": [],
  "rejected": [],
  "sourceGaps": [],
  "costs": {"collectorCalls": 0, "modelCalls": 0, "knownSpend": null, "cacheHits": 0}
}
```

Each recommendation includes:

- `keyword`: unmodified original term; optional `translation` is explanatory only.
- `decision`: related; `eligible`: true only after relevance, source, region and freshness gates.
- `association`: reader need, product role, concrete creative angle where applicable, verbatim supplied capability quote and relationship type (direct/extension).
- `observations`: all original source ranks and exact scopes; never overwrite them with recommendation order.
- `priority`: explained ordinal, or a host-provided validated heuristic score clearly labeled as such; never a probability by implication.
- `preferenceContribution`: actual bounded contribution, or unavailable; never fabricate memory.

Pending/rejected entries explain the missing fact or conflict and have no automatic recommendation priority. Related-but-unverified entries explain the evidence gap. Unavailable cost is null, not zero. Collection windows/filter sets must match before comparing ordinals. If they do not, expose separate groups and explain any presentation order.

Application pseudocode:

```text
for each candidate:
    decision = assess_current_product_connection(candidate, profile)
    if decision != related:
        withhold(candidate)
    elif not verified_fresh_region_correct_evidence(candidate):
        related_but_unverified(candidate)
    else:
        eligible.append(candidate_with_source_and_product_explanation)
rank(eligible, user_mode, exact_source_scopes, authorized_bounded_preferences)
```

This pseudocode documents the gate; no classifier or storage backend is supplied by this repository.

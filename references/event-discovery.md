# Fast-moving event discovery

Use this mode for breaking stories, local incidents or emerging topics whose useful lifetime is shorter than a daily/monthly trend chart. It supplements chart-based research without inventing a chart position.

## Timely sources and budgets

Choose authorized sources based on measured publication/indexing delay, supported locality/language, incremental queries, licensing and actual account prices. Potential inputs include provider-supported regional social trends, relevant official announcements, publisher feeds and news/search APIs. A city name in a query does not establish the provider's geographic scope. Never call a third-party search order an official social trend rank.

Prefer shared per-region public ingestion to one paid poll per user. A reasonable test configuration is source checks every3–5 minutes where allowed, with deduplication and event-triggered evidence lookup. This is an operator-selected experiment, not a latency SLA. Sparse/slow sources remain slow even with frequent polling. Honor an explicit budget cap, rate limits and backoff; stop paid enrichment at the cap and expose the gap. Do not start a recurring job or buy a plan merely because this reference exists.

## Resolve the event

For ambiguous names such as Barcelona, resolve city/region, football club, named organization or other entity before matching product use. Record:

- Original term, detected entity, event description and supported geographic scope.
- Source URL/provider and source publication time, event occurrence time when available, first-seen time and last-checked time separately.
- Source-specific verification state, original chart observation if any, and expiry/recheck time.

Normalize timestamps while preserving source timezone evidence. Do not silently equate updated-page time with event time. Deduplicate syndicated copies and reshares; an old event resurfacing is not a new incident. Prefer a relevant authoritative source or independent corroboration. Distinguish confirmed facts, reported claims and unresolved uncertainty.

## Match and present

Run the same product relevance gate against the actual event context, not merely its trending entity name. A football win might support an explicitly offered fan product; it does not automatically support an AI marketing tool. A capability-relevant product launch may support a software comparison if the supplied product facts justify the connection. Unknown details stay pending.

Keep eligible event signals in a separate, clearly labeled event-discovery view unless official chart evidence independently qualifies them for a verified-ranked list. For event-only evidence use originalRank=null. Explain any recency, velocity or confidence indicators as application signals, not official ranks; never manufacture volume from search samples. Original words remain primary, translations secondary.

## Validate freshness and costs

Test recent real events and deliberately old/resurfaced stories, ambiguous place/team names, conflicting timestamps, duplicate coverage, unrelated viral incidents and source outages. Measure source-publication-to-first-seen latency plus event-to-publication delay where knowable. Report median and tail latency, coverage gaps, false positives and product relevance separately; polling cadence alone is not a performance result.

Estimate requests as regions × queries per region × checks per day × days, then add actual event-triggered enrichment. Include free allowances only where actually available to the account, and keep social API, search, model and infrastructure costs separate. Share fresh public evidence across users while keeping private profiles and preference memory partitioned. Do not report an untested design as a deployed real-time capability.

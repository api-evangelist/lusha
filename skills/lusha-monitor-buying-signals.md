---
name: Monitor buying signals for a set of accounts
description: Enumerate the supported signal types, pull raw signal events or an aggregate momentum score for up to 100 entities, and narrow company signals with the filter-value endpoints.
api: openapi/lusha-signals-api-openapi.yml
operations: [getContactSignalTypes, getCompanySignalTypes, getCompanySignalFilters, getCompanySignalFilterValues, getContactSignals, getCompanySignals, getCompanySignalScores, getContactSignalScores]
generated: '2026-08-13'
method: generated
source: openapi/lusha-signals-api-openapi.yml + changelog/lusha-changelog.yml
---

# Monitor buying signals

Signals are dated real-world events attached to a contact or a company. You can read them as a raw event
list, or as a single aggregate momentum score per entity.

## Steps

1. **Enumerate signal types (free).** `getContactSignalTypes` (`GET /v3/contacts/signals/types`) returns
   the contact set — `promotion`, `companyChange`, `allSignals`. `getCompanySignalTypes`
   (`GET /v3/companies/signals/types`) returns the much larger company set: headcount increase/decrease
   over 1m/3m/6m/12m, `surgeInHiring` (and by department / by location), website traffic up/down, IT spend
   up/down, the news classes (`riskNews`, `commercialActivityNews`, `corporateStrategyNews`,
   `financialEventsNews`, `peopleNews`, `marketIntelligenceNews`, `productActivityNews`) and
   `linkedinActivityIntent`.
2. **Discover company signal filters (free).** `getCompanySignalFilters`
   (`GET /v3/companies/signals/filters`) lists the filter types and whether each requires a query;
   `getCompanySignalFilterValues` (`GET /v3/companies/signals/filters/{filterType}`) returns the valid
   values — including the Bombora `intentCategories` list used to narrow `linkedinActivityIntent`.
3. **Pull raw events.** `getContactSignals` (`POST /v3/contacts/signals`) or `getCompanySignals`
   (`POST /v3/companies/signals`) with up to 100 ids, a `signalTypes` array (or `allSignals`), an optional
   `startDate`, and `maxResultsPerSignal`. Pass `tableId` to also write matches into a table.
4. **Or score instead of listing.** `getCompanySignalScores` (`POST /v3/companies/signal-score`) and
   `getContactSignalScores` (`POST /v3/contacts/signal-score`) return a `signalScore` between 0 and 1,
   the active `signalTypes`, and a `noActiveSignals` flag — up to 100 entities per call. Use this to rank
   a list; use step 3 when you need the events themselves.

## Rules

- Billing is per matched signal per result, via the `showSignalsContact` / `showSignalsCompany` actions.
  A wide `allSignals` query over 100 companies can charge far more than a targeted `signalTypes` array.
- `linkedinActivityIntent` carries two hard caps the API enforces regardless of what you pass:
  `startDate` is clamped to a trailing 90-day window, and `maxResultsPerSignal` is clamped to 50 per
  company. `activitySummary` is AI-generated and never contains the raw post text.
- Per-item outcomes on the scoring endpoints: `NOT_FOUND` (identifier did not resolve) and `NO_SCORE`
  (resolved, but no score). Treat them differently — `NO_SCORE` is a real answer.
- `getContactSignalScores` returns a **retryable `502`** when the identity-resolution provider is out,
  rather than masking it as `NOT_FOUND`. Retry with backoff; do not treat it as "person not found".
- For continuous monitoring, subscribe to webhooks instead of polling — see the webhook skill.

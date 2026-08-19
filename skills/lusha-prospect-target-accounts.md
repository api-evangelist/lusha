---
name: Build a target account and contact list with Lusha Prospecting
description: Discover valid filter values first, then run filter-based company and contact prospecting, page through results without duplicates, and enrich only the shortlist.
api: openapi/lusha-prospecting-api-openapi.yml
operations: [getCompanyFilterTypes, getCompanyFilterValues, getContactFilterTypes, getContactFilterValues, prospectingCompanies, prospectingContacts, enrichContacts, enrichCompanies]
generated: '2026-08-13'
method: generated
source: openapi/lusha-*-api-openapi.yml + conventions/lusha-conventions.yml
---

# Build a target list with Prospecting

Prospecting is filter-based search over Lusha's whole database. Filter values are **enumerated by the
API** — do not guess industry names, seniority ids or technology labels; look them up.

Prospecting and Filters are **Scale-plan** endpoints. On a self-service plan they return `403`.

## Steps

1. **Discover the filter surface (free).** `getCompanyFilterTypes` (`GET /v3/companies/prospecting/filters`)
   and `getContactFilterTypes` (`GET /v3/contacts/prospecting/filters`) list the available filter types
   and whether each needs a search query.
2. **Resolve filter values (free).** `getCompanyFilterValues`
   (`GET /v3/companies/prospecting/filters/{filterType}`) and `getContactFilterValues`
   (`GET /v3/contacts/prospecting/filters/{filterType}`) return the valid values for one filter type.
   These discovery calls charge no credits — use them freely, cache the results.
3. **Prospect companies.** `prospectingCompanies` (`POST /v3/companies/prospecting`) with
   `filters.companies.include` (names, domains, locations, sizes, revenues, technologies, industries,
   intentTopics, signals) and `pagination: { page, size }`. Results are previews with `has`/`canReveal`.
4. **Prospect contacts.** `prospectingContacts` (`POST /v3/contacts/prospecting`) with
   `filters.contacts` (jobTitles, seniorityIds, departments, countries, locations, existingDataPoints,
   signals) and optionally `filters.companies` to constrain to the accounts from step 3.
5. **Page safely.** The response returns a `dedupeSessionId`; pass it back on the next page so you do not
   receive the same entities twice. An expired or invalid session returns `410 Gone` — start a new search
   rather than retrying the same id.
6. **Persist (optional).** Pass `tableId` on a prospecting call to write matching results straight into an
   existing Lusha table (see the Tables operations). The response `tableWrite` block reports
   `added`, `alreadyPresent`, `rowsCharged` and `creditsCharged`.
7. **Enrich the shortlist only.** Take the ids you actually want and call `enrichContacts` /
   `enrichCompanies` with a narrow `reveal` list. Do not enrich a whole prospecting page.

## Rules

- Filter/type discovery is free; every prospecting, search, enrich or signal call spends credits, with a
  1-credit floor per request even on an empty result.
- Bulk economics: 1 credit per 1-25 results returned, max 100 entities per request — batch deliberately.
- `existingDataPoints` on contact filters lets you pre-filter to profiles that already have the data point
  you intend to reveal, which is the cheapest way to raise reveal hit rate.
- There is no idempotency key. Re-running a prospecting page after a timeout can re-charge; use the
  `dedupeSessionId` and your own request log instead.

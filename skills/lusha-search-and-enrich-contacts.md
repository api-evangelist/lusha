---
name: Search and enrich a contact with Lusha
description: Resolve a person from an email, LinkedIn URL or name + company, then spend credits deliberately to reveal their email and phone.
api: openapi/lusha-search-api-openapi.yml
operations: [searchContacts, enrichContacts, searchAndEnrichContacts, getAccountUsage]
generated: '2026-08-13'
method: generated
source: openapi/lusha-*-api-openapi.yml + conventions/lusha-conventions.yml + plans/lusha-plans-pricing.yml
---

# Search and enrich a contact

Lusha's v3 API is deliberately two-phase: **search returns a non-PII preview, enrich spends credits.**
Never call enrich blind — search first, read `canReveal`, then reveal only what you need.

## Before you start

- Base URL `https://api.lusha.com`. Every request needs the header `api_key: <your key>` — **not**
  `Authorization: Bearer` (the help-centre 401 article says Bearer; the OpenAPI and API reference say
  `api_key`, and the spec is authoritative).
- Minimum **1 credit per request**, even when nothing comes back. Email = 1 credit, phone = 5 credits,
  company info = 1 credit. A data point already revealed for a contact is not charged again.
- Max 100 contacts per request.

## Steps

1. **Check headroom** — `getAccountUsage` (`GET /v3/account/usage`) returns credits total/used/remaining
   plus the minute, hourly and daily rate-limit tiers. Do this once per session, not per call.
2. **Search** — `searchContacts` (`POST /v3/contacts/search`). Identify each contact by exactly one of:
   `id`, `linkedinUrl`, `email`, or `firstName` + `lastName` + (`companyName` | `companyDomain`).
   Pass `clientReferenceId` on each item so you can match results back to your own records.
   The response gives `id`, `has` (what exists) and `canReveal` (what can be unlocked, with the credit
   cost per field). Nothing PII comes back at this stage.
3. **Decide** — only proceed for contacts whose `canReveal` actually contains the field you need.
   Revealing a phone costs 5x an email; if email is enough, ask for email only.
4. **Enrich** — `enrichContacts` (`POST /v3/contacts/enrich`) with the `ids` from step 2 and a `reveal`
   array naming just the fields you want (e.g. `["emails"]`). Optionally set `waterfallEnabled` /
   `waterfallReveal` to fall through to third-party providers when Lusha has no match — but note those
   fields are billed at the *provider's* rate, which can be higher than a Lusha reveal.
5. **Read the billing block** — every response carries `billing.creditsCharged` and
   `billing.resultsReturned`. Log it; it is the only spend record you get inline.

**Shortcut:** `searchAndEnrichContacts` (`POST /v3/contacts/search-and-enrich`) collapses steps 2-4 into
one call. Use it only when you have already decided to pay — it removes the `canReveal` checkpoint.

## Rules

- **No idempotency.** There is no `Idempotency-Key` header on any Lusha operation. A retried enrich call
  is a new call. Deduplicate on your side before retrying, and rely on the "already revealed is not
  re-charged" rule rather than on request replay safety.
- **Rate limits are three simultaneous windows.** Read `x-minute-requests-left`,
  `x-hourly-requests-left` and `x-daily-requests-left` on every response and stop before you hit zero.
  There is no `Retry-After`; on `429` back off exponentially from 1s, doubling, capped at 60s.
- **Errors**: `402` = out of credits, `403` = the endpoint is not in your plan (self-service plans reach
  enrichment only), `451` = blocked for GDPR reasons. Error bodies are
  `{ "statusCode", "message", "errors"? }` — not RFC 9457 problem+json.
- Per-item failures come back inside the results array as an `error` object; a `200` does not mean every
  item resolved.

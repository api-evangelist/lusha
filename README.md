# Lusha (lusha)

Lusha is a B2B sales intelligence platform offering verified contact and company data. It exposes four REST APIs (Enrichment, Prospecting, Signals, Lookalike) plus an OpenAPI specification. Authentication is via API key generated in the dashboard.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/lusha/refs/heads/main/apis.yml)

## Type
- **x-type:** company

## Tags
- Sales Intelligence, B2B, Enrichment, Contact Data, Prospecting, Intent

## Timestamps
- **Created:** 2026-05-08
- **Modified:** 2026-05-08

## APIs

### Lusha Enrichment API
Adds verified contact (email, phone) and company (firmographic) details to records given identifiers (email, LinkedIn, domain).
- **Base URL:** `https://api.lusha.com`
- **Docs:** https://docs.lusha.com/apis

### Lusha Prospecting API
Search and filter contacts/companies by job title, seniority, industry, geography, and other firmographic/persona filters.
- **Base URL:** `https://api.lusha.com`
- **Docs:** https://docs.lusha.com/apis

### Lusha Signals API
Real-world signals (job changes, hiring, momentum) that affect outreach timing.
- **Base URL:** `https://api.lusha.com`
- **Docs:** https://docs.lusha.com/apis

### Lusha Lookalike API
Discover similar accounts and buyers based on a seed list.
- **Base URL:** `https://api.lusha.com`
- **Docs:** https://docs.lusha.com/apis

## Common Properties
- [Website](https://www.lusha.com/)
- [Developer Portal](https://docs.lusha.com/)
- [OpenAPI](https://docs.lusha.com/apis/openapi)
- [Plans](plans/lusha-plans-pricing.yml) — reconciled (seat + credits; tiered)
- [RateLimits](rate-limits/lusha-rate-limits.yml) — partial (plan-based credits; RPS not on landing page)
- [FinOps](finops/lusha-finops.yml) — reconciled (FOCUS-aligned)

## Maintainers
**FN:** Kin Lane

**Email:** kin@apievangelist.com

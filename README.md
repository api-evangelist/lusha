# Lusha (lusha)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Lusha is a B2B sales intelligence platform offering verified contact and company data. It exposes four REST APIs (Enrichment, Prospecting, Signals, Lookalike) plus an OpenAPI specification. Authentication is via API key generated in the dashboard.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/lusha/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/lusha/refs/heads/main/apis.yml)

## Tags

- Sales Intelligence
- B2B
- Enrichment
- Contact Data
- Prospecting
- Intent

## Timestamps

- **Created:** 2026-05-08
- **Modified:** 2026-05-08

## APIs

### Lusha Enrichment API

Adds verified contact (email, phone) and company (firmographic) details to records given identifiers (email, LinkedIn, domain).

- **Human URL:** [https://docs.lusha.com/apis](https://docs.lusha.com/apis)
- **Base URL:** `https://api.lusha.com`

#### Tags

- Enrichment
- Contacts
- Companies

#### Properties

- [Documentation](https://docs.lusha.com/apis)
- [OpenAPI](https://docs.lusha.com/apis/openapi) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/lusha.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lusha.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Lusha Prospecting API

Search and filter contacts/companies by job title, seniority, industry, geography, and other firmographic/persona filters.

- **Human URL:** [https://docs.lusha.com/apis](https://docs.lusha.com/apis)
- **Base URL:** `https://api.lusha.com`

#### Tags

- Prospecting
- Search

#### Properties

- [Documentation](https://docs.lusha.com/apis)
- [Postman Collection](collections/lusha.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lusha.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Lusha Signals API

Real-world signals (job changes, hiring, momentum) that affect outreach timing.

- **Human URL:** [https://docs.lusha.com/apis](https://docs.lusha.com/apis)
- **Base URL:** `https://api.lusha.com`

#### Tags

- Intent
- Signals

#### Properties

- [Documentation](https://docs.lusha.com/apis)
- [Postman Collection](collections/lusha.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lusha.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Lusha Lookalike API

Discover similar accounts and buyers based on a seed list.

- **Human URL:** [https://docs.lusha.com/apis](https://docs.lusha.com/apis)
- **Base URL:** `https://api.lusha.com`

#### Tags

- ABM
- Lookalike

#### Properties

- [Documentation](https://docs.lusha.com/apis)
- [Postman Collection](collections/lusha.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/lusha.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/lusha-oss)
- [LinkedIn](https://www.linkedin.com/company/lushadata)
- [Website](https://www.lusha.com/)
- [Developer Portal](https://docs.lusha.com/)
- [OpenAPI](https://docs.lusha.com/apis/openapi) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Plans](plans/lusha-plans-pricing.yml)
- [Rate Limits](rate-limits/lusha-rate-limits.yml)
- [Fin Ops](finops/lusha-finops.yml)
- [L L Ms Txt](https://docs.lusha.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

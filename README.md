# Lusha

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Lusha is a B2B sales-intelligence platform that sells verified contact and company data, buying signals and AI recommendations to revenue teams. Its v3 REST API at api.lusha.com exposes 58 operations across thirteen resource families — Search, Enrich, Search & Enrich, Prospecting, Lookalikes, Buying Group, Contacts Tables, Companies Tables, Signals, Website Visits, Filters, Webhooks and Account — behind a single `api_key` header credential, on a search-then-enrich pattern where previews are free of PII and reveals spend credits. Lusha also ships a first-party hosted MCP server at mcp.lusha.com with 22 tools, OAuth 2.1 discovery and official Claude, ChatGPT and Codex connectors, plus HMAC-signed webhooks for real-time signal delivery.

**Areas:** Sales Intelligence · B2B · Data Enrichment · Contact Data · Prospecting · Intents · Signals · Lookalikes · Webhook · MCP

## Lusha on APIs.io

Everything profiled for Lusha is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/lusha/](https://apis.io/providers/lusha/)** — or go straight to one of the APIs or properties below.

### APIs (19)

- [Lusha Search API](https://apis.io/apis/lusha/lusha-search-api/) — Find contacts or companies from known identifiers — contact id, LinkedIn URL, email or name + company; company id, name or domain — and return a non-PII…
- [Lusha Enrich API](https://apis.io/apis/lusha/lusha-enrich-api/) — Reveal full contact and company profiles by Lusha id, with an explicit `reveal` list controlling which fields are unlocked and charged, and optional…
- [Lusha Search & Enrich API](https://apis.io/apis/lusha/lusha-search-enrich-api/) — Resolve an identifier and return the fully revealed contact or company record in a single call, collapsing the two-phase search-then-enrich pattern where…
- [Lusha Prospecting API](https://apis.io/apis/lusha/lusha-prospecting-api/) — Filter-based search across Lusha's contact and company database — job title, seniority, department, location, company size, revenue, industry, technology…
- [Lusha Lookalikes API](https://apis.io/apis/lusha/lusha-lookalike-api/) — AI-powered similarity search that expands a seed list of contacts or companies into comparable profiles, with exclusion lists, a dedupe session id and…
- [Lusha Buying Group API](https://apis.io/apis/lusha/lusha-buying-group-api/) — Persona classification over a fixed set of up to 25 named accounts — labels each returned contact decision_maker, potential_champion or end_user with a…
- [Lusha Signals API](https://apis.io/apis/lusha/lusha-signals-api/) — Real-world activity data for contacts and companies — promotions and job changes on the contact side; headcount movement, hiring surges, web traffic, IT…
- [Lusha Website Visitors API](https://apis.io/apis/lusha/lusha-website-visits-api/) — Companies ranked by website-visit signals for domains you track, filtered by score band, visitor country, session counts, unique visitors, high-intent…
- [Lusha Filters API](https://apis.io/apis/lusha/lusha-filters-api/) — Filter discovery for prospecting — enumerates the available filter types and the valid values for each, so callers never guess industry labels, seniority…
- [Lusha Contacts Tables API](https://apis.io/apis/lusha/lusha-contacts-tables-api/) — Persist, organise and enrich contacts in reusable tables with dynamic columns — create, list, read, update, delete tables; add and remove up to 500 entity…
- [Lusha Companies Tables API](https://apis.io/apis/lusha/lusha-companies-tables-api/) — The company-side twin of Contacts Tables — persist and enrich company working sets in tables with dynamic columns, capped at 50,000 entities per table and…
- [Lusha Webhooks API](https://apis.io/apis/lusha/lusha-webhooks-api/) — Subscription management for real-time signal callbacks — bulk create and delete up to 25 items per request, account-level HMAC-SHA256 secret with rotation,…
- [Lusha Account API](https://apis.io/apis/lusha/lusha-account-api/) — Credit balance, plan information, per-action credit pricing and the live rate-limit tiers for the minute, hourly and daily windows.
- [Lusha MCP Server](https://apis.io/apis/lusha/mcp/) — First-party hosted Model Context Protocol server exposing 22 Lusha tools over streamable HTTP. Authenticates with OAuth 2.1 (scope `mcp`, PKCE S256, dynamic…
- [Lusha Account Management API](https://apis.io/apis/lusha/lusha-account-management-api/) — Manage your account and monitor usage. Use this endpoint to: - Monitor credit usage - Understand consumption patterns - Align API usage with plan limits -…
- [Lusha Company Filters API](https://apis.io/apis/lusha/lusha-company-filters-api/) — Available filters for company searches
- [Lusha Contact Filters API](https://apis.io/apis/lusha/lusha-contact-filters-api/) — Available filters for contact searches
- [Lusha Enrichment API](https://apis.io/apis/lusha/lusha-enrichment-api/) — **What is enrichment?** Enrichment is the process of adding missing or updated data to existing contact or company records. Use enrichment to: - Complete…
- [Lusha Prospecting - Search & Enrich API](https://apis.io/apis/lusha/lusha-prospecting-search-enrich-api/) — With Lusha's Prospecting API, you can query Lusha's extensive database based on specific criteria (such as job title, seniority, location, and more) to…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Lusha Webhooks](https://apis.io/asyncapis/lusha/lusha-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [lusha](https://apis.io/servers/lusha/lusha/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Lusha Agentic Access](https://apis.io/agentic-access/lusha/lusha-agentic-access/)

#### Collections (13)

Postman and Open Collection request collections.

- [Lusha API Documentation Account API](https://apis.io/collections/lusha/open-lusha-account-api/)
- [Lusha API Documentation Buying Group API](https://apis.io/collections/lusha/open-lusha-buying-group-api/)
- [Lusha API Documentation Companies Tables API](https://apis.io/collections/lusha/open-lusha-companies-tables-api/)
- [Lusha API Documentation Contacts Tables API](https://apis.io/collections/lusha/open-lusha-contacts-tables-api/)
- [Lusha API Documentation Enrich API](https://apis.io/collections/lusha/open-lusha-enrich-api/)
- [Lusha API Documentation Filters API](https://apis.io/collections/lusha/open-lusha-filters-api/)
- [Lusha API Documentation Lookalikes API](https://apis.io/collections/lusha/open-lusha-lookalikes-api/)
- [Lusha API Documentation Prospecting API](https://apis.io/collections/lusha/open-lusha-prospecting-api/)
- [Lusha API Documentation Search API](https://apis.io/collections/lusha/open-lusha-search-api/)
- [Lusha API Documentation Search & Enrich API](https://apis.io/collections/lusha/open-lusha-search-enrich-api/)
- [Lusha API Documentation Signals API](https://apis.io/collections/lusha/open-lusha-signals-api/)
- [Lusha API Documentation Webhooks API](https://apis.io/collections/lusha/open-lusha-webhooks-api/)
- [Lusha API Documentation Website Visits API](https://apis.io/collections/lusha/open-lusha-website-visits-api/)

#### Overlays (31)

OpenAPI overlays, including conversational phrasing for each operation.

- [Lusha Account Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-account-api-phrasing-overlay/)
- [Lusha Account Management Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-account-management-api-phrasing-overlay/)
- [Lusha Account Overlay](https://apis.io/overlays/lusha/lusha-account-overlay/)
- [Lusha Buying Group Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-buying-group-api-phrasing-overlay/)
- [Lusha Buying Group Overlay](https://apis.io/overlays/lusha/lusha-buying-group-overlay/)
- [Lusha Companies Tables Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-companies-tables-api-phrasing-overlay/)
- [Lusha Companies Tables Overlay](https://apis.io/overlays/lusha/lusha-companies-tables-overlay/)
- [Lusha Company Filters Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-company-filters-api-phrasing-overlay/)
- [Lusha Contact Filters Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-contact-filters-api-phrasing-overlay/)
- [Lusha Contacts Tables Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-contacts-tables-api-phrasing-overlay/)
- [Lusha Contacts Tables Overlay](https://apis.io/overlays/lusha/lusha-contacts-tables-overlay/)
- [Lusha Enrich Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-enrich-api-phrasing-overlay/)
- [Lusha Enrich Overlay](https://apis.io/overlays/lusha/lusha-enrich-overlay/)
- [Lusha Enrichment Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-enrichment-api-phrasing-overlay/)
- [Lusha Filters Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-filters-api-phrasing-overlay/)
- [Lusha Filters Overlay](https://apis.io/overlays/lusha/lusha-filters-overlay/)
- [Lusha Lookalikes Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-lookalikes-api-phrasing-overlay/)
- [Lusha Lookalikes Overlay](https://apis.io/overlays/lusha/lusha-lookalikes-overlay/)
- [Lusha Prospecting Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-prospecting-api-phrasing-overlay/)
- [Lusha Prospecting Overlay](https://apis.io/overlays/lusha/lusha-prospecting-overlay/)
- [Lusha Prospecting Search Enrich Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-prospecting-search-enrich-api-phrasing-overlay/)
- [Lusha Search Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-search-api-phrasing-overlay/)
- [Lusha Search Enrich Api Phrasing Overlay](https://apis.io/overlays/lusha/lusha-search-enrich-api-phrasing-overlay/)
- [Lusha Search Enrich Overlay](https://apis.io/overlays/lusha/lusha-search-enrich-overlay/)
- [Lusha Search Overlay](https://apis.io/overlays/lusha/lusha-search-overlay/)
- …and 6 more published on APIs.io

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Lusha Authentication](https://apis.io/security/lusha/lusha-authentication/)
- [Lusha Domain Security](https://apis.io/security/lusha/lusha-domain-security/)
- [Lusha Trust Center](https://apis.io/security/lusha/lusha-trust-center/)
- [Lusha Vulnerability Disclosure](https://apis.io/security/lusha/lusha-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Lusha Scopes](https://apis.io/scopes/lusha/lusha-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Lusha Plans Pricing](https://apis.io/plans/lusha/lusha-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Lusha Rate Limits](https://apis.io/rate-limits/lusha/lusha-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Lusha Finops](https://apis.io/finops/lusha/lusha-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.lusha.com/)
- [Documentation](https://docs.lusha.com/apis/openapi)
- [Getting started](https://docs.lusha.com/guides/advanced-topics/new-getting-started)
- [API reference](https://docs.lusha.com/apis/openapi)
- [Pricing](https://www.lusha.com/pricing/)
- [Support](https://info.lusha.com/)
- [Changelog](https://docs.lusha.com/changelog)
- [Blog](https://www.lusha.com/blog/)
- [Security](https://www.lusha.com/.well-known/security.txt)
- [Compliance](https://www.lusha.com/trust-center)
- [Terms of service](https://lusha.com/legal/terms)
- [Privacy policy](https://lusha.com/legal/privacy-notice/)
- [GitHub](https://github.com/lusha-oss)
- [Status](https://status.lusha.com)

## API Evangelist rating

**Kin Score 71.2** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 62.0 |
| Contract governance | 18.2 |
| Operational transparency | 86.8 |
| Developer ergonomics | 63.7 |
| Access clarity | 85.5 |

**Agent readiness 60.7** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | verified |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | mostly |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/lusha/](https://apis.io/providers/lusha/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Lusha: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/lusha/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

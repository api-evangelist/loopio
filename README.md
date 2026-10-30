# Loopio

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

Loopio is a Toronto-based response management platform used by teams to answer RFPs, RFIs, DDQs, and security questionnaires from a governed, reusable content Library. It publishes a public REST API — the Loopio Public API v2 at https://api.loopio.com/data/v2 — documented on a Stoplight developer portal at developer.loopio.com, with a 96-operation OpenAPI 3.0.1 contract covering Library Entries, Projects, Project Entries, Sections and subSections, Custom Project Fields, Merge Variables, Compliance Sets, Project Templates, Stacks, Tags, Teams, Users, Roles, Files, CRM opportunity links, asynchronous task status, and webhook subscriptions. Authentication is OAuth 2.0 client credentials against https://api.loopio.com/oauth2/access_token with 22 in-spec scopes, and the authorization server publishes RFC 8414 and RFC 9728 discovery documents that advertise a wider 51-scope surface including SCIM user/group provisioning and MCP tool/prompt/resource scopes.

**Areas:** Company · RFP · Proposals · Response Management · Content Library · Sales Enablement · Questionnaire · Compliance · Collaboration · Documents · Webhook · Software-as-a-Service

## Loopio on APIs.io

Everything profiled for Loopio is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/loopio/](https://apis.io/providers/loopio/)** — or go straight to one of the APIs or properties below.

### APIs (15)

- [Loopio Asynchronous API](https://apis.io/apis/loopio/loopio-asynchronous-api/) — An asynchronous endpoint
- [Loopio CRM API](https://apis.io/apis/loopio/loopio-crm-api/) — The CRM API from Loopio — 2 operation(s) for crm.
- [Loopio Custom Project Fields API](https://apis.io/apis/loopio/loopio-custom-project-fields-api/) — Create and manage Custom Project Fields
- [Loopio Customers API](https://apis.io/apis/loopio/loopio-customers-api/) — Get information about Customer instances
- [Loopio Files API](https://apis.io/apis/loopio/loopio-files-api/) — Manage Loopio files
- [Loopio Library Entries API](https://apis.io/apis/loopio/loopio-library-entries-api/) — Create and manage Library Entries
- [Loopio Merge Variables API](https://apis.io/apis/loopio/loopio-merge-variables-api/) — Reusable Library/Project-wide variables
- [Loopio Project Templates API](https://apis.io/apis/loopio/loopio-project-templates-api/) — Get Information about Project Templates
- [Loopio Projects API](https://apis.io/apis/loopio/loopio-projects-api/) — Create and manage Projects
- [Loopio Roles API](https://apis.io/apis/loopio/loopio-roles-api/) — The Roles API from Loopio — 2 operation(s) for roles.
- [Loopio Stacks API](https://apis.io/apis/loopio/loopio-stacks-api/) — View accessible stacks or Library structure
- [Loopio Tags API](https://apis.io/apis/loopio/loopio-tags-api/) — Create and manage Tags
- [Loopio Teams API](https://apis.io/apis/loopio/loopio-teams-api/) — Get Information about Teams
- [Loopio Users API](https://apis.io/apis/loopio/loopio-users-api/) — Create and manage Users
- [Loopio Webhooks API](https://apis.io/apis/loopio/loopio-webhooks-api/) — Create & Manage webhook subscriptions

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Loopio Events Webhooks](https://apis.io/asyncapis/loopio/loopio-events-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [loopio-mcp.yml](https://apis.io/servers/loopio/loopio-mcp-yml/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Loopio Openapi Overlay](https://apis.io/overlays/loopio/loopio-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Loopio Authentication](https://apis.io/security/loopio/loopio-authentication/)
- [Loopio Domain Security](https://apis.io/security/loopio/loopio-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Loopio Scopes](https://apis.io/scopes/loopio/loopio-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Loopio Plans Pricing](https://apis.io/plans/loopio/loopio-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Loopio Rate Limits](https://apis.io/rate-limits/loopio/loopio-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://loopio.com/)
- [Documentation](https://developer.loopio.com/docs/loopio-api/c56ffe1fdae3e-getting-started-with-the-loopio-api)
- [Getting started](https://developer.loopio.com/docs/loopio-api/c56ffe1fdae3e-getting-started-with-the-loopio-api)
- [API reference](https://developer.loopio.com/docs/loopio-api/68a341c676710-loopio)
- [Pricing](https://loopio.com/pricing/)
- [Support](https://support.loopio.com/hc/en-us)
- [Blog](https://loopio.com/blog/)
- [Compliance](https://loopio.com/legal/compliance-statement/)
- [Terms of service](https://loopio.com/legal/)
- [Privacy policy](https://loopio.com/legal/privacy/)
- [Status](https://www.loopiostatus.com/)

## API Evangelist rating

**Kin Score 30.2** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 56.6 |
| Contract governance | 18.2 |
| Operational transparency | 23.7 |
| Developer ergonomics | 18.5 |
| Access clarity | 0.0 |

**Agent readiness 47.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 26.5** — Education & Research

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/loopio/](https://apis.io/providers/loopio/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Loopio: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/loopio/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

# Guidewheel

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

Guidewheel is a FactoryOps platform for manufacturing. Non-invasive, clip-on current
sensors attach to any machine's power leads — regardless of age, make or model — and
stream a real-time heartbeat of machine state (running, idle, down) over cellular, with
no PLC, SCADA or plant Wi-Fi access required. That signal becomes real-time OEE,
downtime categorization and reasoning, Pareto analysis, cycle-time tracking, scrap
tracking, shift and plant reporting, and alerting.

- Website: https://www.guidewheel.com/
- Help centre: https://support.guidewheel.app/en/
- Application / login: https://app.guidewheel.app/
- Status: https://guidewheel.statuspage.io/
- Pricing: https://www.guidewheel.com/pricing

## API

Guidewheel publishes a customer-facing REST/JSON API under `/api/v1` for CMMS and ERP
integration:

| Resource | Path | Methods |
|---|---|---|
| Devices (+ telemetry, uptime, load state, energy, threshold changes) | `/api/v1/devices` | GET, POST |
| Issues (downtime events, comments, tags) | `/api/v1/issues` | GET, POST, PUT, PATCH, DELETE |
| Production entries (incl. bulk CSV upload) | `/api/v1/production-entries` | GET, POST, PUT |
| SKUs | `/api/v1/skus` | GET, POST |
| Tags | `/api/v1/tags` | GET, POST |
| Device lists | `/api/v1/device-lists` | GET |
| Plants | `/api/v1/plants` | GET |
| Shifts | `/api/v1/shifts` | GET |
| Scrap | `/api/v1/scraps` | GET, POST |

- **Auth**: company-scoped API key in the `x-api-key` header (an `api_key` query
  parameter is documented as deprecated). SSO for the application is SAML/OIDC via
  WorkOS; 2FA over SMS/WhatsApp.
- **Rate limits**: 1,000 calls/day and 50 calls/minute per key.
- **Environments**: production base URL is tenant-specific and provided with
  credentials; a sandbox base URL is provided on request.
- **Reference**: https://support.guidewheel.app/en/articles/15696169-guidewheel-api-cmms-erp-integration-guide

### No machine-readable contract

Guidewheel publishes **no OpenAPI, Swagger, GraphQL, AsyncAPI, MCP or A2A artifact**.
The detailed technical API guide — query parameters and sample responses — is password
protected and provided on request. Contract discovery on 2026-08-01 probed
`/openapi.json`, `/openapi.yaml`, `/swagger.json`, `/v1/openapi.json`, `/api-docs`,
`/redoc`, `/api/schema` and `/.well-known/*` against `www.guidewheel.com`,
`api.guidewheel.app`, `app.guidewheel.app`, `docs.guidewheel.app`,
`developers.guidewheel.app` and `support.guidewheel.app` — all miss. Note that every
`*.guidewheel.app` host is one single-page application that answers 200 with an HTML
shell for extensionless paths, so `api.`, `docs.` and `developers.` are CNAMEs of the
app, not separate API/docs surfaces.

Guidewheel does serve a first-party `llms.txt` at https://www.guidewheel.com/llms.txt.

## Artifacts

```
authentication/  API key + SSO/MFA profile (searched)
changelog/       dated product release notes (searched)
conformance/     standards posture (derived)
conventions/     request/response semantics, time params, gaps (searched)
data-model/      entity graph for the v1 REST API (searched)
errors/          HTTP status contract (searched)
lifecycle/       versioning, deprecation, status page (searched)
llms/            verbatim first-party llms.txt x2 (searched)
plans/           pricing (searched)
rate-limits/     1000/day, 50/min (searched)
sandbox/         on-request sandbox environment (searched)
security/        domain security probe (probed)
well-known/      discovery probe index incl. negatives (probed)
```

# Sterling (sterling-check)

Sterling (Sterling Check Corp) is a global background and identity screening provider offering criminal checks, employment and education verifications, drug and health screening, identity verification, and continuous (recurring) monitoring. The Sterling API is a documented RESTful, OAuth2-secured developer API that lets platforms, ATS/HRIS systems, and marketplaces initiate background checks, manage candidates and screening packages, retrieve results and reports (PDF/HTML), send candidate invites, and receive real-time status updates via webhook callbacks.

**Access is gated.** Developers request a Client ID and Client Secret per screening region (US, EMEA, Canada, or APAC), with separate credentials for the sandbox/integration and production environments. Documentation is published via a Postman-hosted portal at [apidocs.sterlingcheck.app](https://apidocs.sterlingcheck.app/), with a developer portal at [developer.sterlingcheck.app](https://developer.sterlingcheck.app/).

**First Advantage acquisition.** Sterling Check Corp was acquired by First Advantage Corporation; the deal closed on **October 31, 2024** at a **$2.2 billion** valuation. Sterling now operates as "a First Advantage company."

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/sterling-check/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/sterling-check/refs/heads/main/apis.yml)

## Tags

- Background Screening
- Identity Verification
- Background Check
- HR Tech
- Compliance
- Gated API

## Timestamps

- **Created:** 2026-07-03
- **Modified:** 2026-07-03

## Confirmed vs. Modeled

The Sterling API is real and documented, but its full reference sits behind a gated (Postman-hosted) portal. Confirmed from public documentation: the OAuth token exchange (Client ID + Client Secret → access token), `GET /packages`, `POST /candidates`, `POST /screenings` (including the `invite` object with `method` = `email`/`link` and the `callbackUri` webhook), and results/reports availability in PDF or HTML with per-report-item statuses. Everything else in the OpenAPI and collections is honestly **[MODELED]** on Sterling's documented order lifecycle and marked as such. The API request host `https://api.sterlingcheck.app/v2` is a modeled representative host (exact host is provisioned with credentials); the OAuth host `auth.sterlingcheck.app` is confirmed.

## APIs

### Sterling Screenings API

Initiate and manage background screenings (orders) — submit a screening for a candidate against a package, list/retrieve/cancel screenings, and schedule recurring / continuous screenings. `POST /screenings` is confirmed; list/retrieve/cancel and recurring operations are modeled.

- **Human URL:** [https://apidocs.sterlingcheck.app/](https://apidocs.sterlingcheck.app/)
- **Base URL:** `https://api.sterlingcheck.app/v2`

#### Tags

- Screenings
- Orders
- Background Check

#### Properties

- [Documentation](https://www.sterlingcheck.com/services/api/)
- [API Reference](https://apidocs.sterlingcheck.app/)
- [OpenAPI](openapi/sterling-check-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sterling-check.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sterling-check.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sterling Candidates API

Create and manage the candidate (subject) records screenings run against. Minimum fields are first name, last name, email, and `clientReferenceId`. `POST /candidates` is confirmed; retrieve and update are modeled.

- **Human URL:** [https://apidocs.sterlingcheck.app/](https://apidocs.sterlingcheck.app/)
- **Base URL:** `https://api.sterlingcheck.app/v2`

#### Tags

- Candidates
- Subjects
- PII

#### Properties

- [API Reference](https://apidocs.sterlingcheck.app/)
- [OpenAPI](openapi/sterling-check-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sterling-check.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sterling-check.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sterling Packages API

Retrieve the screening packages available to your account. A package groups screening products and specifies which candidate fields are required. `GET /packages` is confirmed; retrieve-by-id is modeled.

- **Human URL:** [https://apidocs.sterlingcheck.app/](https://apidocs.sterlingcheck.app/)
- **Base URL:** `https://api.sterlingcheck.app/v2`

#### Tags

- Packages
- Products
- Catalog

#### Properties

- [API Reference](https://apidocs.sterlingcheck.app/)
- [OpenAPI](openapi/sterling-check-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sterling-check.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sterling-check.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sterling Reports API

Retrieve results for completed screenings. A screening rolls up multiple report items, each with its own status, delivered as PDF or HTML. The Reports concept and result statuses are documented; the exact report retrieval paths are modeled.

- **Human URL:** [https://apidocs.sterlingcheck.app/](https://apidocs.sterlingcheck.app/)
- **Base URL:** `https://api.sterlingcheck.app/v2`

#### Tags

- Reports
- Results
- Adjudication

#### Properties

- [API Reference](https://apidocs.sterlingcheck.app/)
- [OpenAPI](openapi/sterling-check-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sterling-check.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sterling-check.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sterling Invites API

Invite candidates to complete consent and data collection. On `POST /screenings`, set `invite.method` to `email` (Sterling emails the candidate) or `link` (receive a hosted form URL in the response). The invite object is confirmed; standalone invite retrieval/resend is modeled.

- **Human URL:** [https://apidocs.sterlingcheck.app/](https://apidocs.sterlingcheck.app/)
- **Base URL:** `https://api.sterlingcheck.app/v2`

#### Tags

- Invites
- Candidate Experience
- Consent

#### Properties

- [API Reference](https://apidocs.sterlingcheck.app/)
- [OpenAPI](openapi/sterling-check-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sterling-check.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sterling-check.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Sterling Webhooks API

Receive real-time updates for the screenings you initiate. Specify a `callbackUri` on `POST /screenings` and Sterling posts status-change events to your endpoint. The per-screening callback is confirmed; account-level webhook subscription management is modeled.

- **Human URL:** [https://apidocs.sterlingcheck.app/](https://apidocs.sterlingcheck.app/)
- **Base URL:** `https://api.sterlingcheck.app/v2`

#### Tags

- Webhooks
- Callbacks
- Notifications

#### Properties

- [API Reference](https://apidocs.sterlingcheck.app/)
- [OpenAPI](openapi/sterling-check-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/sterling-check.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/sterling-check.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/sterlingcheck)
- [Website](https://www.sterlingcheck.com)
- [Documentation](https://apidocs.sterlingcheck.app/)
- [Developer Portal](https://developer.sterlingcheck.app/)
- [Plans](plans/sterling-check-plans-pricing.yml)
- [Rate Limits](rate-limits/sterling-check-rate-limits.yml)
- [Fin Ops](finops/sterling-check-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

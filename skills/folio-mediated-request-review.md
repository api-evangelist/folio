---
generated: '2026-10-09'
method: generated
name: mediated-request-review
description: Create a mediated request, then staff confirm or decline it in mod-requests-mediated.
api: openapi/folio-mod-requests-mediated-openapi.yml
operations:
- postMediatedRequest
- getMediatedRequestCollection
- getMediatedRequestById
- confirmMediatedRequest
- declineMediatedRequest
source: Grounded in the FOLIO module OpenAPI files under openapi/ (bundled from the provider-hosted docs at s3.amazonaws.com/foliodocs/api/).
  Every operationId verified verbatim in the named spec.
---

# Review a mediated request

Create a mediated request, then staff confirm or decline it in mod-requests-mediated.

## Auth and tenancy
FOLIO is self-hosted: use your library's gateway URL. Send `X-Okapi-Tenant` and `X-Okapi-Token` on every call (edge-* modules instead take the edge API key configured for the deployment). See overlays/ for the scheme added to specs that omit it.

## Steps
1. `postMediatedRequest` — `POST /requests-mediated/mediated-requests` — Create mediated request
2. `getMediatedRequestCollection` — `GET /requests-mediated/mediated-requests` — Retrieve a collection of mediated requests
3. `getMediatedRequestById` — `GET /requests-mediated/mediated-requests/{mediatedRequestId}` — Retrieve mediated request object by id
4. `confirmMediatedRequest` — `POST /requests-mediated/mediated-requests/{mediatedRequestId}/confirm` — Confirm mediated request
5. `declineMediatedRequest` — `POST /requests-mediated/mediated-requests/{mediatedRequestId}/decline` — Decline mediated request

## Notes
- Queries on collection endpoints use CQL in the `query` parameter.
- Operation semantics, parameters and error bodies are as defined in the spec; no idempotency keys are documented, so do not blindly retry POSTs.

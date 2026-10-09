---
generated: '2026-10-09'
method: generated
name: place-and-track-a-request
description: Create a hold/page/recall request through mod-circulation-bff, list requests, and print pick slips
  for a service point.
api: openapi/folio-mod-circulation-bff-circulationbff-openapi.yml
operations:
- createRequest
- getRequests
- getPickSlips
source: Grounded in the FOLIO module OpenAPI files under openapi/ (bundled from the provider-hosted docs at s3.amazonaws.com/foliodocs/api/).
  Every operationId verified verbatim in the named spec.
---

# Place and track a circulation request

Create a hold/page/recall request through mod-circulation-bff, list requests, and print pick slips for a service point.

## Auth and tenancy
FOLIO is self-hosted: use your library's gateway URL. Send `X-Okapi-Tenant` and `X-Okapi-Token` on every call (edge-* modules instead take the edge API key configured for the deployment). See overlays/ for the scheme added to specs that omit it.

## Steps
1. `createRequest` — `POST /circulation-bff/requests` — Create ECS TLR or Circulation request
2. `getRequests` — `GET /circulation-bff/requests` — Get ECS TLR or Circulation requests
3. `getPickSlips` — `GET /circulation-bff/pick-slips/{servicePointId}` — API to get pick slips

## Notes
- Queries on collection endpoints use CQL in the `query` parameter.
- Operation semantics, parameters and error bodies are as defined in the spec; no idempotency keys are documented, so do not blindly retry POSTs.

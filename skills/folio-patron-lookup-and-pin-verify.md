---
generated: '2026-10-09'
method: generated
name: patron-lookup-and-pin-verify
description: 'Edge flow for third-party systems: find a user, check existence, verify a patron PIN via edge-users.'
api: openapi/folio-edge-users-openapi.yml
operations:
- getUsers
- userExists
- verifyPin
source: Grounded in the FOLIO module OpenAPI files under openapi/ (bundled from the provider-hosted docs at s3.amazonaws.com/foliodocs/api/).
  Every operationId verified verbatim in the named spec.
---

# Look up a patron and verify a PIN

Edge flow for third-party systems: find a user, check existence, verify a patron PIN via edge-users.

## Auth and tenancy
FOLIO is self-hosted: use your library's gateway URL. Send `X-Okapi-Tenant` and `X-Okapi-Token` on every call (edge-* modules instead take the edge API key configured for the deployment). See overlays/ for the scheme added to specs that omit it.

## Steps
1. `getUsers` — `GET /users/users` — Retrieve users collection
2. `userExists` — `GET /users/user-exists` — Returns an indication whether the specified user exists or not
3. `verifyPin` — `POST /users/patron-pin/verify` — Verify patron PIN

## Notes
- Queries on collection endpoints use CQL in the `query` parameter.
- Operation semantics, parameters and error bodies are as defined in the spec; no idempotency keys are documented, so do not blindly retry POSTs.

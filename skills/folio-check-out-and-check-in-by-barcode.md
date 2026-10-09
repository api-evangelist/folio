---
generated: '2026-10-09'
method: generated
name: check-out-and-check-in-by-barcode
description: 'Circulation desk flow through mod-circulation-bff: check out to a patron by barcode, read the loan,
  check it back in.'
api: openapi/folio-mod-circulation-bff-circulationbff-openapi.yml
operations:
- checkOutByBarcode
- findCirculationLoansByQuery
- getCirculationLoanById
- checkInByBarcode
source: Grounded in the FOLIO module OpenAPI files under openapi/ (bundled from the provider-hosted docs at s3.amazonaws.com/foliodocs/api/).
  Every operationId verified verbatim in the named spec.
---

# Check an item out and back in by barcode

Circulation desk flow through mod-circulation-bff: check out to a patron by barcode, read the loan, check it back in.

## Auth and tenancy
FOLIO is self-hosted: use your library's gateway URL. Send `X-Okapi-Tenant` and `X-Okapi-Token` on every call (edge-* modules instead take the edge API key configured for the deployment). See overlays/ for the scheme added to specs that omit it.

## Steps
1. `checkOutByBarcode` — `POST /circulation-bff/loans/check-out-by-barcode` — Checks item out by barcode
2. `findCirculationLoansByQuery` — `GET /circulation-bff/loans` — Find circulation loans by query
3. `getCirculationLoanById` — `GET /circulation-bff/loans/{loanId}` — Retrieve circulation flow by id
4. `checkInByBarcode` — `POST /circulation-bff/loans/check-in-by-barcode` — Checks item in by barcode

## Notes
- Queries on collection endpoints use CQL in the `query` parameter.
- Operation semantics, parameters and error bodies are as defined in the spec; no idempotency keys are documented, so do not blindly retry POSTs.

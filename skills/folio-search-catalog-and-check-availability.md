---
generated: '2026-10-09'
method: generated
name: search-catalog-and-check-availability
description: Find instances with a CQL query via mod-search, narrow with facets, then check live item availability
  through edge-rtac.
api:
- openapi/folio-mod-search-openapi.yml
- openapi/folio-edge-rtac-openapi.yml
operations:
- searchInstances
- getFacets
- getInstanceRtac
- getBatchRtac
source: Grounded in the FOLIO module OpenAPI files under openapi/ (bundled from the provider-hosted docs at s3.amazonaws.com/foliodocs/api/).
  Every operationId verified verbatim in the named spec.
---

# Search the catalog and check real-time availability

Find instances with a CQL query via mod-search, narrow with facets, then check live item availability through edge-rtac.

## Auth and tenancy
FOLIO is self-hosted: use your library's gateway URL. Send `X-Okapi-Tenant` and `X-Okapi-Token` on every call (edge-* modules instead take the edge API key configured for the deployment). See overlays/ for the scheme added to specs that omit it.

## Steps
1. `searchInstances` — `GET /search/instances` — Search Instances
2. `getFacets` — `GET /search/{recordType}/facets` — Get Facets
3. `getInstanceRtac` — `GET /rtac/{instanceId}` — Get RTAC info for a single instance
4. `getBatchRtac` — `GET /rtac` — Get RTAC info for multiple instances

## Notes
- Queries on collection endpoints use CQL in the `query` parameter.
- Operation semantics, parameters and error bodies are as defined in the spec; no idempotency keys are documented, so do not blindly retry POSTs.

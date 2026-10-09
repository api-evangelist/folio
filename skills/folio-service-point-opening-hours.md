---
generated: '2026-10-09'
method: generated
name: service-point-opening-hours
description: Find calendars for a service point and compute its openings with mod-calendar.
api: openapi/folio-mod-calendar-openapi.yml
operations:
- searchCalendars
- getCalendar
- getAllOpenings
- getSurroundingOpenings
source: Grounded in the FOLIO module OpenAPI files under openapi/ (bundled from the provider-hosted docs at s3.amazonaws.com/foliodocs/api/).
  Every operationId verified verbatim in the named spec.
---

# Look up service point opening hours

Find calendars for a service point and compute its openings with mod-calendar.

## Auth and tenancy
FOLIO is self-hosted: use your library's gateway URL. Send `X-Okapi-Tenant` and `X-Okapi-Token` on every call (edge-* modules instead take the edge API key configured for the deployment). See overlays/ for the scheme added to specs that omit it.

## Steps
1. `searchCalendars` — `GET /calendar/calendars` — Search all calendars
2. `getCalendar` — `GET /calendar/calendars/{calendarId}` — Get a calendar
3. `getAllOpenings` — `GET /calendar/dates/{servicePointId}/all-openings` — Daily opening information
4. `getSurroundingOpenings` — `GET /calendar/dates/{servicePointId}/surrounding-openings` — Surrounding openings

## Notes
- Queries on collection endpoints use CQL in the `query` parameter.
- Operation semantics, parameters and error bodies are as defined in the spec; no idempotency keys are documented, so do not blindly retry POSTs.

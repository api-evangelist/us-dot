---
name: Check US airport delays and ground stops
description: >-
  Read live National Airspace System delay status from the FAA — national roll-up or a
  single airport by IATA/ICAO code. Anonymous, free, no registration.
generated: '2026-07-28'
method: generated
provider: us-dot
api: openapi/us-dot-faa-airport-status-web-service-openapi.yml
base_url: https://external-api.faa.gov
operations:
  - getDelays
  - getAirportStatus
---

# Check US airport delays and ground stops

The FAA Airport Status Web Service (ASWS) reports what the National Airspace System is
doing right now: ground delays, ground stops, arrival/departure delays and airport
closures. It is one of the very few genuinely open, unauthenticated federal APIs.

## Before you call

- **Auth: none.** No API key, no registration, no terms acceptance. Verified anonymous
  HTTP 200 on 2026-07-28.
- **Base URL:** `https://external-api.faa.gov` (the spec also lists
  `https://external.apic4e.faa.gov`; both are the same FAA Gravitee gateway).
- **Content type:** the operations declare both `application/json` and
  `application/xml`. Send `Accept: application/json`.
- **Do not cache.** The service responds `Cache-Control: max-age=0, no-cache, no-store`
  and `Pragma: no-cache`. Poll; never serve a stale delay.
- **Coverage is ~40 airports.** BOS, LGA, TEB, EWR, JFK, PHL, PIT, IAD, BWI, DCA, RDU,
  CLT, ATL, MCO, TPA, FLL, MIA, DTW, CLE, MDW, ORD, IND, CVG, BNA, MEM, STL, MCI, MSP,
  DFW, IAH, DEN, SLC, PHX, LAS, SAN, LAX, SJC, SFO, PDX, SEA. Anything else is a 404 by
  design, not a failure.

## Step 1 — national picture

Call **`getDelays`** — `GET /api/airport/delays`.

The response is a `Delays` envelope with four parallel collections:
`GroundDelays`, `GroundStops`, `ArriveDepartDelays`, `Closures`. Each entry carries an
`airport` (IATA code) plus a `reason` and a timing field (`avgTime`, `endTime`,
`minTime`/`maxTime`, `reopen`).

There is no total count and no paging — the collection is complete.

## Step 2 — one airport

Call **`getAirportStatus`** — `GET /api/airport/status/{airportCode}`.

`airportCode` accepts **either** an IATA three-letter code (`JFK`) **or** an ICAO
four-letter code (`KJFK`). The response returns both (`iata`, `icao`) plus `name`,
`city`, `state`, `supportedAirport`, `delay` (boolean), `delayCount`, a `status[]` array
of `Status` objects, and a `weather` object.

Read `supportedAirport` before you read `delay`: `supportedAirport: false` means the
airport is outside the FAA's reporting set, which is different from "no delays".

## Errors — and what they actually mean

The spec declares `content: {}` on every error, so you get a bare status code.

| Status | Operation | Meaning | Do |
|---|---|---|---|
| 404 | `getDelays` | Upstream fly.faa.gov feed is unavailable | Retry with backoff; fall back to `https://nasstatus.faa.gov/` |
| 404 | `getAirportStatus` | Airport not in the supported set | Validate the code against the list above — do not retry |
| 500 | both | fly.faa.gov returned an error | Retry with backoff |

Both operations are safe `GET`s, so **retry is unconditionally safe**. There is no
idempotency key anywhere in this API and none is needed.

## Tracing

Responses carry `X-Gravitee-Transaction-Id`, `X-Gravitee-Request-Id` and
`X-Gravitee-Client-Identifier`. Capture the transaction id and quote it if you report a
problem through `https://api.faa.gov/s/`.

## Rate limits

No `RateLimit`, `X-RateLimit` or `Retry-After` header is emitted, and the FAA publishes
no numeric limit. Be a good citizen: this is a real-time operational feed — poll on the
order of a minute, not a second.

## Licence

CC0 1.0 (declared in `info.license` of the OpenAPI). Public domain, no attribution
required, no commercial restriction.

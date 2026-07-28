---
name: Query BTS and DOT open data with SoQL
description: >-
  Pull US airline economics and DOT open data from the Socrata SODA 2.1 platforms at
  data.bts.gov, data.transportation.gov and datahub.transportation.gov. Anonymous.
generated: '2026-07-28'
method: generated
provider: us-dot
api: null
api_note: >-
  Socrata publishes no OpenAPI, so there are no operationIds to ground in. Every
  resource id, parameter and endpoint below was verified live on 2026-07-28.
base_url: https://data.bts.gov/resource
operations: []
---

# Query BTS and DOT open data with SoQL

The Bureau of Transportation Statistics is the authoritative record of US commercial
aviation activity, and it is served as a plain Socrata SODA 2.1 API. There is no
OpenAPI, no SDK from DOT, and no key required.

## Before you call

- **Auth: none required.** An optional Socrata **application token** (`X-App-Token`
  header, or `$$app_token` query parameter) moves you off the shared anonymous throttle
  pool onto a per-application one. It is **not** authentication and the API works
  without it. Get one at `https://data.transportation.gov/profile/edit/developer_settings`.
- **Hosts:**
  - `https://data.bts.gov/resource` — Bureau of Transportation Statistics (420 datasets)
  - `https://datahub.transportation.gov/resource` — DOT Data Hub (1,542 datasets)
  - `https://data.transportation.gov/resource` — same tenancy as datahub
- **Licence:** Public Domain U.S. Government (`USGOV_WORKS`).

## Step 1 — find the dataset

Each dataset is addressed by a **four-by-four** id (`bu82-4pwz`). Two ways to find one:

- `GET https://data.bts.gov/data.json` — the DCAT-US 1.1 catalogue, every dataset with
  `title`, `description`, `modified` and `accrualPeriodicity`. 598 KB.
- `GET https://data.transportation.gov/data.json` — same for the DOT Data Hub. 2.7 MB.

Dataset metadata (licence, attribution, provenance, column types) is at
`/api/views/{fourbyfour}.json`.

Verified live aviation resources on `data.bts.gov`:

| Resource | Content |
|---|---|
| `bu82-4pwz` | T-100 segment summaries by carrier, country, origin airport, month |
| `6u8d-47ih` | Air Carrier Financial (Form 41) series |
| `xyfb-hgtv` | Commercial aviation service-quality series |

On `datahub.transportation.gov`: `4f3n-jbg2` and `tfrh-tu9e` (Consumer Airfare Report
city-pair fare tables).

## Step 2 — query with SoQL

`GET /resource/{fourbyfour}.json` plus `$`-prefixed parameters:

| Parameter | Use |
|---|---|
| `$select` | Column projection, aggregates (`sum(passengers) AS pax`) |
| `$where` | Filter (`year=2025 AND origin='JFK'`) |
| `$order` | Sort — **required for stable paging** |
| `$group` | Group by |
| `$having` | Filter on aggregates |
| `$limit` | Page size. Default **1000**, max **50000** |
| `$offset` | Page offset |
| `$q` | Full-text search |

Example:

```
GET https://data.bts.gov/resource/bu82-4pwz.json
  ?$select=carrier_name,sum(passengers) AS pax
  &$where=year=2025
  &$group=carrier_name
  &$order=pax DESC
  &$limit=25
```

Extensions drive the format: `.json`, `.csv`, `.geojson`, `.xml` on the resource path.

## Paging — the one real trap

SODA 2.1 returns a **bare JSON array**. No envelope, no total count, no next-link.
Without an explicit `$order` on a unique column the row order is **not stable across
pages** and you will silently duplicate and drop rows. Always page like this:

```
?$order=:id&$limit=50000&$offset=0
?$order=:id&$limit=50000&$offset=50000
```

`:id` is Socrata's internal row identifier and is always unique.

## Errors

Socrata returns its own envelope — **not** RFC 9457:

```json
{"code": "query.soql.no-such-column", "error": true, "message": "...", "data": {}}
```

Read `code`, not the HTTP status, to decide what to do. A malformed `$where` is a client
error you must fix, not retry.

## Caching and tracing

`ETag` / `If-None-Match` are supported — use conditional GETs on datasets that update
monthly or quarterly. Responses carry `X-Socrata-RequestId`.

## Bulk

For anything large, skip the API: `https://www.transtats.bts.gov/` publishes the same
T-100 and Form 41 series as bulk downloads. There is no rate charge and no lock-in.

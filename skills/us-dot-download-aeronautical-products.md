---
name: Download FAA aeronautical charts and airspace data
description: >-
  Resolve the current or next edition of an FAA aeronautical product (NASR, dTPP, CIFP,
  enroute and VFR charts, obstacle file) and get its download URL. Anonymous and free.
generated: '2026-07-28'
method: generated
provider: us-dot
api: openapi/us-dot-faa-aeronautic-product-release-api-openapi.yml
base_url: https://external-api.faa.gov/apra
operations:
  - getNASREdition
  - getNASRSubscription
  - getTPPEdition
  - getTPPRelease
  - getCIFPEdition
  - getCIFPRelease
  - getIFREnrouteEdition
  - getIFREnrouteRelease
  - getDDOFEdition
  - getDDOFRelease
  - getSectionalInfo
  - getSectionalChart
  - getOceanicRouteEdition
  - getOceanicRouteChart
---

# Download FAA aeronautical charts and airspace data

The FAA Aeronautic Product Release API (APRA) exposes 34 GET operations over the FAA's
published chart and data products. It does **not** serve the files — it serves the
**download URLs** and the **edition metadata** that tells you when a new one exists.

## Before you call

- **Auth: none.** Verified anonymous HTTP 200 on 2026-07-28 against `/nfdc/nasr/info`
  and `/dtpp/info`.
- **Base URL:** `https://external-api.faa.gov/apra`.
- **Response format:** XML (`productSet` document with a `status` element and one or more
  `edition` elements), not JSON. Do not send `Accept: application/json` and expect it to
  work.
- **Licence:** CC0 1.0.

## The one pattern that governs all 34 operations

Every product ships as a **pair**:

- `/{product}/info` → **edition metadata** — the current and next edition date and number.
- `/{product}/chart` → **the download link** for a given edition.

**Always call `/info` first.** Requesting a `/chart` for an edition that has not been
released yet returns 404, and you cannot tell that apart from "wrong parameters" because
the error body is empty.

## Step 1 — resolve the edition

| Product | Edition op | Cycle |
|---|---|---|
| NASR 28-day subscription (airports, navaids, airways, fixes) | `getNASREdition` | 28 days |
| US Terminal Procedures Publication (dTPP) | `getTPPEdition` | 28 days |
| Coded Instrument Flight Procedures (CIFP) | `getCIFPEdition` | 28 days |
| IFR enroute charts | `getIFREnrouteEdition` | 56 days |
| Oceanic route charts | `getOceanicRouteEdition` | 56 days |
| VFR sectional charts | `getSectionalInfo` | 56 days |
| Daily Digital Obstacle File | `getDDOFEdition` | daily |

Common parameter: `edition` — enum `current` | `next`, default `current`.

## Step 2 — get the download URL

| Product | Release op | Extra required parameters |
|---|---|---|
| NASR | `getNASRSubscription` | — |
| dTPP | `getTPPRelease` | `geoname` (`US` or a full state name); `edition` also accepts `changeset` |
| CIFP | `getCIFPRelease` | — |
| IFR enroute | `getIFREnrouteRelease` | `geoname` (`US`\|`Alaska`\|`Pacific`\|`Caribbean`) **and** `seriesType` (`low`\|`high`\|`area`), both required |
| Oceanic | `getOceanicRouteChart` | `geoname` (`NARC`\|`PORC`\|`WATRS`), required |
| Sectional | `getSectionalChart` | `geoname` (a city — 52-value enum), required |
| DDOF | `getDDOFRelease` | — |

`format` is `pdf` (default) or `tiff` where offered. **TIFF is geo-referenced; PDF is
not.** If you are going to place the chart on a map, ask for TIFF.

Then fetch the returned URL directly. It is a ZIP on the FAA aeronav host, not on the API
gateway.

## The `changeset` trick

`getTPPRelease` accepts `edition=changeset`, which operates against the current release
and returns **only the charts that changed since the previous release**. Use it to avoid
re-downloading the whole terminal procedures set every 28 days.

## Errors

| Status | Meaning | Do |
|---|---|---|
| 400 | Illegal arguments | Check `edition`/`format`/`geoname`/`seriesType` against the enums — the API is strict |
| 404 | Edition not released, or not found | Call the matching `/info` first; do not retry blindly |
| 404 with "This product has been deprecated" | Product retired | **Retire the integration.** This description is the FAA's only deprecation signal — there is no `Sunset` header |
| 500 | Internal service error | Retry with backoff; all operations are safe GETs |

`getDERSRelease` and `getDERSEdition` (Digital Enroute Supplement) are marked
`deprecated: true` in the spec and return only 404. Do not call them.

## Watching for new editions

There is no webhook, no feed and no `Sunset`/`Deprecation` header anywhere. Poll the
`/info` operation on the product's cycle and compare `editionDate`. A human email list
exists at `https://www.faa.gov/data/subscribe`.

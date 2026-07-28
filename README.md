# U.S. Department of Transportation (us-dot)

The U.S. Department of Transportation (DOT) is the federal transportation regulator for the United States, the deepest travel market in the world. In aviation DOT is not a participant in the distribution chain — it is the counterweight to it: through the Office of the Secretary it writes and enforces 14 CFR Part 256 on electronic airline information systems (explicitly naming global distribution systems, corporate booking tools and internet flight search tools), Part 257 on code-share disclosure, Part 250 on oversales, Part 259 on enhanced passenger protections, Part 260 on fare and ancillary fee refunds, and 399.84 on full-fare advertising. Its Bureau of Transportation Statistics is the sole authoritative source for US airline economics — T-100 segment traffic, Form 41 financials, the Consumer Airfare Report city-pair fare tables, denied boardings and mishandled baggage — published as free Socrata SODA APIs. Its Federal Aviation Administration operates a Gravitee API portal at api.faa.gov whose public catalog is enumerable without login and serves genuinely open, unauthenticated OpenAPI 3.0.1 services for national airspace delay status and aeronautical chart product releases, alongside gated APIs for pilot records and safety reporting.

API posture, honestly: transportation.gov itself is bot-blocked (HTTP 403 to any non-browser client) and publishes no departmental OpenAPI, but the data surfaces underneath it are open, unmetered, public domain, and fully bulk-exportable — this is a provider with an excellent exit path and no commercial lock-in of any kind.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/us-dot/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/us-dot/refs/heads/main/apis.yml)

## Tags

- Travel
- United States
- Aviation
- Airlines
- Airports
- Government
- Regulator
- Distribution
- Aviation Consumer Protection
- Open Data

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

### FAA Airport Status Web Service (ASWS)

Real-time National Airspace System delay and airport status service operated by the Federal Aviation Administration, a DOT operating administration. Two GET operations return current ground delays, ground stops, arrival/departure delays and closures across supported US airports, and per-airport status keyed by IATA or ICAO code. Verified anonymously with HTTP 200 on 2026-07-28 — no API key, no registration, no terms acceptance.

- **Human URL:** [https://api.faa.gov/s/](https://api.faa.gov/s/)
- **Base URL:** `https://external-api.faa.gov/asws/api`

#### Tags

- Aviation
- Airports
- Delays
- Air Traffic
- FAA

#### Properties

- [OpenAPI](openapi/us-dot-faa-airport-status-web-service-openapi.yml)
- [Documentation](https://api.faa.gov/s/)

### FAA Aeronautic Product Release API (APRA)

FAA aeronautical chart and data publication download API. Thirty-four GET operations expose edition metadata and ZIP product downloads for the digital Terminal Procedures Publication (dTPP), IFR enroute and oceanic charts, VFR charts, the Coded Instrument Flight Procedures data set, the NFDC/NASR 28-day airspace subscription, the Digital Obstacle File and more. Verified anonymously with HTTP 200 on 2026-07-28.

- **Human URL:** [https://api.faa.gov/s/](https://api.faa.gov/s/)
- **Base URL:** `https://external-api.faa.gov/apra`

#### Tags

- Aviation
- Charts
- Aeronautical Data
- Airspace
- FAA

#### Properties

- [OpenAPI](openapi/us-dot-faa-aeronautic-product-release-api-openapi.yml)
- [Documentation](https://www.faa.gov/air_traffic/flight_info/aeronav/digital_products/)

### FAA Air Carrier Pilot Records Database (PRD) API

Data submission API for the FAA Pilot Records Database. Five paths covering pilot record create/update/delete, pilot data tracking, and asynchronous pilot data search request and response. Access is restricted by the FAA to operators under 14 CFR Part 121, 135, 125, 91K, Air Tour, Public Aircraft, or Part 91 Corporate.

- **Human URL:** [https://api.faa.gov/s/](https://api.faa.gov/s/)
- **Base URL:** `https://external.apic4e.faa.gov`

#### Tags

- Aviation
- Pilot Records
- Airlines
- Compliance
- FAA

#### Properties

- [OpenAPI](openapi/us-dot-faa-air-carrier-prd-api-openapi.yml)
- [Documentation](https://api.faa.gov/s/)

### FAA Safety Assurance System (SAS) API

Single-operation submission API for passenger discrepancy reporting into the FAA Safety Assurance System. The harvested OpenAPI 3.0.0 declares apiKey and appId security schemes, so a credential is required.

- **Human URL:** [https://api.faa.gov/s/](https://api.faa.gov/s/)
- **Base URL:** `https://external.apic4e.faa.gov/axh-sasp-api/sas`

#### Tags

- Aviation
- Safety
- Compliance
- FAA

#### Properties

- [OpenAPI](openapi/us-dot-faa-safety-assurance-system-api-openapi.yml)
- [Documentation](https://api.faa.gov/s/)

### DOT Data Hub Open Data API

The departmental open data platform, served from both data.transportation.gov and datahub.transportation.gov on Socrata SODA 2.1. For travel and aviation this is where the DOT Office of the Assistant Secretary for Aviation and International Affairs publishes the Consumer Airfare Report city-pair fare tables, the Airline Quarterly Financial Review, and international seat and passenger reports. Datasets are licensed Public Domain U.S. Government (USGOV_WORKS).

- **Human URL:** [https://data.transportation.gov/](https://data.transportation.gov/)
- **Base URL:** `https://datahub.transportation.gov/resource`

#### Tags

- Open Data
- Aviation
- Airfares
- Airlines
- Statistics

#### Properties

- [Documentation](https://dev.socrata.com/docs/endpoints.html)
- [Portal](https://data.transportation.gov/)
- [Portal](https://datahub.transportation.gov/)
- [License](https://www.usa.gov/government-works)

### Bureau of Transportation Statistics Open Data API

The Bureau of Transportation Statistics open data platform on Socrata SODA 2.1, and the authoritative record of US commercial aviation activity. Aviation holdings verified live include T-100 segment summaries, Air Carrier Financial (Form 41) series, average air fare by carrier and quarter, mishandled baggage and wheelchairs, and involuntary denied boardings by airline.

- **Human URL:** [https://data.bts.gov/](https://data.bts.gov/)
- **Base URL:** `https://data.bts.gov/resource`

#### Tags

- Open Data
- Aviation
- Airlines
- Statistics
- BTS

#### Properties

- [Documentation](https://dev.socrata.com/docs/endpoints.html)
- [Portal](https://data.bts.gov/)
- [Bulk Data](https://www.transtats.bts.gov/)
- [License](https://www.usa.gov/government-works)

## Common Properties

- [Website](https://www.transportation.gov/)
- [Portal](https://data.transportation.gov/)
- [Portal](https://data.bts.gov/)
- [Documentation](https://api.faa.gov/s/)
- [Bulk Data](https://www.transtats.bts.gov/)
- [Bulk Data](https://registry.faa.gov/database/ReleasableAircraft.zip)
- [GitHub Organization](https://github.com/usdot-jpo-ode)
- [X](https://x.com/USDOT)
- [License](https://www.usa.gov/government-works)
- [Regulation — 14 CFR Part 256](https://www.ecfr.gov/current/title-14/chapter-II/subchapter-A/part-256)

## Switching Cost

Recorded in full in [`review.yml`](review.yml).

- **Interface shape:** standard-plus-proprietary — OpenAPI 3.0.x and Socrata SODA 2.1 over plain HTTP, with DOT/FAA-specific payload vocabularies. No OpenTravel/OTA, HTNG or IATA NDC conformance anywhere.
- **Second source:** no-alternative — DOT and FAA are the statutory origin for US airline economic filings, aircraft registration, aeronautical charts and airspace status. Commercial vendors (Cirium, OAG, FlightAware, aviationstack) repackage this data rather than replace it.
- **Exit path:** bulk-export-documented — SODA `$limit`/`$offset` and `rows.csv?accessType=DOWNLOAD`, TranStats full-table ZIPs, `registry.faa.gov/database/ReleasableAircraft.zip` (HTTP 200), and APRA chart product ZIPs.
- **Identifier portability:** IATA carrier and airport codes, ICAO airport codes, DOT/BTS airline IDs, BTS city market and airport IDs, FAA N-numbers. No PNRs, no GDS record IDs, nothing opaque.
- **Contractual lock-in:** nothing published for developers — datasets are `USGOV_WORKS` public domain and the open APIs require no account. The contractual weight runs outward, as 14 CFR Chapter II obligations on carriers, ticket agents and electronic airline information systems.
- **Distribution model:** not-applicable — DOT regulates the distribution chain rather than participating in it, asserting jurisdiction over GDSs, corporate booking tools and internet flight search tools under 14 CFR Part 256.
- **Access gate:** self-serve — no key, no registration and no terms click-through on the public surface. The FAA NOTAM API (HTTP 401) and the PRD API (restricted to specific operator classes) are the exceptions.

## Maintainers

- **Kin Lane** — kin@apievangelist.com

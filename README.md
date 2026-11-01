# U.S. Department of Transportation

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

The U.S. Department of Transportation (DOT) is the federal transportation regulator for the United States, the deepest travel market in the world. In aviation DOT is not a participant in the distribution chain — it is the counterweight to it: through the Office of the Secretary it writes and enforces 14 CFR Part 256 on electronic airline information systems (explicitly naming global distribution systems, corporate booking tools and internet flight search tools), Part 257 on code-share disclosure, Part 250 on oversales, Part 259 on enhanced passenger protections, Part 260 on fare and ancillary fee refunds, and 399.84 on full-fare advertising. Its Bureau of Transportation Statistics is the sole authoritative source for US airline economics — T-100 segment traffic, Form 41 financials, the Consumer Airfare Report city-pair fare tables, denied boardings and mishandled baggage — published as free Socrata SODA APIs. Its Federal Aviation Administration operates a Gravitee API portal at api.faa.gov whose public catalog is enumerable without login and serves genuinely open, unauthenticated OpenAPI 3.0.1 services for national airspace delay status and aeronautical chart product releases, alongside gated APIs for pilot records and safety reporting. Beyond aviation the operating administrations each run their own surface: NHTSA publishes anonymous vehicle, recall, complaint and safety-rating APIs; FRA publishes SOAP/WSDL rail safety services; FMCSA issues the department's only self-serve API key behind a Login.gov account. API posture, honestly: transportation.gov itself is bot-blocked (HTTP 403 to any non-browser client) and publishes no departmental OpenAPI, there is no OAuth, no idempotency key, no RFC 9457 errors, no Sunset headers and no security.txt anywhere — but the data surfaces underneath are open, unmetered, public domain and fully bulk-exportable. This is a provider with an excellent exit path and no commercial lock-in of any kind.

**Areas:** Travel · United States · Aviation · Airlines · Airports · Government · Regulator · Aviation Consumer Protection · Open Data · Transportation · Safety · Statistics

## U.S. Department of Transportation on APIs.io

Everything profiled for U.S. Department of Transportation is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/us-dot/](https://apis.io/providers/us-dot/)** — or go straight to one of the APIs or properties below.

### APIs (41)

- [FAA Data Catalog (CKAN Action API v3)](https://apis.io/apis/us-dot/faa-data-catalog-ckan-api/) — The Federal Aviation Administration's open data catalog, running CKAN 2.11.4 and exposing the full CKAN Action API v3 anonymously at /api/3/action/.…
- [DOT Data Hub Open Data API](https://apis.io/apis/us-dot/dot-data-hub-soda-api/) — The departmental open data platform, served from both data.transportation.gov and datahub.transportation.gov on Socrata SODA 2.1. For travel and aviation…
- [Bureau of Transportation Statistics Open Data API](https://apis.io/apis/us-dot/bts-open-data-soda-api/) — The Bureau of Transportation Statistics open data platform on Socrata SODA 2.1, and the authoritative record of US commercial aviation activity. Aviation…
- [NHTSA vPIC (Vehicle Product Information Catalog) API](https://apis.io/apis/us-dot/nhtsa-vpic-api/) — The National Highway Traffic Safety Administration's Vehicle Product Information Catalog and VIN decoder, and the most widely consumed API in the…
- [NHTSA Safety API (recalls, complaints, safety ratings)](https://apis.io/apis/us-dot/nhtsa-safety-api/) — The NHTSA public safety API that powers the dynamic search applications on nhtsa.gov. Three families: /recalls for safety recalls by vehicle or campaign…
- [FRA Safety Data Web Services](https://apis.io/apis/us-dot/fra-safety-data-api/) — The Federal Railroad Administration's rail safety web services, and the only SOAP surface in the department. Two WSDL 1.1 contracts were retrieved live and…
- [FMCSA QCMobile API](https://apis.io/apis/us-dot/fmcsa-qcmobile-api/) — The Federal Motor Carrier Safety Administration's carrier data API — real-time queries on motor carrier registration, authority and safety data, including…
- [U.S. Department of Transportation Air Carrier API](https://apis.io/apis/us-dot/us-dot-aircarrierapi-api/) — The AirCarrierApi API from U.S. Department of Transportation — 4 operation(s) for aircarrierapi.
- [U.S. Department of Transportation Axhsubmitdiscrepancies API](https://apis.io/apis/us-dot/us-dot-axhsubmitdiscrepancies-api/) — The Axhsubmitdiscrepancies API from U.S. Department of Transportation — 1 operation(s) for axhsubmitdiscrepancies.
- [U.S. Department of Transportation Coded Instrument Flight Procedures (CIFP) API](https://apis.io/apis/us-dot/us-dot-coded-instrument-flight-procedures-cifp-api/) — The Coded Instrument Flight Procedures (CIFP) API from U.S. Department of Transportation — 2 operation(s) for coded instrument flight procedures (cifp).
- [U.S. Department of Transportation Daily Digital Obstacle File (DDOF) API](https://apis.io/apis/us-dot/us-dot-daily-digital-obstacle-file-ddof-api/) — The Daily Digital Obstacle File (DDOF) API from U.S. Department of Transportation — 2 operation(s) for daily digital obstacle file (ddof).
- [U.S. Department of Transportation Digital Enroute Charts US (DDECUS) API](https://apis.io/apis/us-dot/us-dot-digital-enroute-charts-us-ddecus-api/) — The Digital Enroute Charts US (DDECUS) API from U.S. Department of Transportation — 2 operation(s) for digital enroute charts us (ddecus).
- [U.S. Department of Transportation Digital Enroute Supplement (DERS) API](https://apis.io/apis/us-dot/us-dot-digital-enroute-supplement-ders-api/) — The Digital Enroute Supplement (DERS) API from U.S. Department of Transportation — 2 operation(s) for digital enroute supplement (ders).
- [U.S. Department of Transportation FAA Airport Status Service API](https://apis.io/apis/us-dot/us-dot-faa-airport-status-service-api/) — The FAA Airport Status Service API from U.S. Department of Transportation — 2 operation(s) for faa airport status service.
- [U.S. Department of Transportation Grand Canyon VFR Chart API](https://apis.io/apis/us-dot/us-dot-grand-canyon-vfr-chart-api/) — The Grand Canyon VFR Chart API from U.S. Department of Transportation — 2 operation(s) for grand canyon vfr chart.
- [U.S. Department of Transportation Gulf of Mexico IFR Enroute Chart API](https://apis.io/apis/us-dot/us-dot-gulf-of-mexico-ifr-enroute-chart-api/) — The Gulf of Mexico IFR Enroute Chart API from U.S. Department of Transportation — 2 operation(s) for gulf of mexico ifr enroute chart.
- [U.S. Department of Transportation IFR Enroute Charts API](https://apis.io/apis/us-dot/us-dot-ifr-enroute-charts-api/) — The IFR Enroute Charts API from U.S. Department of Transportation — 2 operation(s) for ifr enroute charts.
- [U.S. Department of Transportation IFR Planning Charts API](https://apis.io/apis/us-dot/us-dot-ifr-planning-charts-api/) — The IFR Planning Charts API from U.S. Department of Transportation — 2 operation(s) for ifr planning charts.
- [U.S. Department of Transportation log file API](https://apis.io/apis/us-dot/us-dot-log-file-api/) — The log file API from U.S. Department of Transportation — 1 operation(s) for log file.
- [U.S. Department of Transportation NASR 28 Day Subscription API](https://apis.io/apis/us-dot/us-dot-nasr-28-day-subscription-api/) — The NASR 28 Day Subscription API from U.S. Department of Transportation — 2 operation(s) for nasr 28 day subscription.
- [U.S. Department of Transportation Oceanic Route Charts API](https://apis.io/apis/us-dot/us-dot-oceanic-route-charts-api/) — The Oceanic Route Charts API from U.S. Department of Transportation — 2 operation(s) for oceanic route charts.
- [U.S. Department of Transportation PDM API](https://apis.io/apis/us-dot/us-dot-pdm-api/) — The PDM API from U.S. Department of Transportation — 1 operation(s) for pdm.
- [U.S. Department of Transportation Sectional Charts API](https://apis.io/apis/us-dot/us-dot-sectional-charts-api/) — The Sectional Charts API from U.S. Department of Transportation — 2 operation(s) for sectional charts.
- [U.S. Department of Transportation SNMP API](https://apis.io/apis/us-dot/us-dot-snmp-api/) — The SNMP API from U.S. Department of Transportation — 1 operation(s) for snmp.
- [U.S. Department of Transportation Supplement Chart API](https://apis.io/apis/us-dot/us-dot-supplement-chart-api/) — The Supplement Chart API from U.S. Department of Transportation — 2 operation(s) for supplement chart .
- [U.S. Department of Transportation Terminal Area Charts API](https://apis.io/apis/us-dot/us-dot-terminal-area-charts-api/) — The Terminal Area Charts API from U.S. Department of Transportation — 2 operation(s) for terminal area charts.
- [U.S. Department of Transportation TIM API](https://apis.io/apis/us-dot/us-dot-tim-api/) — The TIM API from U.S. Department of Transportation — 2 operation(s) for tim.
- [U.S. Department of Transportation US Terminal Procedures Publication (TPP) API](https://apis.io/apis/us-dot/us-dot-us-terminal-procedures-publication-tpp-api/) — The US Terminal Procedures Publication (TPP) API from U.S. Department of Transportation — 2 operation(s) for us terminal procedures publication (tpp).
- [U.S. Department of Transportation US VFR Wall Planning Chart API](https://apis.io/apis/us-dot/us-dot-us-vfr-wall-planning-chart-api/) — The US VFR Wall Planning Chart API from U.S. Department of Transportation — 2 operation(s) for us vfr wall planning chart.
- [U.S. Department of Transportation Version API](https://apis.io/apis/us-dot/us-dot-version-api/) — The Version API from U.S. Department of Transportation — 1 operation(s) for version.
- [U.S. Department of Transportation VFR Helicopter Route Chart API](https://apis.io/apis/us-dot/us-dot-vfr-helicopter-route-chart-api/) — The VFR Helicopter Route Chart API from U.S. Department of Transportation — 4 operation(s) for vfr helicopter route chart.
- [FMCSA SaferBus API](https://apis.io/apis/us-dot/fmcsa-saferbus-api/) — The FMCSA SaferBus API is a RESTful service making available safety performance data for U.S. DOT-registered bus companies. It enables developers to build…
- [NHTSA Datasets and APIs](https://apis.io/apis/us-dot/nhtsa-datasets-api/) — NHTSA provides public datasets and APIs covering vehicle safety complaints, recalls, safety ratings (NCAP), and defect investigations. Complaint data…
- [DOT Open Data Portal](https://apis.io/apis/us-dot/dot-data-portal/) — The U.S. Department of Transportation Open Data Portal provides access to transportation datasets published by DOT agencies including FMCSA, NHTSA, FTA,…
- [U.S. Department of Transportation Child Seats API](https://apis.io/apis/us-dot/us-dot-childseats-api/) — Child Seat search and list endpoints
- [U.S. Department of Transportation Equipment API](https://apis.io/apis/us-dot/us-dot-equipment-api/) — Equipment search and list endpoints
- [U.S. Department of Transportation Ewr API](https://apis.io/apis/us-dot/us-dot-ewr-api/) — Early Warning Report endpoints
- [U.S. Department of Transportation Foreign Campaigns API](https://apis.io/apis/us-dot/us-dot-foreigncampaigns-api/) — Foreign Campaign search and list endpoints
- [U.S. Department of Transportation Safety Issues API](https://apis.io/apis/us-dot/us-dot-safetyissues-api/) — Recalls, Investigations, Complaints, and Manufacturer Communications
- [U.S. Department of Transportation Tires API](https://apis.io/apis/us-dot/us-dot-tires-api/) — Tire search and list endpoints
- [U.S. Department of Transportation Vehicles API](https://apis.io/apis/us-dot/us-dot-vehicles-api/) — Vehicle search and list endpoints

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [Us Dot Event Surfaces](https://apis.io/asyncapis/us-dot/us-dot-event-surfaces/)
- [USDOT ITS JPO Operational Data Environment (ODE) — Kafka event surface](https://apis.io/asyncapis/us-dot/us-dot-its-jpo-ode-asyncapi/)

#### Event channels (32)

Individual events and webhooks the provider emits.

- [topic.Asn1DecoderInput](https://apis.io/channels/us-dot/topic-asn1decoderinput/)
- [topic.Asn1DecoderOutput](https://apis.io/channels/us-dot/topic-asn1decoderoutput/)
- [topic.Asn1EncoderInput](https://apis.io/channels/us-dot/topic-asn1encoderinput/)
- [topic.Asn1EncoderOutput](https://apis.io/channels/us-dot/topic-asn1encoderoutput/)
- [topic.FilteredOdeBsmJson](https://apis.io/channels/us-dot/topic-filteredodebsmjson/)
- [topic.FilteredOdeSpatJson](https://apis.io/channels/us-dot/topic-filteredodespatjson/)
- [topic.FilteredOdeTimJson](https://apis.io/channels/us-dot/topic-filteredodetimjson/)
- [topic.OdeBsmJson](https://apis.io/channels/us-dot/topic-odebsmjson/)
- [topic.OdeDriverAlertJson](https://apis.io/channels/us-dot/topic-odedriveralertjson/)
- [topic.OdeMapJson](https://apis.io/channels/us-dot/topic-odemapjson/)
- [topic.OdePsmJson](https://apis.io/channels/us-dot/topic-odepsmjson/)
- [topic.OdeRawEncodedBSMJson](https://apis.io/channels/us-dot/topic-oderawencodedbsmjson/)
- [topic.OdeRawEncodedMAPJson](https://apis.io/channels/us-dot/topic-oderawencodedmapjson/)
- [topic.OdeRawEncodedPSMJson](https://apis.io/channels/us-dot/topic-oderawencodedpsmjson/)
- [topic.OdeRawEncodedRSMJson](https://apis.io/channels/us-dot/topic-oderawencodedrsmjson/)
- [topic.OdeRawEncodedRTCMJson](https://apis.io/channels/us-dot/topic-oderawencodedrtcmjson/)
- [topic.OdeRawEncodedSDSMJson](https://apis.io/channels/us-dot/topic-oderawencodedsdsmjson/)
- [topic.OdeRawEncodedSPATJson](https://apis.io/channels/us-dot/topic-oderawencodedspatjson/)
- [topic.OdeRawEncodedSRMJson](https://apis.io/channels/us-dot/topic-oderawencodedsrmjson/)
- [topic.OdeRawEncodedSSMJson](https://apis.io/channels/us-dot/topic-oderawencodedssmjson/)
- [topic.OdeRawEncodedTIMJson](https://apis.io/channels/us-dot/topic-oderawencodedtimjson/)
- [topic.OdeRsmJson](https://apis.io/channels/us-dot/topic-odersmjson/)
- [topic.OdeRtcmJson](https://apis.io/channels/us-dot/topic-odertcmjson/)
- [topic.OdeSdsmJson](https://apis.io/channels/us-dot/topic-odesdsmjson/)
- [topic.OdeSpatJson](https://apis.io/channels/us-dot/topic-odespatjson/)
- …and 7 more published on APIs.io

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [us-dot](https://apis.io/servers/us-dot/us-dot/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Us Dot Agentic Access](https://apis.io/agentic-access/us-dot/us-dot-agentic-access/)

#### JSON Schema (6)

The data models the API reads and writes.

- [GeoJSON Bounding Box](https://apis.io/schemas/us-dot/us-dot-wzdx-4.2-boundingbox/)
- [WZDx v4.2 DeviceFeed](https://apis.io/schemas/us-dot/us-dot-wzdx-4.2-devicefeed/)
- [Direction Enumerated Type](https://apis.io/schemas/us-dot/us-dot-wzdx-4.2-direction/)
- [WZDx Feed Information](https://apis.io/schemas/us-dot/us-dot-wzdx-4.2-feedinfo/)
- [Road Event Feature (GeoJSON Feature)](https://apis.io/schemas/us-dot/us-dot-wzdx-4.2-roadeventfeature/)
- [WZDx v4.2 Work Zone Feed](https://apis.io/schemas/us-dot/us-dot-wzdx-4.2-workzonefeed/)

#### Examples (2)

Example requests and responses.

- [Us Dot Faa Sas Submit Discrepancies Request](https://apis.io/examples/us-dot/us-dot-faa-sas-submit-discrepancies-request/)
- [Us Dot Faa Sas Submit Discrepancies Response](https://apis.io/examples/us-dot/us-dot-faa-sas-submit-discrepancies-response/)

#### Collections (5)

Postman and Open Collection request collections.

- [Aeronautic Product Release API](https://apis.io/collections/us-dot/open-us-dot-faa-aeronautic-product-release-api/)
- [PRD Air Carrier API](https://apis.io/collections/us-dot/open-us-dot-faa-air-carrier-prd-api/)
- [Airport Status Web Service](https://apis.io/collections/us-dot/open-us-dot-faa-airport-status-web-service/)
- [sas-api](https://apis.io/collections/us-dot/open-us-dot-faa-safety-assurance-system-api/)
- [ODE REST API](https://apis.io/collections/us-dot/open-us-dot-its-jpo-ode-rest-api/)

#### Overlays (5)

OpenAPI overlays, including conversational phrasing for each operation.

- [Us Dot Faa Aeronautic Product Release Api Overlay](https://apis.io/overlays/us-dot/us-dot-faa-aeronautic-product-release-api-overlay/)
- [Us Dot Faa Air Carrier Prd Overlay](https://apis.io/overlays/us-dot/us-dot-faa-air-carrier-prd-overlay/)
- [Us Dot Faa Airport Status Web Service Overlay](https://apis.io/overlays/us-dot/us-dot-faa-airport-status-web-service-overlay/)
- [Us Dot Faa Safety Assurance System Overlay](https://apis.io/overlays/us-dot/us-dot-faa-safety-assurance-system-overlay/)
- [Us Dot Its Jpo Ode Rest Api Overlay](https://apis.io/overlays/us-dot/us-dot-its-jpo-ode-rest-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Us Dot Authentication](https://apis.io/security/us-dot/us-dot-authentication/)
- [Us Dot Domain Security](https://apis.io/security/us-dot/us-dot-domain-security/)
- [Us Dot Vulnerability Disclosure](https://apis.io/security/us-dot/us-dot-vulnerability-disclosure/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.transportation.gov/)
- [Documentation](https://api.faa.gov/s/)
- [Getting started](https://mobile.fmcsa.dot.gov/QCDevsite/docs/getStarted)
- [API reference](https://dev.socrata.com/docs/queries/)
- [Sign up](https://mobile.fmcsa.dot.gov/QCDevsite/logingovInfo)
- [Support](https://api.faa.gov/s/help)
- [Blog](https://www.transportation.gov/blog)
- [Security](https://www.transportation.gov/vulnerability-disclosure-policy)
- [Terms of service](https://www.transportation.gov/web-policies)
- [Privacy policy](https://www.transportation.gov/privacy)
- [GitHub](https://github.com/usdot-jpo-ode)
- [Status](https://status.socrata.com/)

## API Evangelist rating

**Kin Score 49.5** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 89.3 |
| Contract quality | 54.9 |
| Contract governance | 4.5 |
| Operational transparency | 44.7 |
| Developer ergonomics | 58.9 |
| Access clarity | 34.2 |

**Agent readiness 30.8** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | — |

**Regulatory alignment 30.4** — Government & Public Sector

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/us-dot/](https://apis.io/providers/us-dot/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for U.S. Department of Transportation: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/us-dot/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

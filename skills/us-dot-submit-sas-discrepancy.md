---
name: Submit a passenger hazmat discrepancy to the FAA SAS
description: >-
  Report hazardous-material discrepancies found on passengers or in passenger baggage
  into the FAA Safety Assurance System. Credentialed write; carries passenger PII.
generated: '2026-07-28'
method: generated
provider: us-dot
api: openapi/us-dot-faa-safety-assurance-system-api-openapi.yml
base_url: https://external.apic4e.faa.gov/axh-sasp-api/sas
operations: []
operations_note: >-
  The FAA spec declares NO operationId on this operation. Address it by path and method:
  POST /axhsubmitdiscrepancies. Do not invent an operationId and do not trust one you
  find in a generated client.
---

# Submit a passenger hazmat discrepancy to the FAA SAS

One operation: `POST /axhsubmitdiscrepancies`. An air carrier reports hazardous materials
discovered on a passenger or in passenger baggage into the FAA Safety Assurance System.

## STOP — read this before wiring an agent to it

This request body carries **passenger personally identifiable information**: full name,
street address, city, state, ZIP, country, phone, email — plus a **PNR locator** and the
reporting employee's name, phone and email.

- Never log the request body.
- Never cache it.
- Never place it in general-purpose agent context or a prompt.
- Treat every field under `Discrepancies[].Passenger*` as regulated PII.

This is the most sensitive payload in the entire U.S. DOT API surface area, and it is
the reason the endpoint is credential-gated.

## Auth

Two headers, **both required**:

- `X-API-KEY`
- `X-APP-ID`

Both are declared as `apiKey` securitySchemes in the spec, but the spec applies **no**
`security` requirement to the operation — so a generated client will happily omit them
and get a gateway 401 (`{"message":"Unauthorized","http_status_code":401}`).

Credentials come from the FAA developer portal at `https://api.faa.gov/s/`. There is no
self-serve signup and no usable staging host (the FAA's internal entrypoint
`https://internal.apic4e.faa.gov/axh-sasp-api/sas` is not publicly reachable).

## Base URL

`https://external.apic4e.faa.gov/axh-sasp-api/sas`

The spec declares `servers[0].url` as `"/"` — a build artefact. Use the entrypoint above,
which is what the FAA Gravitee portal catalogue publishes.

## Request

`Content-Type: application/json`.

Required at the top level: `ReporterName`, `AirCarrierName`, `ReporterEmail`,
`ReporterDSGN`, `Discrepancies`. Optional: `ReporterPhone`.

Each entry in `Discrepancies[]` requires `HazmatItems`, and may carry
`AirCarrierDSGN`, `FlightOperatedByDSGN`, `CarrierRecordId`, `AirportCode`,
`LocationOfDiscovery`, `DiscrepancyDate`, `PnrLocator`, `PassengerFullName`,
`PassengerAddress`, `PassengerCity`, `PassengerStateCode`, `PassengerZipCode`,
`PassengerCountryCode`, `PassengerPhone`, `PassengerEmail`, `FlightNumber`,
`DestinationAirportCode`.

Each `HazmatItems[]` entry: `HazmatDescription`, `Quantity`, `HazmatType`, `HazmatClass`.

Every field is typed `string` — including `DiscrepancyDate`, which the FAA's own example
formats as `MM/DD/YYYY`.

A complete FAA-published sample payload is at
`examples/us-dot-faa-sas-submit-discrepancies-request.json`.

## Response

`200` with:

```json
{
  "confirmationMessage": "...",
  "totalDiscrepanciesImported": 2,
  "discrepanciesImportedWithErrors": "record failed due to data issues",
  "errorMessage": "..."
}
```

**A 200 does not mean everything landed.** Partial success is reported in the body:
compare `totalDiscrepanciesImported` against the length of the array you sent, and read
`discrepanciesImportedWithErrors` and `errorMessage` on every call.

## Retries — the hazard

There is **no** idempotency key, no dedupe field and no submission id. A retried POST
imports the discrepancies **again**.

On a timeout or a 5xx, do **not** blind-retry. Reconcile first: if you cannot determine
whether the submission landed, escalate to a human rather than resubmitting. On a partial
success, resubmit **only** the failed discrepancy entries, never the whole batch.

## Agentic posture

`action-class: acting`, `consequence: write`, `subject: required`, token max-TTL 900s,
`audit: required`. See `agentic-access/us-dot-agentic-access.yml`.

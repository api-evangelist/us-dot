---
name: Deposit a Traveler Information Message to a roadside unit (ODE)
description: >-
  Write, query and delete SAE J2735 Traveler Information Messages on physical roadside
  units through a self-hosted USDOT ITS JPO Operational Data Environment. Safety-critical.
generated: '2026-07-28'
method: generated
provider: us-dot
api: openapi/us-dot-its-jpo-ode-rest-api-openapi.yml
base_url: null
operations:
  - getVersion
  - tim_query
  - tim_post
  - tim_put
  - tim_delete
  - snmp_get
  - pdm_post
---

# Deposit a Traveler Information Message to a roadside unit (ODE)

The USDOT ITS Joint Program Office Operational Data Environment is the reference
connected-vehicle data platform. Its REST API writes SAE J2735 Traveler Information
Messages onto **physical roadside units** on real highways.

## Read this first

**There is no U.S. DOT-hosted ODE.** The Swagger document declares `host: yourhostname`
— a literal placeholder. The ODE is Apache 2.0 software an operator deploys against its
own Kafka cluster and its own roadside hardware
(`https://github.com/usdot-jpo-ode/jpo-ode`). Point this skill at your operator's host,
never at a DOT domain.

**This is a safety-critical control surface.** `tim_post`, `tim_put` and `tim_delete`
change what messages a roadside unit broadcasts to vehicles. `snmp_get` and `pdm_post`
talk directly to field hardware. Treat every write as
`consequence: safety-critical`, `human-in-the-loop: required`, token max-TTL 120s,
`proof-of-possession: true`, `audit: required` — see
`agentic-access/us-dot-agentic-access.yml`.

## Step 1 — confirm you are talking to the ODE you think you are

Call **`getVersion`** — `GET /version`. Returns a `versionResponse`. Do this before every
session; it is the only cheap, side-effect-free operation on the API.

## Step 2 — read current state

Call **`tim_query`** — `POST /tim/query`. Queries an RSU for the TIM index slots that are
currently set.

`tim_query` declares a **408 Timeout** response with no safe-retry contract. A timeout
means the RSU did not answer — it does **not** tell you the RSU's state.

## Step 3 — write

| Operation | Method / path | Effect |
|---|---|---|
| `tim_post` | `POST /tim` | Create a TIM (also deposits to the SDX) |
| `tim_put` | `PUT /tim` | Update an existing TIM |
| `tim_delete` | `DELETE /tim` | Remove a TIM from an RSU index slot |

Payloads validate against the `TravelerInputData` definition in the spec. A malformed
payload returns **400 "Error in body request"**.

## Step 4 — probe data messages

- **`pdm_post`** — `POST /pdm` deposits a Probe Data Management message. Also returns
  400 on a bad `ProbeDataManagement` payload.
- **`snmp_get`** — SNMP query against the RSU. Declares **408 Timeout**.

## The idempotency hazard — the single most important rule here

The ODE defines **no idempotency key** on any write, and `tim_query` and `snmp_get`
declare a 408 with no retry semantics.

> On a 408 or a 5xx, **do not assume the write did not land.**

Correct recovery sequence:

1. Do **not** retry the write.
2. Call `tim_query` to read the RSU's actual index state.
3. Reconcile against your intended state.
4. Only then issue a corrective `tim_put` or `tim_delete`.

For an autonomous agent this is a hard stop: escalate to a human operator rather than
retrying a safety-critical write against uncertain state.

## Errors

| Status | Where | Meaning |
|---|---|---|
| 400 | `tim_post`, `pdm_post` | Value input error in the submitted payload |
| 408 | `tim_query`, `snmp_get` | RSU did not respond — **state unknown** |
| 500 | any | See the response body or the ODE User Guide |

## The event surface behind the REST API

The REST API is the thin edge of a Kafka platform. 35 topics are declared in the ODE's own
configuration — `topic.OdeTimJson`, `topic.OdeBsmJson`, `topic.OdeSpatJson`,
`topic.FilteredOdeBsmJson`, `topic.SDWDepositorInput` and more. A deposited TIM lands on
`topic.OdeTimJson`; the privacy-filtered projections land on the `Filtered*` topics.

Full channel catalogue: `asyncapi/us-dot-its-jpo-ode-asyncapi.yml`.

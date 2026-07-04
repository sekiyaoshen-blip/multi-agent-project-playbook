# Current Technical Design

Last updated: YYYY-MM-DD

This document is the current technical implementation snapshot. It should let a developer or AI agent understand how the project is built and continue development without reading old chat history.

Keep this file aligned with `docs/current-prd.md`. Do not use it as a debug log or full architecture history.

## Snapshot Metadata

- Project:
- Owner:
- Current phase:
- Product source:
  - `docs/current-prd.md`
- Current workboard:
  - `docs/current-work.md`
- Related roadmap:
  - `docs/roadmap.md`
- Related ADRs:
  - `docs/decisions/ADR-XXXX-title.md`

## Architecture Summary

Describe the current architecture in one or two paragraphs.

## Runtime Topology

| Component / Service | Responsibility | Runtime / Process | Owner Module | Notes |
|---|---|---|---|---|
| <component> | <responsibility> | <runtime> | `<module>` | <notes> |

## Repository / Module Map

| Path / Package | Owns | Depends On | Exposes | Notes |
|---|---|---|---|---|
| `path/to/module` | <scope> | <deps> | <API/schema/event/UI> | <notes> |

## Key Data Models

| Model / Table / Entity | Purpose | Owner | Important Fields | Notes |
|---|---|---|---|---|
| `<model>` | <purpose> | `<module>` | `<field>` | <notes> |

## APIs / Contracts / Events

| Contract | Type | Owner | Consumers | Stability | Link |
|---|---|---|---|---|---|
| `<contract>` | API/schema/event/config/CLI | `<module>` | <consumer> | stable / changing / draft | <link> |

## Important Flows

### Flow: <Name>

- Trigger:
- Components involved:
- Data path:
- Error handling:
- Verification path:

## Configuration / Deployment

- Runtime services:
- Environment variables:
- Deployment assumptions:
- External dependencies:
- Secrets handling:

## Verification Strategy

| Area | Checks | Command / Manual Check | Owner | Last Known State |
|---|---|---|---|---|
| <area> | <checks> | `<command>` | `<module>` | passing / failing / unknown |

## Security / Performance / Cost Notes

- Security:
- Performance:
- Cost:
- Reliability:

## Current Technical Debt / Known Limitations

| Item | Impact | Owner | Priority | Planned Action |
|---|---|---|---|---|
| <item> | <impact> | `<module>` | P0/P1/P2/P3 | <action> |

## Module Technical Design Index

For large projects, keep this global design short and split details into module technical designs:

- `docs/modules/<module>/current-technical-design.md`

## Update Rules

Update this document when:

- architecture changes,
- module boundaries change,
- APIs, schemas, events, shared types, configs, deployment, or data flows change,
- an ADR is accepted and affects current implementation,
- a meaningful refactor changes how future developers should work,
- current implementation diverges from this document.

Do not put raw logs, transient debugging attempts, or long historical alternatives here. Use runbooks, Return Packets, ADRs, or archives instead.

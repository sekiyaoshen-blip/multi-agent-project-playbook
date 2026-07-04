# Current PRD

Last updated: YYYY-MM-DD

This document is the current product-requirements snapshot. It is the fastest onboarding document for understanding what the product is, what it currently does, and what product behavior is expected now.

Keep this file current after meaningful product iterations. Do not use it as a changelog or todo list.

## Snapshot Metadata

- Product / project:
- Owner:
- Current phase:
- Related roadmap:
  - `docs/roadmap.md`
- Related current workboard:
  - `docs/current-work.md`
- Related technical design:
  - `docs/current-technical-design.md`
- Related ADRs:
  - `docs/decisions/ADR-XXXX-title.md`

## Product Summary

Describe the current product in one or two paragraphs.

## Target Users / Personas

| User / Persona | Need / Pain | Current Support | Notes |
|---|---|---|---|
| <persona> | <need> | supported / partial / planned | <notes> |

## Current Product Surfaces

- Admin:
- User portal:
- API / integration surface:
- CLI / automation surface:
- Other:

## Current Capabilities

| Capability | User Outcome | Current State | Entry Points | Notes |
|---|---|---|---|---|
| <capability> | <outcome> | working / partial / planned / deprecated | <route/API/UI> | <notes> |

## Current User Workflows

### Workflow: <Name>

- Actor:
- Trigger:
- Main path:
- Success state:
- Failure / edge cases:
- Related modules:

## Product Requirements

| Requirement ID | Requirement | Priority | State | Owner Module | Source / Link |
|---|---|---|---|---|---|
| PRD-001 | <requirement> | P0/P1/P2/P3 | active / partial / planned / deferred | `<module>` | <link> |

## Current Non-Goals / Out Of Scope

- <non-goal>
- <non-goal>

## Product Constraints

- Compliance / legal:
- Platform:
- Performance:
- Cost:
- Timeline:
- Localization / accessibility:

## Open Product Questions

| Question | Owner | Blocks | Needed By | Current Bias |
|---|---|---|---|---|
| <question> | <owner> | <work> | YYYY-MM-DD | <current answer if any> |

## Module PRD Index

For large projects, keep this global PRD short and split product requirements into module PRDs:

- `docs/modules/<module>/current-prd.md`

## Update Rules

Update this document when:

- user-visible behavior changes,
- product scope changes,
- requirements are added, removed, accepted, deferred, or deprecated,
- workflows, personas, or product surfaces change,
- a release, milestone, or optimization changes current product truth.

Do not put implementation details, debug notes, task logs, or long historical records here. Link to `docs/current-technical-design.md`, `docs/current-work.md`, ADRs, or archives instead.

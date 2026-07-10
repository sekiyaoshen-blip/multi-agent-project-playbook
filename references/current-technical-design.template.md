# Current Technical Design

Last updated: YYYY-MM-DD

Current architecture and accepted implementation truth only. Reuse existing
architecture/design docs when they already own this responsibility. Do not use
this file as a debug log or task history.

## Architecture Summary

- System shape:
- Important runtime boundaries:
- Current implementation constraints:

## Module Map

| Path / Component | Responsibility | Owner Module | Depends On | Exposes |
|---|---|---|---|---|
| `path/to/module` | <scope> | `<module>` | <dependencies> | <API/schema/event/UI> |

## Data And Contracts

| Model / Contract | Type | Owner | Consumers | Stability | Link |
|---|---|---|---|---|---|
| `<name>` | model/API/schema/event/config/CLI | `<module>` | <consumers> | stable / changing / draft | <link> |

## Important Flows

### <Flow>

- Trigger:
- Components/data path:
- Error handling:
- Verification path:

## Runtime And Deployment

- Runtime services/processes:
- External dependencies:
- Configuration assumptions:
- Secrets handling:
- Deployment/recovery assumptions:

## Verification

| Area | Check | Command / Evidence | Current State |
|---|---|---|---|
| <area> | <check> | `<command>` | passing / failing / unknown |

## Active Technical Risks / Debt

| Item | Impact | Owner | Priority | Next Needed Outcome |
|---|---|---|---|---|
| <item> | <impact> | `<module>` | P0/P1/P2/P3 | <outcome> |

## Links

- Current product truth: `docs/current-prd.md`
- Current outcomes/WIP: `docs/current-work.md`
- Durable decisions: `docs/decisions/`
- Optional module design docs: `docs/modules/<module>/current-technical-design.md`

Update when architecture, module boundaries, APIs, schemas, events, shared
types, config, deployment, data flows, or accepted implementation strategy
changes. Keep temporary plans and debug detail in native tasks; use optional
recovery notes or Portable Controls only when needed.

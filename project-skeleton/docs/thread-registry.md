# Long-Lived Task Registry

Last updated: YYYY-MM-DD

This file maps stable project roles/modules to long-lived visible native tasks.
It is an identity and ownership map, not a duplicate task queue or event log.

## Main Task

- Role: planning, decomposition, routing, cross-module decisions, result review
- Native task ID/link: <native task ID or link>
- State: active | paused | replaced
- Replaces: none | <previous task ID/link>

## Module Task Map

| Module / Role | Ownership Scope | Native Task ID / Link | State | Status | Handoff | Runbook (Optional) | Replaces |
|---|---|---|---|---|---|---|---|
| `<module>` | <stable owned scope> | <native task ID/link> | active | `docs/modules/<module>/status.md` | `docs/modules/<module>/handoff.md` | `docs/modules/<module>/runbook.md` | none |

Use `Unavailable in current runtime` when the current product cannot expose a
stable native identity. Do not invent IDs or store credentials, cookies, tokens,
private URLs, or signed links.

## Ownership Boundaries

| Module / Role | Owns | Does Not Own | Escalate To Main Task When |
|---|---|---|---|
| `<module>` | <implementation and local verification> | <other module contracts or decisions> | <boundary, product, architecture, security, or priority decision> |

## Routing Rules

- Reuse the registered visible module task for module-owned work.
- Use native task messaging for ordinary dispatch and native task reads for
  progress/result review.
- Do not register temporary subagents used for bounded disposable work.
- Create or replace a visible module task only when the boundary is stable and
  the required user/runtime authorization exists.
- When replacing a task, preserve the previous identity in `Replaces`, update
  the new task with the compact module handoff, then archive stale mappings.
- Keep active work state in the native task system and `docs/current-work.md` or
  the project issue tracker. Do not copy every task row here.

## Optional Portable Controls

Enable only when native task state is insufficient for recovery, audit,
asynchronous delivery, or cross-tool work.

| Control | Enabled | Reason / Scope |
|---|---|---|
| `docs/thread-runs/` | no | <long/high-risk/resumable task need> |
| Return Inbox | no | <cross-tool or unreliable native delivery> |
| `docs/.locks/` | no | <broad shared-doc compaction concurrency> |
| `docs/archive/` | no | <useful history removed from active context> |

If Portable Controls are enabled, keep their active indexes in the relevant
control files. Do not expand this registry into a second queue.

## Open Ownership Questions

- Question:
  - Modules affected:
  - Decision owner:
  - Needed by:

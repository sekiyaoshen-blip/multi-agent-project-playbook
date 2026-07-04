# Current Workboard

Last updated: YYYY-MM-DD

This document is the current active-work snapshot. It tells humans and AI agents what the project is trying to accomplish now, what is in progress, what is next, what is deferred, and what risks need attention.

It is not a full task history. Keep it short and actionable.

## What-To-Do Only Rule

This document records **what needs to be done**, not **how it should be done**.

Use `current-work.md` to preserve the shared problem set, priority, ownership, state, dependencies, risks, and decisions needed. Do not prescribe implementation strategy, step-by-step plans, architecture choices, prompt recipes, or preferred technical solutions here.

This keeps the workboard solution-neutral so different humans or AI agents can approach the same problem from different angles.

Put implementation details elsewhere:

- Product behavior and requirements: `docs/current-prd.md`
- Technical architecture and accepted implementation approach: `docs/current-technical-design.md`
- Durable decisions and tradeoffs: `docs/decisions/`
- Dispatch-specific execution instructions: `docs/thread-runs/<task-id>.md`
- Module-local debugging and recovery context: module `runbook.md`
- Main-thread relevant module updates: module `handoff.md`

## Current Core Objectives

| Objective ID | Objective / Desired Outcome | Priority | Owner | State | Success Signal |
|---|---|---|---|---|---|
| OBJ-001 | <what outcome should exist> | P0/P1/P2/P3 | Main / `<module>` | active / blocked / done | <observable signal> |

## In Progress Now

| Work ID | Work Item / Problem To Resolve | Owner Thread / Module | State | Related Task / Run | Next Needed Outcome |
|---|---|---|---|---|---|
| WORK-001 | <what problem or outcome is being worked on> | `<module>` | running / blocked / review | `docs/thread-runs/<task-id>.md` | <what should be true next> |

## Next Up

| Item / Outcome Needed | Priority | Owner | Why Next | Dependencies |
|---|---|---|---|---|
| <what should be addressed next> | P0/P1/P2/P3 | `<module>` | <reason> | <dependency> |

## Later / Low-Priority Follow-Ups

These are useful but not current focus. Move stale or abandoned items to archive.

- <follow-up outcome needed>
- <optimization opportunity>
- <cleanup needed>

## Risks / Watchlist

Record the risk and the next check or decision needed. Do not write detailed mitigation plans here unless the mitigation is already an accepted requirement or decision.

| Risk | Impact | Owner | Trigger | Next Check / Decision Needed |
|---|---|---|---|---|
| <risk> | <impact> | <owner> | <trigger> | <what needs to be checked or decided> |

## Open Decisions Needed

Record the decision that must be made and what it blocks. Do not use this section to debate full solution proposals; put durable tradeoffs in ADRs or technical design docs.

| Decision Needed | Owner | Needed By | Blocks | Decision Frame / Constraints |
|---|---|---|---|---|
| <decision> | Main / `<module>` | YYYY-MM-DD | <work> | <constraints or decision boundary> |

## Recently Accepted / Closed

Keep only recent items that still matter for planning. Archive old closed work.

- <closed item>: <result / link>

## Links

- Current PRD: `docs/current-prd.md`
- Current technical design: `docs/current-technical-design.md`
- Roadmap: `docs/roadmap.md`
- Thread registry / active dispatch queue: `docs/thread-registry.md`
- Active task records: `docs/thread-runs/`

## Update Rules

Update this document when:

- the active objective set changes,
- work starts, blocks, returns, or closes,
- priorities change,
- a follow-up should be kept but is not urgent,
- a risk or open decision becomes important for near-term planning,
- a milestone closes or new planning cycle starts.

Do not duplicate full dispatch queue rows, Return Packets, historical task detail, implementation plans, step-by-step approaches, prompt drafts, or technical solution details here. Link to `docs/thread-registry.md`, `docs/thread-runs/<task-id>.md`, `docs/current-technical-design.md`, ADRs, module docs, or archives.

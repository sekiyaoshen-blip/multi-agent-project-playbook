# Thread Operating Model

Last updated: YYYY-MM-DD

This project uses native visible tasks for long-lived module work and project
docs for durable truth. It does not mirror every native task event into files.

## Contents

- Principles
- Roles and ownership
- Long-lived visible module tasks
- Dispatch and return flow
- Temporary subagents
- Durable project state
- Dispatch-time model routing
- Portable Controls
- Docs compaction and locks
- Cross-tool compatibility
- Security and maintenance

## Principles

1. **Native-first:** use ChatGPT Desktop/Codex task tools for visible task
   creation, discovery, continuation, routing, progress inspection, forking,
   handoff, and archiving when available.
2. **Long-lived modules:** route module-owned implementation to the registered
   visible module task. Do not replace it with a temporary subagent.
3. **Docs for durable truth:** keep product behavior, architecture, ownership,
   accepted decisions, risks, and current outcomes in project docs.
4. **Native state for transient work:** keep prompts, progress events, temporary
   plans, and ordinary task results in native task history.
5. **Conditional controls:** add thread-runs, Return Packets, locks, and archives
   only when risk, recovery, audit, or cross-tool operation requires them.
6. **One primary home:** link to facts instead of copying them across docs.

## Roles And Ownership

### Main Task

The main task owns:

- product direction and priority
- module boundaries and ownership
- task decomposition and routing
- cross-module decisions and ADR review
- result review and integration
- project-state hygiene

The main task should not become the implementation task for every module.

### Module Tasks

Each stable module may have one long-lived visible task. That task owns:

- implementation and local debugging inside the module
- module-local verification
- compact module status and handoff
- recovery notes only when native history is insufficient
- escalation of contract, product, security, or cross-module decisions

Module boundaries are ownership lines, not hard walls. Small adjacent changes
are acceptable when they are low risk, easy to review, and do not change another
module's public contract, data ownership, permissions, billing, routing, or
deployment assumptions. Route substantial work to the owning module task.

### Temporary Subagents

Use temporary subagents for bounded disposable work such as:

- focused research or code search
- independent review
- narrow test or verification work
- low-risk one-off transformations
- parallel side work whose result is consumed by the current task

Do not use a temporary subagent for work that should build durable module
memory, maintain module ownership, or continue across milestones.

## Long-Lived Visible Module Tasks

Keep a compact mapping in `docs/thread-registry.md`:

- module or role
- ownership scope
- native task ID/link when available
- current state
- status/handoff paths
- replacement relationship when a task is superseded

Do not duplicate native task progress, prompts, full history, or every dispatch
in the registry.

When a module task is missing:

1. Confirm that the module boundary is stable enough to justify a long-lived
   task.
2. Obtain or rely on explicit user authorization before creating a separate
   visible task when the current product requires it.
3. Start it with the module startup prompt.
4. Record the returned native identity/link in the registry.

If a native identity is unavailable, write `Unavailable in current runtime`.
Never invent IDs or store credentials, cookies, or signed URLs.

## Dispatch And Return Flow

### Main Task Dispatch

When work is parallelizable or belongs to a module:

1. Classify the work: decision, module implementation, cross-module feature,
   investigation, review, or verification.
2. Identify the owning module. Assign a lead module for cross-module features.
   Stabilize the shared contract before fully parallel execution; downstream
   modules may proceed only on slices that do not require inventing it.
3. Check `docs/thread-registry.md` for the existing visible module task.
4. Classify the concrete task and choose supported `model` and `thinking`
   parameters using Dispatch-Time Model Routing below.
5. Send a compact task payload through the native task messaging tool, passing
   both selected parameters explicitly.
6. Use the native task state for progress unless Portable Controls are needed.
7. Review the result through native delivery or by reading the target task.
8. Update durable docs only when project truth changed.

Use this minimum task payload:

- desired outcome
- why the target module owns it
- acceptance criteria
- constraints and dependencies
- relevant files/docs
- expected verification
- when to escalate to the main task
- selected model/Thinking profile and one-line reason

Do not dispatch vague ideas, duplicate active work, or tiny questions that the
current task can resolve immediately.

### Return Priority

Use return channels in this order:

1. Native result delivery or main-task inspection of the module task.
2. Compact module `handoff.md` update when the result must survive native task
   history, tool, or account boundaries.
3. Return Packet only when cross-tool/asynchronous work, high-risk audit,
   unreliable native delivery, or explicit project policy requires it.

Do not require both native delivery and a Return Packet for routine work.

The main task should promote only durable outcomes:

- accepted product or technical truth
- contract or architecture decisions
- changed ownership or priority
- material risk or verification gaps
- preserved follow-up work

Do not promote raw logs, full transcripts, abandoned local attempts, or routine
file lists.

## Durable Project State

Reuse existing project docs first. The names below are defaults, not a mandate.

| Responsibility | Default Home |
|---|---|
| Stable mission, users, constraints | `docs/project-brief.md` |
| Current product behavior | `docs/current-prd.md` or existing PRD |
| Current architecture and implementation | `docs/current-technical-design.md` or existing design docs |
| Current outcomes, WIP, risks, decisions needed | `docs/current-work.md` or issue tracker |
| Long-lived visible task identities and ownership | `docs/thread-registry.md` |
| Module current state | `docs/modules/<module>/status.md` |
| Main-task-relevant module summary | `docs/modules/<module>/handoff.md` |
| Recovery context not reliable in native history | `docs/modules/<module>/runbook.md` |
| Durable decisions | `docs/decisions/ADR-*.md` |

`docs/current-work.md` records **what outcome is needed**, not the implementation
strategy. Put accepted implementation truth in technical design, durable
tradeoffs in ADRs, and temporary execution plans in native tasks.

### Read Budget

Read only the active context needed for the current work.

Module tasks normally read:

1. `AGENTS.md`
2. their registry row and module status/handoff
3. relevant PRD, technical design, current-work, and ADR sections
4. runbook only when recovery context is needed

The main task normally reads:

1. `AGENTS.md`
2. project brief and relevant current snapshots
3. compact registry and module handoffs
4. relevant ADRs

Do not read every module runbook, historical task record, archive, or unrelated
ADR by default.

### Update Rule

Update docs only when durable state changed. Rewrite active docs as current
snapshots rather than appending a dated task log. Each fact has one primary
home; other docs link to it.

Do not create optional docs preemptively. Add a roadmap, global status,
module-level PRD/design, runbook, thread-run, Return Inbox, lock, or archive
only when its responsibility is real and not already covered.

## Dispatch-Time Model Routing

Every call to an existing visible task and every authorized creation of a new
visible task must select and pass explicit `model` and `thinking` parameters.
Do not inherit the target task's old settings or rely on the user's default.

### Classification Signals

Assess the concrete task before invocation:

- **Type:** lookup/docs, verification, implementation, review, debugging,
  architecture/decision, migration/operations, security/payment
- **Complexity:** deterministic, normal, ambiguous, or highly coupled
- **Risk:** low, moderate, high, or critical failure cost
- **Context:** short/local, multi-file/module, or long-history synthesis
- **Reversibility:** easy rollback, costly rollback, or irreversible step
- **Parallelism:** one owner, independent module slices, or tightly coupled work

### Routing Matrix

| Profile | Typical Work | Model Capability | Thinking |
|---|---|---|---|
| `fast` | formatting, simple docs, narrow lookup, lint/test check, low-risk deterministic fix | fastest capable | `low`; use `medium` when context is not trivial |
| `balanced` | normal implementation, clear bug fix, routine review, single-module work | balanced general | `medium`; use `high` for uncertainty or broader verification |
| `deep` | ambiguous bug, repeated failure, long context, cross-module contract, architecture, read-only auth/security/payment investigation | strongest available | `high` or `xhigh` |
| `critical` | executing/authorizing irreversible migration or production action, active financial/data/security loss, highest failure cost | strongest available | `max` |

Current GPT-5.6 mappings are typically Luna -> `fast`, Terra -> `balanced`, and
Sol -> `deep`/`critical`. Discover actual current model IDs from the active tool
schema. These names are examples, not durable project configuration.

Do not route from keywords alone. Reversible read-only work in a sensitive
domain is normally `deep`; reserve `critical` for the action/exposure itself.

### Invocation Rules

- Existing visible task: call `send_message_to_thread` with both `model` and
  `thinking` on every dispatch.
- New visible task: after required user authorization, call `create_thread`
  with both parameters selected for its first concrete task.
- New role-only task with no concrete work: use the current `balanced` mapping
  with `medium`; classify again on every later dispatch.
- Temporary subagent, when permitted: apply the same classification and pass
  explicit model/reasoning parameters supported by that tool.
- Include `Routing: <profile>; model=<id>; thinking=<effort>; reason=<short>` in
  the native prompt for observability. Do not duplicate routine routing data in
  project docs.
- Explicit user model/Thinking instructions take precedence.
- Use `ultra` only when the active invocation schema accepts it and the work
  genuinely benefits from that mode. If visible-task tools expose only up to
  `max`, do not send `ultra` to them.

### Fallback Safety

If a preferred model or effort is unavailable:

1. Re-read the active tool's supported model/Thinking values.
2. Choose the closest supported option that still satisfies the risk profile.
3. State the fallback in the native dispatch prompt.
4. Never silently downgrade `deep` or `critical` work below a safe level. Stop
   and ask the user if no supported option is adequate.

Only Portable Controls or audit-sensitive tasks should persist requested/actual
model details outside native task history.

## Portable Controls

Native task state is the default. Add file-based controls only when at least one
condition applies:

- work crosses Codex, Claude Code, another agent, automation, or a human queue
- the task is long-running, high-risk, resumable, or audit-sensitive
- native progress or return delivery is unavailable or unreliable
- the project explicitly requires a durable task ledger

Available controls:

- `docs/thread-runs/<task-id>.md`: compact checkpoint and resume state
- `docs/thread-runs/inbox/main/RET-*.md`: unprocessed Return Packets only
- `docs/.locks/context-compaction.lock`: broad shared-doc compaction ownership
- `docs/archive/`: useful history removed from active context

Do not mirror every native event. A thread-run should contain only the brief,
latest checkpoint, remaining work, verification, and recovery notes. A Return
Packet should contain only the result, verification, risks, and decision needed.

## Docs Compaction And Locks

Native conversation compaction and Memories do not clean project files. Use
LV2 controlled autonomous compaction only for project-doc hygiene.

Trigger a docs compaction check when:

- an active doc is materially oversized or hard to scan
- current docs contradict code, tests, ADRs, or each other
- handoff/runbook/registry contains stale or duplicated material
- a milestone closes or a long-lived task is replaced
- the user or an agent reports context confusion

Do not run a compaction check at every ordinary task startup.

LV2 may:

- rewrite active docs as current snapshots
- archive stale or historical detail
- remove processed Return Packets from the active inbox
- close or archive optional task records
- write a compact compaction note

LV2 must not:

- modify source, tests, production config, schemas, migrations, or credentials
- change ADR decisions, product direction, module ownership, roadmap priority,
  or public contracts
- resolve semantic conflict by guessing
- delete useful history without preserving a summary when history matters

Ordinary targeted doc edits do not need a compaction lock. Acquire
`docs/.locks/context-compaction.lock` before broad rewrites of shared active docs
when multiple tools/tasks could edit them concurrently.

This lock protects documentation compaction only. It does not serialize source
changes, schema migrations, deployment, or production execution. Use a
worktree/branch ownership boundary or the relevant database/deployment
single-flight mechanism for those operations.

A lock owner must identify tool plus task/thread/session. If a lock appears
stale, report it; do not silently replace it. Let the main task or user decide
takeover.

## Cross-Tool Compatibility

All tools share project docs as durable truth:

- Codex reads `AGENTS.md`.
- Claude Code uses a short `CLAUDE.md` that imports `AGENTS.md`.
- Other agents read `AGENTS.md` and relevant project docs before changing
  shared state.

Native task IDs are useful routing handles but may not exist in another tool.
Preserve module ownership and compact handoffs in docs when work must cross tool
boundaries. Enable Return Packets only when native messaging cannot provide a
reliable return path.

## Security And Maintenance

- Never commit secrets, credentials, private customer data, signed URLs, or
  access-granting links.
- Keep logs minimal and redacted; record the signal, not the full output.
- Do not revert unrelated work from another task or agent.
- Use a worktree, branch, or explicit ownership boundary for risky parallel code
  changes.
- Update module status/handoff only when state changed.
- Add or update an ADR when architecture, shared contracts, deployment,
  security, cost, or product scope changes.
- Archive or replace stale visible task mappings when module tasks are replaced.

## Main Task Review Loop

1. Read the minimum active context.
2. Inspect registered long-lived module tasks and current work.
3. Decompose actionable work and route it to the owning visible module task.
4. Use temporary subagents only for bounded side work.
5. Review native results and promote durable truth to the correct doc.
6. Resolve or escalate cross-module decisions.
7. Compact project docs only when a real trigger exists.

Keep the main task focused on planning quality, routing, integration, and
durable project truth rather than duplicating module implementation or task
telemetry.

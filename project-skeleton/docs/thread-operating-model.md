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
3. **Every-task routing:** treat every registered task as an intake surface.
   Check actual ownership before nontrivial execution and route misdirected work
   to its registered owner.
4. **Docs for durable truth:** keep product behavior, architecture, ownership,
   accepted decisions, risks, and current outcomes in project docs.
5. **Native state for transient work:** keep prompts, progress events, temporary
   plans, and ordinary task results in native task history.
6. **Conditional controls:** add thread-runs, Return Packets, locks, and archives
   only when risk, recovery, audit, or cross-tool operation requires them.
7. **One primary home:** link to facts instead of copying them across docs.

## Roles And Ownership

### Main Task

The main task owns:

- product direction and priority
- module boundaries and ownership
- task decomposition and routing
- cross-module decisions and ADR review
- result review and integration
- project-state hygiene

The main task should not become the implementation task for every module, but
it is also not the only routing entrypoint. It resolves boundaries and
project-level decisions that module tasks cannot safely settle themselves.

### Module Tasks

Each stable module may have one long-lived visible task. That task owns:

- implementation and local debugging inside the module
- module-local verification
- ownership checks for every incoming request
- direct routing of work that belongs to another registered module
- decomposition and delegation when this module is the selected lead
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
If a temporary subagent discovers that its bounded slice belongs to another
module, it reports that finding to its parent/lead. It does not become another
cross-task coordinator.

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

### Every-Task Intake And Routing

The main task and every registered module task run the same lightweight gate
before nontrivial analysis or changes. The task where the user asked is an
intake surface; it does not automatically own the problem.

1. Classify the request: answer-only, clearly local, owned by another module,
   cross-module, or ownership-unclear.
2. Inspect the registry and only the project context needed to identify likely
   owners. If ownership is unclear, perform a minimal read-only impact scan; do
   not begin implementation.
3. If the current task owns the work with high confidence, execute it within
   that boundary.
4. If another module owns it, send a compact native request directly to that
   registered task. Do not relay through the main task unless a project-level
   decision is needed.
5. If multiple modules are required, select exactly one lead. The lead owns
   decomposition, shared-contract stabilization, integration, and result
   return. Other modules receive explicit non-overlapping slices and may start
   only work that does not invent an unresolved contract.
6. Classify every delegated slice and choose supported `model` and `thinking`
   parameters using Dispatch-Time Model Routing below.
7. Keep progress and a lightweight routing trace in native task state unless
   Portable Controls are needed.
8. The intake task remains responsible for returning a coherent result to its
   user unless another return owner is explicitly named.
9. Update durable docs only when project truth changed.

Answer-only or clearly local work may stay in the current task only when it has
no plausible module ownership conflict, persistent change, or cross-module
effect. The fact that the current model can solve a problem is not evidence
that the current task should own it.

### Routing Trace And Loop Prevention

Include this compact routing envelope in each native cross-task request:

- request key
- intake/source task and module
- one lead task/module
- assigned non-overlapping slice
- visited tasks/modules
- return owner
- selected model/Thinking profile and one-line reason

Use the same request key across re-routing. A receiving task may transfer work
that it does not own, but it must extend the visited list and preserve one lead
and one return owner.

- Never send the same or a broader slice back to a visited task.
- Never broadcast an unresolved request to every module. Perform a read-only
  impact scan and contact only likely owners.
- Inspect target native state before dispatch when duplicate work is plausible.
- Do not let multiple tasks independently coordinate the same request.
- If routing would loop, duplicate active work, or require a missing visible
  task, stop and escalate. Create a missing task only with the authorization
  required by the current product/runtime.
- If native cross-task tools are unavailable, send the compact request to the
  main task or use the project-approved Portable Controls fallback. State the
  visibility limitation.

Use this minimum task payload:

- desired outcome
- why the target module owns it
- acceptance criteria
- constraints and dependencies
- relevant files/docs
- expected verification
- when to escalate to the main task
- routing trace and named return owner
- selected model/Thinking profile and one-line reason

Do not dispatch vague ideas, duplicate active work, or answer-only questions
with no ownership ambiguity. Do not retain module-owned work merely because the
current task could resolve it immediately.

### Return Priority

Use return channels in this order:

1. System/Codex Desktop native result delivery to the named return owner:
   native delegation return, `send_message_to_thread`, or active inspection
   with `read_thread`. Do not declare the intake request complete before the
   delegated result is reviewed unless the runtime requires asynchronous
   return and that limitation is stated. If automatic return fails before
   output, prefer native read plus one compatibility-safe native send before a
   file-based fallback.
2. Compact module `handoff.md` update when the result must survive native task
   history, tool, or account boundaries.
3. Return Packet only when cross-tool/asynchronous work, high-risk audit,
   unreliable native delivery, or explicit project policy requires it.

Do not require both native delivery and a Return Packet for routine work.

The return owner should promote only durable outcomes:

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

## Receiver-Aware Model Routing

Every call to an existing visible task, module-to-module re-route, automatic
owner return, or authorized new visible task must classify the work the target
will perform after receiving the message. Do not classify by payload length or
transport simplicity alone.

### Classification Signals

Assess the concrete task before invocation:

- **Type:** lookup/docs, verification, implementation, review, debugging,
  architecture/decision, migration/operations, security/payment
- **Complexity:** deterministic, normal, ambiguous, or highly coupled
- **Risk:** low, moderate, high, or critical failure cost
- **Context:** short/local, multi-file/module, or long-history synthesis
- **Reversibility:** easy rollback, costly rollback, or irreversible step
- **Parallelism:** one owner, independent module slices, or tightly coupled work
- **Receiver duty:** acknowledge, review, integrate, decide, update a gate, or
  execute an action

### Routing Matrix

| Profile | Typical Work | Model Capability | Thinking |
|---|---|---|---|
| `fast` | receipt-only acknowledgement or mechanical low-risk work with no review/merge/decision duty | efficient general model | `low`; use `medium` when context is not trivial |
| `balanced` | normal implementation, clear bug fix, routine review, single-module work | balanced general | `medium`; use `high` for uncertainty or broader verification |
| `deep` | ambiguous bug, repeated failure, long context, cross-module contract, architecture, read-only auth/security/payment investigation | strongest available | `high` or `xhigh` |
| `critical` | executing/authorizing irreversible migration or production action, active financial/data/security loss, highest failure cost | strongest available | `xhigh` by default; `max` only with exact model/path support |

Current GPT-5.6 mappings are typically Luna -> `fast`, Terra -> `balanced`, and
Sol -> `deep`/`critical`. Discover actual current model IDs from the active tool
schema. These names are examples, not durable project configuration.

Autonomous routing may select only GPT-5.6 or GPT-5.5 families. Prefer GPT-5.6;
use GPT-5.5 only as a supported compatibility fallback. Do not autonomously
select GPT-5.4, mini/nano, Codex-Spark, or older families. A user's explicit
model request may override this pool only when supported and compatible.

Apply these receiver floors:

- `fast`: pure acknowledgement with no review, merge, decision, or state change
- `balanced`: ordinary owner-result review or routine state integration
- `deep`: production evidence, acceptance/gate review, cross-module integration,
  or long/risky context
- `critical`: the high-consequence action or active severe incident itself, not
  merely the review of production evidence

Do not route from keywords alone. Reversible read-only work in a sensitive
domain is normally `deep`; reserve `critical` for the action/exposure itself.

### Invocation Rules

- Existing visible task: inspect the active schema and normally call
  `send_message_to_thread` with explicit supported `model` and `thinking` that
  pass the Desktop compatibility gate below.
- New visible task: after required user authorization, call `create_thread`
  with both parameters selected for its first concrete task.
- New role-only task with no concrete work: use the current `balanced` mapping
  with `medium`; classify again on every later dispatch.
- Temporary subagent, when permitted: apply the same classification and pass
  explicit model/reasoning parameters supported by that tool.
- Include `Routing: <profile>; model=<id>; thinking=<effort>; reason=<short>` in
  the native prompt for observability. Actual tool arguments and product
  compatibility are authoritative; this text cannot force unsupported params.
- Explicit user model/Thinking instructions take precedence.
- Use `max`/`ultra` only when the exact model/path accepts it and the work needs it; a generic tool enum is insufficient.

### Desktop Compatibility Gate
- Refresh model examples from the official guide during audit/upgrade; during routine work use the active schema and project mapping.
- Intersect tool values with model/path capability. A tool enum may span models;
  GPT-5.5 accepts up to `xhigh` on the observed Desktop path, never `max`.
- Do not use GPT-5.3-Codex-Spark or another preview/specialized model for visible
  cross-task work unless the product confirms all Desktop-managed turn options.
  Spark is not a compatibility fallback.
- If a visible tool lacks `reasoning.summary`, the source cannot set/remove it.
  Attribute incompatibility to the Desktop turn-start/adapter layer, not source.
- Product-managed automatic returns must use the same receiver-aware profile and
  compatibility gate. A completed task is not automatically a `fast` return.
- Explicit user model/Thinking choices take precedence only when the selected
  pair is supported and compatible with the active Desktop path.

### Fallback Safety
If a preferred model or effort is unavailable:

1. Re-read the active tool's supported model/Thinking values.
2. Choose the closest supported option that still satisfies the risk profile.
3. State the fallback in the native dispatch prompt.
4. Never silently downgrade `deep` or `critical` work below a safe level. Stop
   and ask the user if no supported option is adequate.

If an invocation fails before the target produces output because a
Desktop-managed optional reasoning parameter is unsupported:

1. Confirm that the target produced no response and that retry cannot duplicate
   work.
2. Reuse the same request key and prompt.
3. Retry without overrides only when the target's current GPT-5.5/5.6
   model/Thinking pair is confirmed compatible. Otherwise retry once with a
   compatible pair that satisfies the receiver floor. State the fallback.
4. If product-managed automatic return cannot retry, recover the completed
   source result with native task read and send one explicit compatibility-safe
   message, or use the approved Return Packet fallback.
5. Stop after a second failure and report the product-layer limitation.

If a pre-output error lists supported Thinking values, preserve key/prompt/model
and retry once at the highest safe listed value (GPT-5.5 `max` -> `xhigh`). Do
not retry after output or lower a profile below its safe floor.

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
- Use a worktree, branch, or explicit ownership boundary for risky parallel code changes.
- Update module status/handoff only when state changed.
- Add/update an ADR for architecture, shared contracts, deployment, security, cost, or product scope changes.
- Archive or replace stale visible task mappings when module tasks are replaced.

## Runtime Loops

### Any Registered Task

1. Read the minimum active context and its registry boundary.
2. Classify ownership before nontrivial execution.
3. Execute owned work, directly route misowned work, or perform a minimal read-only impact scan when ownership is unclear.
4. For cross-module work, keep one lead, non-overlapping slices, and a loop-safe routing trace.
5. Reclassify model/Thinking for every outward dispatch.
6. Return a coherent result to the intake user or named return owner.

### Main Task Review Loop

1. Read the minimum active context.
2. Inspect registered long-lived module tasks and current work.
3. Route actionable work to its owning visible module task; accept escalations only for unresolved ownership or project-level decisions.
4. Use temporary subagents only for bounded side work.
5. Review native results and promote durable truth to the correct doc.
6. Resolve or escalate cross-module decisions.
7. Compact project docs only when a real trigger exists.

Keep the main task focused on planning, routing, integration, and durable truth rather than duplicating module implementation or task telemetry.

---
name: multi-agent-model
description: >
  Bootstrap, audit, slim, repair, or upgrade a native-first operating model for
  long-running agent-assisted projects. Use when a project needs a main planning
  task, durable visible module tasks, automatic intake and cross-task module
  routing, project-local
  AGENTS.md rules, dispatch-time model/Thinking selection, compact current-state
  docs, non-preemptive verification, Focus Leases, pull-based result harvesting,
  cross-tool compatibility, or lock-safe docs compaction. Prefer ChatGPT
  Desktop/Codex native task tools for visible long-lived work and temporary
  subagents only for bounded disposable work. Do not use for routine
  implementation after the project contract is
  installed. Trigger terms include agent operating model, long-lived module
  threads, visible module tasks, main thread dispatch, thread routing, project
  agent OS, model routing, thinking routing, context governance, 项目智能体协作,
  长期模块线程, 主线程派单, 模型路由, 推理强度, 文档压缩.
---

# Multi-Agent Model

## Purpose

Install a small project-local contract that lets every registered task detect
ownership and route work to long-lived visible module tasks without turning
chat history or task telemetry into a second project database.

Use this skill for initialization, migration, audit, repair, or docs
compaction. After installation, `AGENTS.md` and project docs govern routine
work; this skill is not the runtime.

Core rule:

> Keep durable project truth in project docs. Keep transient execution state in
> native tasks. Add file-based task records only when native state is not durable
> enough for the risk or collaboration boundary.

## Fit Check

Choose the smallest mode that solves the real coordination problem.

- Use **Minimal Mode** for one active task or an early project with unclear
  module boundaries.
- Use **Native Mode** by default when Codex/ChatGPT Desktop can create, list,
  read, continue, fork, or hand off visible tasks.
- Add **Portable Controls** only for cross-tool, compliance, high-risk,
  asynchronous, or unreliable-runtime work.
- Activate the **Verification Side Lane** only when an unrelated cross-task
  check could interrupt a long-lived owner or when a fixed-target independent
  review is useful. Task-local self-verification stays with the owner.
- Reuse existing PRDs, architecture docs, issue trackers, and status docs.
  Map responsibilities instead of duplicating them.
- If project docs are already bloated, compact or consolidate them before
  installing more files.

## Operating Modes

### Minimal Mode

Install only:

- `AGENTS.md`
- one current work surface, normally `docs/current-work.md` or the existing
  issue tracker

### Native Mode (Default)

Install or map:

- `AGENTS.md`
- `docs/thread-operating-model.md`
- `docs/current-work.md`
- `docs/thread-registry.md` for durable visible task identities and module
  ownership only
- existing PRD and technical-design docs, or the included current snapshot
  templates when the project has no equivalent
- module `status.md` and `handoff.md`; add `runbook.md` only when a module task
  needs recovery across long histories
- ADRs only for durable decisions

### Portable Controls (Opt-In)

Add only when native task state is insufficient:

- `docs/thread-runs/<task-id>.md` for long, risky, resumable, or audited work
- Return Packets for cross-tool/asynchronous return delivery
- `docs/.locks/context-compaction.lock` for broad shared-doc compaction
- archives for useful history removed from active context
- Focus Leases and file-based verification records when native state cannot
  coordinate interruption or evidence across tools
- `CLAUDE.md` or another tool-specific entrypoint that imports `AGENTS.md`

## Installation Workflow

1. Inventory existing instructions, docs, issue trackers, modules, tests, and
   visible native tasks.
2. Clarify main-task authority, stable module ownership, and the every-task
   intake/routing rule.
3. Choose Minimal, Native, or Native plus Portable Controls.
4. Install `AGENTS.md` from `references/agents.template.md` and keep it concise.
5. Install `docs/thread-operating-model.md` from
   `references/thread-operating-model.template.md` only when more than Minimal
   Mode is needed.
6. Reuse existing project docs. Add current PRD, technical design, or workboard
   templates only when the responsibility has no current home.
7. Discover existing visible module tasks with native task tools. Reuse them
   and record their durable IDs/links in `docs/thread-registry.md`.
8. If a required visible module task does not exist, ask for or rely on explicit
   user authorization before creating it. Generate its startup prompt from
   `references/module-startup-prompt.template.md`.
9. Install receiver-aware model routing so every existing-task message,
   automatic return, or authorized new-task creation selects a supported,
   Desktop-compatible model/Thinking pair for the receiver's next work.
10. Install loop-safe direct routing so any registered module task can transfer
    or split misrouted work without routing every request through the main task.
11. Install the non-preemptive verification summary. Add Focus Leases or
    file-based `VAL-*` records only for concrete concurrent, cross-tool, audit,
    or unreliable-runtime needs.
12. Add other Portable Controls only for a concrete risk or interoperability
    need.
13. Report the installed mode, mapped docs, visible task map, assumptions, and
    omitted optional controls.

## Native-First Runtime Contract

### Long-Lived Visible Module Tasks

- Treat the main task as planner, dispatcher, reviewer, and cross-module
  decision authority, not the only routing entrypoint.
- Treat each registered module task as a durable visible work surface with a
  stable ownership boundary, recovery context, and routing responsibility.
- Require the main task and every registered module task to check ownership
  before nontrivial execution. The task where the user asked is an intake
  surface, not proof that the task owns the work.
- Route work directly to the registered owner when it clearly belongs to
  another module. Do not execute it locally merely because the current model
  can complete it.
- For cross-module work, name a lead module and stabilize shared contracts
  before fully parallel execution. Other modules may proceed only on slices
  that do not require inventing an unresolved contract.
- Do not replace a registered long-lived module task with a temporary subagent
  merely because subagents are available.
- Use temporary subagents for bounded research, review, test, search, or other
  disposable work whose result can be consumed by the current task.
- If a temporary subagent discovers that its slice belongs elsewhere, it must
  report that to its parent/lead instead of becoming a second routing
  coordinator.
- Use native task reads/messages for progress and result review. Write a compact
  module handoff when the result changes durable project truth.
- If native routing is unavailable, use the registry plus a compact task payload
  as the fallback. Add a thread-run or Return Packet only when needed.

### Every-Task Routing Gate

Before the main task or any registered module task performs nontrivial analysis
or changes:

1. Classify the request as answer-only, clearly local, owned by another module,
   cross-module, or ownership-unclear.
2. Check the registry and the minimum relevant project context. Do not infer
   ownership from the task in which the user happened to ask.
3. If another module clearly owns the work, send a compact native request to
   that registered task. The intake task remains responsible for returning a
   coherent answer to its user unless the request names a different return
   owner.
4. If several modules are involved, select exactly one lead. The lead owns
   decomposition, shared-contract stabilization, integration, and result
   return; other tasks own only explicit non-overlapping slices.
5. If ownership is unclear, perform only the smallest read-only impact scan
   needed to identify likely owners. Do not begin implementation. Escalate to
   the main task or user only when the boundary or decision still cannot be
   resolved.
6. Allow direct module-to-module routing without mandatory main-task relay.
   Reserve the main task for unresolved boundaries, product/priority choices,
   shared contracts, and other project-level decisions.

Every cross-task request must keep a lightweight routing trace in native task
history: request key, intake/source task, lead, assigned slice, visited tasks,
and return owner. Do not write routine traces to project docs.

- Never send the same or a broader slice back to a visited task.
- Never broadcast an unresolved request to all modules. Use a read-only impact
  scan, then route only to likely owners.
- Check target task state before dispatch when duplicate work is plausible.
- A receiving task may re-route work it does not own, but it must preserve the
  request key, extend the visited list, and keep one lead.
- If routing would loop, duplicate active work, or require a missing visible
  task, stop and escalate. Create a missing task only with the authorization
  required by the current product/runtime.

### Result Return

Use this priority:

1. Codex Desktop or system-native result delivery to the named return owner,
   including native delegation return, `send_message_to_thread`, or active
   inspection with `read_thread`. Do not declare the intake request complete
   until the delegated result has been reviewed, unless the runtime requires an
   asynchronous return and that limitation is stated. If automatic return
   fails before output, prefer native read plus one compatibility-safe native
   send before creating a file-based fallback.
2. Compact update to module `handoff.md` when the result must survive task UI,
   tool, or account boundaries.
3. Return Packet only for cross-tool/asynchronous work, high-risk audit trails,
   unreliable native delivery, or explicit project policy.

Do not require both native return and a Return Packet for ordinary work.

### Non-Preemptive Verification Side Lane

Preserve one visible mainline in every long-lived main or module task. Keep
task-local tests and self-verification with that owner, but route unrelated
cross-task review, testing, or evidence checks to a bounded verifier by default.

- Give independent verification a `VAL-*` request key and one immutable target
  when possible: commit, diff, recorded branch head, artifact, checkpoint, or
  isolated worktree snapshot.
- Verification is read-only by default. A discovered fix becomes a separate
  `TASK-*` owned by the relevant module; a verifier must not silently turn into
  an implementation worker.
- Use four interruption classes:
  - `background`: no push; harvest later
  - `checkpoint`: deliver after the owner's next safe checkpoint
  - `blocking`: prevent dependent acceptance/progress, but notify only at the
    next safe checkpoint
  - `emergency`: immediate preemption, reserved for active severe production,
    data-loss, security, credential, or irreversible-failure risk
- If concurrent tools or tasks could inject work into a focused owner, create a
  cooperative Focus Lease under `docs/.locks/focus/`. It protects attention,
  not files, branches, migrations, deployments, or transactions. Do not create
  one for ordinary single-task work.
- A valid lease records owner identity, active task, focus state, interruption
  policy, safe-delivery event, heartbeat, expiry, and release state. Never
  silently overwrite a stale lease; report it for explicit takeover.
- Pull results at safe harvest points: before a new owner task, after a
  checkpoint or stable commit, when blocked/idle, and before acceptance, merge,
  release, or deployment review. Do not harvest ordinary results during
  unstable edits, migrations, high-risk actions, or unfinished debug/test-fix
  cycles.
- Prefer native `read_thread`, task completion state, and system/Desktop result
  delivery. `pass` and informational results stay pull-only; do not push them
  into the owner task. Route actionable failure, decision, blocker, or emergency
  results through native messaging at the allowed interruption point.
- Add file-based verification requests/results only for Portable Controls:
  cross-tool coordination, audit evidence, asynchronous work, or unreliable
  native state. Do not require `thread-runs`, inboxes, or result packets for
  routine native verification.
- If the target changes before review completes, mark the result `stale` and
  requeue against a new immutable target instead of merging stale evidence.

Read `references/verification-operating-model.template.md` only when activating,
recovering, or auditing this side lane. Use its request, result, startup, and
Focus Lease templates only for the controls the project actually needs.

### Receiver-Aware Model Routing

Before every native call to an existing visible task, including a re-route from
one module task to another, or authorized creation of a new visible task:

1. Classify both the message and the work the receiving task must perform next:
   task type, complexity, risk, context size, reversibility, parallelism,
   review/integration duty, and decision authority. Message length and the
   simplicity of transport never determine the profile by themselves.
2. Inspect both the active tool/client schema and the selected model's accepted
   Thinking values on that invocation path, then use their intersection. A tool
   enum may be broader than one model's actual support. Do not invent a model,
   effort, or hidden request parameter.
3. Select a capability profile:
   - `fast`: deterministic, bounded work whose receiver only acknowledges or
     performs a mechanical low-risk action -> efficient model; `low` or `medium`
   - `balanced`: normal implementation/review with clear scope -> balanced
     model; `medium` or `high`
   - `deep`: ambiguous, long-context, cross-module, architecture, repeated
     failure, or read-only security/payment investigation -> strongest model;
     `high` or `xhigh`
   - `critical`: executing/authorizing an irreversible migration or production
     action, responding to active financial/data/security loss, or other
     highest-failure-cost work -> strongest model; `xhigh` by default, with
     `max` only when the exact model and invocation path explicitly support it
4. Apply receiver floors:
   - pure receipt acknowledgement with no review, merge, decision, or state
     change may use `fast`
   - ordinary owner result review or routine state integration is at least
     `balanced`
   - production evidence review, acceptance/needs-followup verdicts, project
     gate updates, cross-module integration, or long/risky context are normally
     `deep`
   - use `critical` only when the receiver will execute/authorize an
     irreversible high-consequence action or handle an active severe incident
5. Pass explicit supported `model` and `thinking` when the invocation exposes
   those controls and the selected pair passes the compatibility gate. Include
   a one-line routing reason in the native prompt. Do not create routine
   model/version/quota telemetry in project docs.

Current GPT-5.6 examples are Luna for `fast`, Terra for `balanced`, and Sol for
`deep`/`critical`. Treat these as discoverable current mappings, not durable
project contracts. Use `ultra` only when the exact model/invocation path supports
it and the task genuinely benefits from that execution mode; otherwise use the
highest supported effort or route independent work to registered module tasks.
For GPT-5.5 cross-task calls, use `xhigh` as the ceiling and never send `max`.

For autonomous routing, limit the candidate pool to GPT-5.6 and GPT-5.5
families. Prefer GPT-5.6; use GPT-5.5 only as a supported compatibility fallback.
Do not autonomously select GPT-5.4, mini/nano, Codex-Spark, or older families.
An explicit user model request may override this pool only when the active path
supports it and the compatibility/risk checks pass.

Do not classify by sensitive keywords alone. A reversible read-only
investigation in a high-risk domain is normally `deep`; use `critical` when the
task itself performs/authorizes a high-consequence action or an active incident
creates immediate severe exposure.

### Desktop Compatibility Gate

- Treat exact model IDs as runtime-discovered values. During skill audit or
  upgrade, refresh examples from the current official model guide; during
  routine dispatch, use the active tool schema and current project mapping.
- Treat a generic tool enum as an outer bound, not proof that every listed
  effort works with every model. Confirm the selected model/path combination.
  GPT-5.5 accepts at most `xhigh` on the observed Desktop cross-task path.
- For visible cross-task delivery or continuation in Codex Desktop, do not use
  GPT-5.3-Codex-Spark or another preview/specialized model unless the current
  product explicitly confirms compatibility with all Desktop-managed turn
  options. Spark is not a cross-task fallback.
- The visible `send_message_to_thread` contract may expose only `model`,
  `thinking`, and `prompt`. If it does not expose `reasoning.summary`, the skill
  cannot add, remove, or retry that hidden field directly. Attribute such a
  failure to the Desktop turn-start/adapter layer, not to the source task.
- Treat the `Routing:` line as an audit statement. Actual tool arguments and
  product compatibility are authoritative; text must never force an
  unsupported parameter combination.
- If a pre-output error lists supported Thinking values, retry at most once with
  the same request key, prompt, and model, selecting the highest listed effort
  that still satisfies the profile. For GPT-5.5, `max` falls back to `xhigh`.
  Never retry after any target output.
- If a cross-task invocation fails before the target produces output because a
  Desktop-managed optional reasoning parameter is unsupported, retry exactly
  once with the same request key and prompt. Omit `model` and `thinking` only
  when the target's current model/Thinking pair is confirmed compatible and
  uses GPT-5.5/5.6; otherwise use a compatible GPT-5.6 or GPT-5.5 pair. Record the
  fallback and do not retry after any target output exists.
- If a product-managed automatic return cannot perform that retry, recover the
  result with native task read plus an explicit compatibility-safe message, or
  use the approved Return Packet fallback. State the product-layer limitation.

Explicit user model/Thinking instructions win only when the pair is supported
and Desktop-compatible. If a preferred option is unavailable, choose the
closest supported option that still meets the receiver's risk requirement and
state the fallback. Never silently lower `deep` or `critical`; ask or stop when
no safe supported option exists.

For a new role-only module task with no concrete work yet, use the current
`balanced` model mapping with `medium`; classify and override again on every
future dispatch.

## Durable State Rules

- Chat/task history and memory are useful work surfaces, not the sole source of
  truth for product behavior, architecture, ownership, or accepted decisions.
- Keep `current-work.md` solution-neutral: record what outcome is needed, not
  how to implement it.
- Keep each fact in one primary home and link instead of copying.
- Update docs only for substantive state changes.
- Keep active docs as current snapshots, not append-only logs.
- Do not create `roadmap.md`, `status.md`, module PRD/design docs, runbooks,
  thread-runs, Return Inbox, locks, or archives unless the project needs them.
- Never commit secrets, credentials, private customer data, signed URLs, or
  access-granting links.

## Docs Compaction

Native conversation compaction and product memory do not compact project docs.
Use LV2 only for docs-only cleanup when active docs are stale, contradictory,
duplicated, or materially oversized.

- Ordinary targeted doc updates do not need a compaction lock.
- Acquire `docs/.locks/context-compaction.lock` before broad shared active-doc
  rewrites across multiple tools or tasks.
- A compaction lock is not a source-code, migration, deployment, or production
  execution lock. Use a worktree/branch ownership boundary or the relevant
  database/deployment single-flight mechanism for those operations.
- LV2 may rewrite current snapshots and archive stale history.
- LV2 must not change source, tests, production config, schemas, migrations,
  ADR decisions, product direction, module ownership, roadmap priority, or
  public contracts.
- Do not silently replace a stale lock. Report it and let the main task or user
  decide takeover.
- If ownership, scope, or semantics are unclear, create a compaction request
  instead of guessing.

## Resource Routing

Read only the resources needed for the selected mode:

- Core project contract: `references/agents.template.md` and
  `references/thread-operating-model.template.md`
- Visible module task map: `references/thread-registry.template.md`
- Module startup: `references/module-startup-prompt.template.md`
- Main-task and module-to-module payloads:
  `references/main-thread-dispatch-task.template.md` and
  `references/cross-thread-task.template.md`
- Current snapshots: `references/current-prd.template.md`,
  `references/current-technical-design.template.md`, and
  `references/current-work.template.md`
- Module recovery: `references/module-status.template.md`,
  `references/handoff.template.md`, and `references/runbook.template.md`
- Durable decisions: `references/adr.template.md`
- Portable Controls only: `references/thread-run.template.md`,
  `references/return-packet.template.md`,
  `references/compaction-lock.template.md`, and
  `references/context-compaction-note.template.md`
- Non-preemptive verification when activated:
  `references/verification-operating-model.template.md`,
  `references/verification-request.template.md`,
  `references/verification-result-packet.template.md`,
  `references/verification-thread-startup-prompt.template.md`, and
  `references/focus-lease.template.md`
- Cross-tool entrypoint: `references/claude.template.md`

## Audit Checklist

- Is Native Mode used unless there is a concrete need for Portable Controls?
- Does each stable module map to one long-lived visible task?
- Does every registered task check ownership before nontrivial execution?
- Can a misrouted request move directly to its owning module while retaining
  one lead, one return owner, and a loop-safe native routing trace?
- Does dispatch reuse that task instead of spawning disposable module workers?
- Are temporary subagents limited to bounded work?
- Is the registry a small identity/ownership map rather than a duplicate queue?
- Are native task state and `current-work.md` the default active work surfaces?
- Are thread-runs and Return Packets conditional instead of mandatory?
- Does unrelated verification preserve the owner's visible mainline, use a
  fixed target, remain read-only, and deliver according to one of four explicit
  interruption classes?
- Are pass/informational results pulled at safe checkpoints instead of pushed,
  with Focus Leases used only when concurrent interruption is a real risk?
- Does every native existing/new task invocation classify the concrete task and
  the receiver's follow-up duty before selecting compatible model/Thinking
  values?
- Are production evidence, acceptance review, gate updates, and cross-module
  integration protected from transport-only `fast` classification?
- Are preview/specialized models excluded from cross-task delivery unless their
  Desktop-managed parameter compatibility is confirmed?
- Is autonomous model selection limited to GPT-5.5/5.6 unless the user
  explicitly requests another supported compatible model?
- Do high-risk routing fallbacks avoid silent capability downgrades and stale
  hard-coded quota rules?
- Are active docs current, compact, non-duplicative, and read selectively?
- Are compaction locks used only for broad shared-doc rewrites?
- Can another tool recover durable project truth without reading chat history?

## Fallback

If project-local instructions cannot be written, tell the user to invoke this
skill in new tasks and point those tasks to the existing project docs. Do not
pretend model memory alone provides a durable project operating contract.

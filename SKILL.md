---
name: project-agent-operating-model
description: >
  Bootstrap, audit, slim, repair, or upgrade a native-first operating model for
  long-running agent-assisted projects. Use when a project needs a main planning
  task, durable visible module tasks, automatic intake and cross-task module
  routing, project-local
  AGENTS.md rules, dispatch-time model/Thinking selection, compact current-state
  docs, cross-tool compatibility, or lock-safe docs compaction. Prefer ChatGPT
  Desktop/Codex native task tools for visible long-lived work and temporary
  subagents only for bounded disposable work. Do not use for routine
  implementation after the project contract is
  installed. Trigger terms include agent operating model, long-lived module
  threads, visible module tasks, main thread dispatch, thread routing, project
  agent OS, model routing, thinking routing, context governance, 项目智能体协作,
  长期模块线程, 主线程派单, 模型路由, 推理强度, 文档压缩.
---

# Project Agent Operating Model

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
9. Install dispatch-time model routing so every existing-task message or
   authorized new-task creation passes an explicit supported `model` and
   `thinking` selected for the concrete task.
10. Install loop-safe direct routing so any registered module task can transfer
    or split misrouted work without routing every request through the main task.
11. Add Portable Controls only for a concrete risk or interoperability need.
12. Report the installed mode, mapped docs, visible task map, assumptions, and
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

1. Native result delivery to the named return owner, or active inspection by
   that intake/lead task. Do not declare the intake request complete until the
   delegated result has been reviewed, unless the runtime requires an
   asynchronous return and that limitation is stated.
2. Compact update to module `handoff.md` when the result must survive task UI,
   tool, or account boundaries.
3. Return Packet only for cross-tool/asynchronous work, high-risk audit trails,
   unreliable native delivery, or explicit project policy.

Do not require both native return and a Return Packet for ordinary work.

### Mandatory Dispatch-Time Model Routing

Before every native call to an existing visible task, including a re-route from
one module task to another, or authorized creation of a new visible task:

1. Classify task type, complexity, risk, context size, reversibility, and
   parallelism.
2. Inspect the active tool/client schema for supported model IDs and Thinking
   values. Do not invent a model or send an unsupported effort.
3. Select a capability profile:
   - `fast`: deterministic, bounded, low-risk work -> fastest capable model;
     `low` or `medium`
   - `balanced`: normal implementation/review with clear scope -> balanced
     model; `medium` or `high`
   - `deep`: ambiguous, long-context, cross-module, architecture, repeated
     failure, or read-only security/payment investigation -> strongest model;
     `high` or `xhigh`
   - `critical`: executing/authorizing an irreversible migration or production
     action, responding to active financial/data/security loss, or other
     highest-failure-cost work -> strongest model; `max`
4. Pass both `model` and `thinking` explicitly to `send_message_to_thread` or,
   after required user authorization, `create_thread`. Do not rely on the
   target task's previous settings or the user's default model.
5. Include a one-line routing reason in the native dispatch prompt. Do not
   create routine model/version/quota telemetry in project docs.

Current GPT-5.6 examples are Luna for `fast`, Terra for `balanced`, and Sol for
`deep`/`critical`. Treat these as discoverable current mappings, not durable
project contracts. Use `ultra` only when the active invocation schema supports
it and the task genuinely benefits from that execution mode; otherwise use the
highest supported effort or route independent work to registered module tasks.

Do not classify by sensitive keywords alone. A reversible read-only
investigation in a high-risk domain is normally `deep`; use `critical` when the
task itself performs/authorizes a high-consequence action or an active incident
creates immediate severe exposure.

Explicit user model/Thinking instructions win. If a preferred option is
unavailable, choose the closest supported option that still meets the risk
requirement and state the fallback in the native prompt. Never silently lower a
`deep` or `critical` task below a safe capability level; ask the user or stop if
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
- Does every native existing/new task invocation classify the concrete task and
  pass explicit supported `model` and `thinking` values?
- Do high-risk routing fallbacks avoid silent capability downgrades and stale
  hard-coded quota rules?
- Are active docs current, compact, non-duplicative, and read selectively?
- Are compaction locks used only for broad shared-doc rewrites?
- Can another tool recover durable project truth without reading chat history?

## Fallback

If project-local instructions cannot be written, tell the user to invoke this
skill in new tasks and point those tasks to the existing project docs. Do not
pretend model memory alone provides a durable project operating contract.

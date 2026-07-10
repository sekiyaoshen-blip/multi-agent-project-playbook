---
name: project-agent-operating-model
description: >
  Bootstrap, audit, slim, repair, or upgrade a native-first operating model for
  long-running agent-assisted projects. Use when a project needs a main planning
  task, durable visible module tasks, automatic module routing, project-local
  AGENTS.md rules, compact current-state docs, cross-tool compatibility, or
  lock-safe docs compaction. Prefer ChatGPT Desktop/Codex native task tools for
  visible long-lived work and temporary subagents only for bounded disposable
  work. Do not use for routine implementation after the project contract is
  installed. Trigger terms include agent operating model, long-lived module
  threads, visible module tasks, main thread dispatch, thread routing, project
  agent OS, context governance, 项目智能体协作, 长期模块线程, 主线程派单, 文档压缩.
---

# Project Agent Operating Model

## Purpose

Install a small project-local contract that lets a main task route work to
long-lived visible module tasks without turning chat history or task telemetry
into a second project database.

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
2. Clarify main-task responsibility and stable module ownership.
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
9. Add Portable Controls only for a concrete risk or interoperability need.
10. Report the installed mode, mapped docs, visible task map, assumptions, and
    omitted optional controls.

## Native-First Runtime Contract

### Long-Lived Visible Module Tasks

- Treat the main task as planner, dispatcher, reviewer, and cross-module
  decision owner.
- Treat each registered module task as a durable visible work surface with a
  stable ownership boundary and recovery context.
- When the main task decomposes work, route module-owned work to the existing
  registered module task with native task messaging.
- For cross-module work, name a lead module and stabilize shared contracts
  before fully parallel execution. Other modules may proceed only on slices
  that do not require inventing an unresolved contract.
- Do not replace a registered long-lived module task with a temporary subagent
  merely because subagents are available.
- Use temporary subagents for bounded research, review, test, search, or other
  disposable work whose result can be consumed by the current task.
- Use native task reads/messages for progress and result review. Write a compact
  module handoff when the result changes durable project truth.
- If native routing is unavailable, use the registry plus a compact task payload
  as the fallback. Add a thread-run or Return Packet only when needed.

### Result Return

Use this priority:

1. Native result delivery or main-task inspection of the module task.
2. Compact update to module `handoff.md` when the result must survive task UI,
   tool, or account boundaries.
3. Return Packet only for cross-tool/asynchronous work, high-risk audit trails,
   unreliable native delivery, or explicit project policy.

Do not require both native return and a Return Packet for ordinary work.

### Model Selection

- Inherit the current task/client model by default.
- Do not write model/version/quota telemetry for routine dispatch.
- Override or pin a model only for explicit user choice, reproducibility,
  compatibility, cost/latency constraints, or a clear capability need.
- When the GPT-5.6 family is available, use Sol for difficult/high-risk work,
  Terra for balanced everyday work, Luna for fast bounded work, and parallel or
  Ultra-style execution for genuinely independent complex work.
- Treat model names as current examples, not durable project contracts.
- Record the requested/actual model only when an override matters to recovery,
  audit, or result interpretation.

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
- Does dispatch reuse that task instead of spawning disposable module workers?
- Are temporary subagents limited to bounded work?
- Is the registry a small identity/ownership map rather than a duplicate queue?
- Are native task state and `current-work.md` the default active work surfaces?
- Are thread-runs and Return Packets conditional instead of mandatory?
- Are model overrides exceptional and free of stale hard-coded quota rules?
- Are active docs current, compact, non-duplicative, and read selectively?
- Are compaction locks used only for broad shared-doc rewrites?
- Can another tool recover durable project truth without reading chat history?

## Fallback

If project-local instructions cannot be written, tell the user to invoke this
skill in new tasks and point those tasks to the existing project docs. Do not
pretend model memory alone provides a durable project operating contract.

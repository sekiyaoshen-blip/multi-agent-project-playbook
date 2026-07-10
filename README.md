# Project Agent Operating Model

Chinese documentation: [`README.zh-CN.md`](README.zh-CN.md)

A native-first Codex skill for projects that need one main planning task and
long-lived visible module tasks.

The skill installs a small project-local contract for module ownership,
automatic routing, durable project truth, cross-tool recovery, and safe docs
compaction. It relies on ChatGPT Desktop/Codex native task tools for ordinary
dispatch and progress instead of recreating the product's task system in files.

## Core Model

```text
GPT-5.6 / current model: decompose and reason
ChatGPT Desktop / Codex: operate visible long-lived tasks
Project docs: preserve durable truth and cross-tool state
Optional Portable Controls: cover recovery, audit, and unreliable boundaries
```

Stable facts belong in docs. Transient prompts, progress events, and routine
results stay in native task history.

## Long-Lived Module Routing

- The main task owns planning, decomposition, routing, review, and cross-module
  decisions.
- Each stable module can own one registered long-lived visible task.
- Module work is routed to that existing task through native task messaging.
- Temporary subagents are limited to bounded disposable research, review,
  search, test, or verification work.
- Native delivery is the default result path. Compact handoffs preserve durable
  cross-task or cross-tool context.
- Thread-runs and Return Packets are optional controls, not routine ceremony.

## Operating Modes

- **Minimal:** `AGENTS.md` plus one current work surface.
- **Native (default):** adds the compact operating model, visible task registry,
  module status/handoff, and existing or mapped product/technical docs.
- **Portable Controls (opt-in):** adds thread-runs, Return Packets, compaction
  locks, or archives only for concrete recovery, audit, asynchronous, high-risk,
  or cross-tool needs.

## GPT-5.6-Aware Model Policy

Inherit the current client/task model by default. Do not write routine model,
version, or quota telemetry into project docs.

When the GPT-5.6 family is available, Sol is suited to difficult/high-risk work,
Terra to balanced everyday work, Luna to fast bounded work, and parallel or
Ultra-style execution to genuinely independent complex work. These are current
examples, not hard-coded project contracts.

## Project Skeleton

The default skeleton is intentionally small:

```text
AGENTS.md
CLAUDE.md
docs/
  thread-operating-model.md
  thread-registry.md
  project-brief.md
  current-prd.md
  current-technical-design.md
  current-work.md
  decisions/
  modules/example-module/
    status.md
    handoff.md
```

Add a module runbook from `references/runbook.template.md` only when native task
history cannot reliably preserve required recovery context.

Do not copy every template automatically. Reuse existing PRDs, design docs,
issue trackers, roadmaps, and status surfaces whenever they already own the
same responsibility.

## Context Governance

- Active docs are current snapshots, not task logs.
- Each durable fact has one primary home.
- Native conversation compaction does not compact project docs.
- LV2 docs-only compaction runs only after a real bloat, contradiction, or
  staleness trigger.
- Ordinary targeted doc edits need no lock.
- Broad concurrent shared-doc rewrites use
  `docs/.locks/context-compaction.lock` when Portable Controls are enabled.

## Installation

See [`INSTALL.md`](INSTALL.md) or [`INSTALL.zh-CN.md`](INSTALL.zh-CN.md).

After initialization, routine work follows project `AGENTS.md` and current docs.
Do not invoke this skill for every implementation or dispatch.

## License

MIT License. See [`LICENSE`](LICENSE).

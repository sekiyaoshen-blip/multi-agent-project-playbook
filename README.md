# Multi-Agent Model

Chinese documentation: [`README.zh-CN.md`](README.zh-CN.md)

A native-first Codex skill for projects that need one main planning task,
long-lived visible module tasks, and ownership-aware routing from every task.

The skill installs a small project-local contract for module ownership,
automatic routing, durable project truth, cross-tool recovery, and safe docs
compaction. It also provides an optional non-preemptive verification lane so
independent checks do not derail a long-lived owner's current work. It relies
on ChatGPT Desktop/Codex native task tools for ordinary dispatch and progress
instead of recreating the product's task system in files.

## Core Model

```text
GPT-5.6 / current model: detect ownership, decompose, and reason
ChatGPT Desktop / Codex: operate visible long-lived tasks
Project docs: preserve durable truth and cross-tool state
Optional Portable Controls: cover recovery, audit, and unreliable boundaries
```

Stable facts belong in docs. Transient prompts, progress events, and routine
results stay in native task history.

## Long-Lived Module Routing

- The main task owns project-level planning, unresolved boundaries, review, and
  cross-module decisions; it is not the only routing entrypoint.
- Each stable module can own one registered long-lived visible task.
- Every registered task checks ownership before nontrivial execution. Where the
  user asked is not proof of which module owns the work.
- A misrouted request moves directly to the registered owner. Ownership-unclear
  requests get a minimal read-only impact scan before implementation.
- Cross-module work has exactly one lead and non-overlapping delegated slices.
- Native routing traces prevent loops, blind broadcasts, duplicate work, and
  competing coordinators without creating a file-based task log.
- Every existing/new native task invocation classifies the receiver's actual
  follow-up work and uses a supported, Desktop-compatible model/Thinking pair.
- Temporary subagents are limited to bounded disposable research, review,
  search, test, or verification work.
- System/Codex Desktop native delivery is the default result path. If automatic
  return fails, prefer native read plus one compatibility-safe native send;
  compact handoffs preserve only durable cross-task or cross-tool context.
- Thread-runs and Return Packets are optional controls, not routine ceremony.

## Non-Preemptive Verification

- Task-local tests stay with the owner; unrelated checks use a bounded verifier
  and a fixed commit, diff, checkpoint, artifact, or worktree when possible.
- Verification is read-only by default. A finding that needs a fix becomes a
  separate module-owned task.
- Four interruption classes control delivery: `background`, `checkpoint`,
  `blocking`, and narrowly defined `emergency`.
- Pass and informational results are pulled from native task state at safe
  checkpoints. Only actionable failures, decisions, blockers, or emergencies
  are pushed, and only when their class permits.
- Optional Focus Leases protect an owner's attention across concurrent tools
  and tasks. They are not code, migration, deployment, or transaction locks.
- File-based verification packets are used only for cross-tool, audit,
  asynchronous, or unreliable-native-state needs.

## Operating Modes

- **Minimal:** `AGENTS.md` plus one current work surface.
- **Native (default):** adds the compact operating model, visible task registry,
  module status/handoff, and existing or mapped product/technical docs.
- **Portable Controls (opt-in):** adds thread-runs, Return Packets, compaction
  locks, Focus Leases, verification records, or archives only for concrete
  recovery, audit, asynchronous, high-risk, or cross-tool needs.

## Dispatch-Time Model Routing

Before every call to an existing visible task, module-to-module re-route,
automatic owner return, or authorized creation of a new task, classify what the
receiver must do next. A short return that requires evidence review, state
integration, or a gate decision is not a `fast` transport message.

- `fast`: fastest capable model, `low`/`medium`
- `balanced`: balanced model, `medium`/`high`
- `deep`: strongest model, `high`/`xhigh`
- `critical`: strongest model, `xhigh` by default; `max` only with exact
  model/path support

Current GPT-5.6 examples are Luna, Terra, and Sol. They are discoverable current
mappings, not durable contracts. User choices win, unsupported values are never
invented, and deep/critical work is not silently downgraded. Routine routing
reasons stay in native task history rather than project docs. Classification is
action-based, not keyword-based: read-only sensitive-domain investigation is
normally `deep`; irreversible action or active severe exposure is `critical`.

Autonomous routing is limited to GPT-5.6 and GPT-5.5 families. GPT-5.6 is the
default; GPT-5.5 is a compatibility fallback. Older, mini/nano, and preview
models are not autonomous choices.

Tool schemas may expose a union of values across models. Routing therefore uses
the intersection of tool, selected model, and invocation-path support. GPT-5.5
cross-task calls are capped at `xhigh`; never send GPT-5.5 with `thinking=max`.

GPT-5.3-Codex-Spark is excluded from visible cross-task delivery unless the
current Desktop path explicitly confirms compatibility with its managed turn
parameters. If a hidden optional reasoning parameter causes a pre-output
failure, retry once using target settings only when that GPT-5.5/5.6
model/Thinking pair is confirmed compatible; otherwise use a compatible pair. The visible task tool does not
expose `reasoning.summary`, so the skill does not pretend it can directly remove
that product-managed field.

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

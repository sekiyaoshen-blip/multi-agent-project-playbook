# Project Agent Instructions

This project uses a native-first project agent operating model.

## Language

- Project language: auto
- Follow explicit user/project language, then repository convention, then the
  current user interface or conversation language.
- Keep identifiers, paths, commands, API/schema/config fields, errors, logs,
  package names, model names, and stable template fields in English or their
  original form.

## Core Rules

- Treat native tasks as work surfaces and project docs as durable truth.
- Keep stable product behavior, architecture, ownership, accepted decisions,
  current risks, and current outcomes in project docs.
- Keep transient prompts, progress events, temporary plans, and ordinary task
  results in native task history.
- The main task owns project-level planning, unresolved module boundaries,
  cross-module decisions, result review, and project-state hygiene. It is not
  the only routing entrypoint.
- Before nontrivial execution, every main or registered module task must classify
  ownership. The task where the user asked is an intake surface, not proof of
  ownership.
- If another module owns the work, route it directly to that registered
  long-lived visible task. Do not implement it locally merely because the
  current task can.
- If ownership is unclear, perform only a minimal read-only impact scan. Route
  after likely owners are known; escalate unresolved boundaries to the main
  task or user.
- For cross-module work, select exactly one lead. The lead owns decomposition,
  shared contracts, integration, and result return; other modules receive
  explicit non-overlapping slices.
- Keep a lightweight native routing trace with request key, intake/source, lead,
  assigned slice, visited tasks, and return owner. Never route the same or a
  broader slice back to a visited task, broadcast blindly, or duplicate active
  work.
- The intake task remains responsible for giving its user a coherent result
  unless another return owner is explicitly named.
- Do not replace a long-lived module task with a temporary subagent. Use
  temporary subagents only for bounded disposable research, review, search,
  test, or verification work.
- A temporary subagent that discovers misowned work reports it to its
  parent/lead; it does not become another routing coordinator.
- Prefer native task tools for discovery, messaging, progress inspection,
  forking, handoff, and result review.
- Create a separate visible task only with the authorization required by the
  current product/runtime, then register its durable identity.
- Use native result delivery first. Update module `handoff.md` when durable
  cross-task or cross-tool recovery matters. Use Return Packets only when
  explicitly required by risk, audit, asynchronous work, or unavailable native
  delivery.
- Before every existing-task message or authorized new-task creation, classify
  the concrete task by type, complexity, risk, context, reversibility, and
  parallelism.
- Inspect the active tool schema, select a supported capability profile, and
  pass both `model` and `thinking` explicitly. Do not rely on target-task or
  user defaults.
- Use fast/low-medium for deterministic low-risk work, balanced/medium-high for
  normal work, strongest/high-xhigh for deep work, and strongest/max for
  critical work. Current GPT-5.6 examples are Luna, Terra, and Sol respectively.
- Explicit user choices win. Never silently downgrade deep/critical work when
  no safe supported model/Thinking combination exists.
- Keep routine routing data in the native dispatch prompt, not project docs.
- Update docs only for substantive state changes. Active docs are current
  snapshots, not task logs.
- Keep each fact in one primary home and link instead of copying.
- Never write secrets, credentials, private customer data, signed URLs, or
  access-granting links into committed docs.

## Read When Relevant

- Detailed runtime rules: `docs/thread-operating-model.md`
- Long-lived visible task map and module ownership: `docs/thread-registry.md`
- Current product truth: `docs/current-prd.md` or the project's existing PRD
- Current technical truth: `docs/current-technical-design.md` or existing design docs
- Current outcomes and WIP: `docs/current-work.md` or the issue tracker
- Module state: `docs/modules/<module>/status.md`
- Durable module handoff: `docs/modules/<module>/handoff.md`
- Recovery notes, only when needed: `docs/modules/<module>/runbook.md`
- Durable decisions: `docs/decisions/`
- Portable Controls, only when enabled: `docs/thread-runs/`, `docs/.locks/`,
  and `docs/archive/`

Do not read all runbooks, historical task records, archives, or unrelated ADRs
by default.

## Documentation Boundary

- `current-work.md` records what outcome is needed, not how to implement it.
- Put accepted implementation truth in technical design and durable tradeoffs
  in ADRs.
- Keep module handoffs compact and main-task relevant.
- Keep runbooks focused on current recovery context; do not append routine logs.
- Do not create optional roadmap, status, module design, runbook, thread-run,
  Return Inbox, lock, or archive files unless the project needs them.

## Docs Compaction

- Native conversation compaction does not compact project docs.
- Run LV2 docs-only compaction only after a real trigger: oversize, stale or
  duplicated content, contradictions, milestone closure, or task replacement.
- Ordinary targeted doc edits do not need a lock.
- Acquire `docs/.locks/context-compaction.lock` before broad shared-doc rewrites
  when concurrent tools/tasks may edit the same active docs.
- Do not use the compaction lock as a source-code, schema migration, deployment,
  or production execution lock; use the appropriate ownership or single-flight
  mechanism.
- LV2 must not change source, tests, production config, schemas, migrations,
  ADR decisions, product direction, module ownership, priority, or public
  contracts.
- Do not silently replace a stale lock; report it to the main task or user.

Do not invoke `$project-agent-operating-model` for routine implementation. Use
it for initialization, audit, repair, compaction, or operating-model upgrades.

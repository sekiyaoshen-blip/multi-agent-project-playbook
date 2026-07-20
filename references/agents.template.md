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
- Use system/Codex Desktop native result delivery first: native delegation
  return, `send_message_to_thread`, or `read_thread` inspection. If automatic
  return fails before output, prefer native read plus one compatibility-safe
  native send. Update module `handoff.md` only when durable recovery matters;
  use Return Packets only for explicit risk, audit, asynchronous work, or
  unavailable/unreliable native delivery.
- Before every existing-task message or authorized new-task creation, classify
  both the message and the receiving task's next work: review, integration,
  decision, context, risk, reversibility, and parallelism. Do not classify by
  message length or transport simplicity alone.
- A pure receipt-only acknowledgement may use `fast`. Ordinary owner-result
  review is at least `balanced`. Production evidence, acceptance verdicts,
  project gate updates, cross-module integration, or long/risky context are
  normally `deep`.
- Inspect the active tool schema and select a supported, Desktop-compatible
  model/Thinking pair. Current GPT-5.6 roles are Luna for `fast`, Terra for
  `balanced`, and Sol for `deep`/`critical`; exact IDs are runtime-discovered.
- Intersect tool-level values with the selected model/path capability; a tool
  enum may be broader than one model. Default `critical` to `xhigh`. Use `max`
  only with exact model/path confirmation; GPT-5.5 must never receive `max`.
- Autonomous routing may select only GPT-5.6 or GPT-5.5 families. Prefer GPT-5.6
  and use GPT-5.5 only as a compatibility fallback. Do not autonomously select
  GPT-5.4, mini/nano, Codex-Spark, or older families.
- Do not use GPT-5.3-Codex-Spark or another preview/specialized model for visible
  cross-task delivery unless the current product confirms compatibility with
  Desktop-managed turn parameters.
- If the visible tool does not expose `reasoning.summary`, do not claim the
  source task set it. On a pre-output optional-parameter compatibility failure,
  retry once with the same request key/prompt. Omit overrides only when the
  target's current GPT-5.5/5.6 model/Thinking pair is confirmed compatible;
  otherwise explicitly use a compatible pair. Never retry after target output.
- If a pre-output error lists supported Thinking values, retry once with the
  same model/request key/prompt and highest safe listed effort (`xhigh` for a
  rejected GPT-5.5 `max`).
- Explicit user choices win. Never silently downgrade deep/critical work when
  no safe supported model/Thinking combination exists.
- Treat a `Routing:` line as observability only; actual tool arguments and
  product compatibility are authoritative.
- Keep routine routing data in the native dispatch prompt, not project docs.
- Preserve one visible mainline in each long-lived owner task. Keep task-local
  self-verification with the owner; route unrelated cross-task checks to a
  bounded verifier with a `VAL-*` key and a fixed target when possible.
- Verification is read-only by default. Findings that require changes become a
  separate `TASK-*`; do not let a verifier silently become an implementer.
- Classify external verification as `background`, `checkpoint`, `blocking`, or
  `emergency`. Only an active severe production, data-loss, security,
  credential, or irreversible-failure risk may immediately preempt a focused
  owner. Blocking work waits for the next safe checkpoint.
- Pull pass/informational results from native task state at safe checkpoints;
  do not push them into the owner task. Push actionable failure, decision,
  blocker, or emergency results through native delivery at the allowed point.
- Use an optional `docs/.locks/focus/` Focus Lease only when concurrent tools or
  tasks create a real interruption risk. It protects attention, not files,
  branches, migrations, deployments, or transactions. Never silently replace a
  stale lease.
- File-based verification requests/results are Portable Controls for cross-tool,
  audit, asynchronous, or unreliable native delivery, not routine requirements.
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
- Non-preemptive verification details, only when enabled:
  `docs/verification-operating-model.md`

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

Do not invoke `$multi-agent-model` for routine implementation. Use
it for initialization, audit, repair, compaction, or operating-model upgrades.

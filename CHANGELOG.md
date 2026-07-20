# Changelog

## Unreleased

- Renamed the project, skill invocation, and installation directory from
  `project-agent-operating-model` to `multi-agent-model`.
- Added an optional non-preemptive verification side lane with fixed targets,
  read-only-by-default execution, and separate `VAL-*` requests.
- Added cooperative Focus Leases across tools/sessions and four interruption
  classes: `background`, `checkpoint`, `blocking`, and `emergency`.
- Switched routine verification to pull-based native result harvesting at safe
  checkpoints; file requests/result packets remain opt-in Portable Controls.
- Replaced the hard-coded `critical` -> `max` mapping with portable `xhigh` and
  require exact model/path confirmation before using `max` or `ultra`.
- Added model-specific Thinking validation because tool schemas may expose a
  union broader than one model; GPT-5.5 cross-task calls are capped at `xhigh`.
- Added one safe pre-output retry using the highest effort listed by the runtime
  error while preserving the model, request key, and prompt.
- Changed model routing to classify the receiver's review, integration,
  decision, and execution duty instead of the transport message alone.
- Added receiver floors so production evidence, acceptance verdicts, project
  gate updates, and cross-module integration cannot be routed as `fast` merely
  because the return payload is short.
- Excluded GPT-5.3-Codex-Spark and other unconfirmed preview/specialized models
  from visible cross-task delivery, and refreshed current examples to the
  GPT-5.6 Luna/Terra/Sol capability family.
- Documented that hidden `reasoning.summary` injection belongs to the Desktop
  turn-start layer when the visible tool does not expose that field.
- Added a single compatibility retry that preserves the request key/prompt,
  keeps target settings only when the current GPT-5.5/5.6 model/Thinking pair
  is confirmed compatible, and otherwise selects a compatible pair.
- Made system/Codex Desktop native delivery the preferred return path, including
  native read plus one compatibility-safe native send before file fallback.
- Limited autonomous model selection to GPT-5.6 and GPT-5.5 families, preferring
  GPT-5.6 and reserving GPT-5.5 for compatibility fallback.
- Added an every-task ownership gate: the main task and every registered module
  task classify ownership before nontrivial execution.
- Added direct module-to-module re-routing for misrouted requests, minimal
  read-only impact discovery for unclear ownership, and one-lead cross-module
  decomposition.
- Added native routing traces and guards against cycles, blind broadcast,
  duplicate active work, unauthorized task creation, and competing
  coordinators.
- Clarified that the intake task remains responsible for a coherent user result
  unless another return owner is explicitly named.
- Added mandatory dispatch-time task classification for every existing-task
  message and authorized new-task creation.
- Added explicit model/Thinking control for normal native task invocations, now
  bounded by receiver-aware classification and Desktop compatibility fallback.
- Added fast/balanced/deep/critical routing profiles, active-tool capability
  discovery, explicit fallback reasons, and no-silent-downgrade rules for
  high-risk work.
- Made sensitive-domain routing action-based so read-only investigation does
  not become `critical` merely because it mentions security or payments.
- Reworked the skill for GPT-5.6 and the unified ChatGPT Desktop/Codex task
  experience.
- Made Native Mode the default: the main task routes module-owned work to
  registered long-lived visible module tasks through native task tools.
- Restricted temporary subagents to bounded disposable work instead of using
  them as replacements for durable module tasks.
- Reduced `thread-operating-model` from more than 1,100 lines to a compact
  native-first contract.
- Replaced the registry's duplicate dispatch queue with a small module ownership
  and native task identity map.
- Made thread-runs, Return Packets, archives, and compaction locks opt-in
  Portable Controls.
- Removed hard-coded GPT-5.3 Spark/GPT-5.5 quota routing and routine model
  telemetry; current model/Thinking values are discovered and explicitly
  passed at dispatch time.
- Added capability-oriented GPT-5.6 guidance for Sol, Terra, Luna, and
  parallel/Ultra-style execution without making model names durable contracts.
- Added contract-first cross-module dispatch guidance and clarified that docs
  compaction locks are not schema-migration or production execution locks.
- Removed optional roadmap, global status, module PRD/design, task-run, return
  packet, and compaction-note examples from the default project skeleton.
- Updated English and Chinese one-prompt installation and Native Mode project
  initialization prompts.

- Renamed package from `project-thread-orchestration` to
  `project-agent-operating-model`.
- Added MIT License and public repository support files.
- Preserved the single-skill architecture: bootstrap/audit/repair/compact/upgrade only.
- Added and preserved Chinese documentation: `README.zh-CN.md` and `INSTALL.zh-CN.md`.

- Added LV2 controlled autonomous docs-only compaction policy.
- Added cross-tool and cross-thread Compaction Lock protocol under `docs/.locks/`.
- Added explicit compaction check trigger points and LV2 execution trigger points.
- Added optional `CLAUDE.md` template to share `AGENTS.md` with Claude Code workflows.
- Added one-prompt installation instructions for Codex, Claude Code, and other local agents.

- Added current snapshot layer: `docs/current-prd.md`, `docs/current-technical-design.md`, and `docs/current-work.md`, plus optional module PRD/technical-design templates.
- Clarified `docs/current-work.md` as a solution-neutral what-to-do board: record outcomes, priorities, owners, risks, and decisions needed, but keep implementation strategies and how-to plans in technical design, ADRs, thread-runs, dispatch payloads, or module docs.

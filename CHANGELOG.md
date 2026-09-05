# Changelog

## Unreleased

- Strengthened existing preferences: useful work before clarification, relevant
  technical detail, behavior-focused tests, bounded delegation, and cleanup
  limited to disposable files created by the current task. No new workflow.

- Simplified defaults using current Codex native coordination and GPT-6 Astra
  prompting guidance; retained model-independent behavior and module ownership.
- Reduced the default project skeleton to three conditional files. Product,
  design, handoff, runbook, verification, and portable-control templates are
  no longer default installation or startup requirements.
- Replaced routine dispatch forms with short native messages and proportional
  testing; independent verification and extra controls require a concrete need.
- Added separate opt-in Chinese personal preferences and capability/source notes.

### Earlier Changes

- Removed model selection, reasoning-effort profiles, provider branches, and
  model compatibility fallbacks from dispatch, forwarding, and result returns.
- Renamed the project, skill invocation, and installation directory from
  `project-agent-operating-model` to `multi-agent-model`.

- Added an optional non-preemptive verification side lane with fixed targets,
  read-only-by-default execution, and separate `VAL-*` requests.
- Added cooperative Focus Leases across tools/sessions and four interruption
  classes: `background`, `checkpoint`, `blocking`, and `emergency`.
- Switched routine verification to pull-based native result harvesting at safe
  checkpoints; file requests/result packets remain opt-in Portable Controls.

- Made system/Codex Desktop native delivery the preferred return path, including
  native read plus one native send before file fallback.

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

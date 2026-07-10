# Changelog

## Unreleased

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
  telemetry; current clients inherit their configured model by default.
- Added capability-oriented GPT-5.6 guidance for Sol, Terra, Luna, and
  parallel/Ultra-style execution without making model names durable contracts.
- Added contract-first cross-module dispatch guidance and clarified that docs
  compaction locks are not schema-migration or production execution locks.
- Removed optional roadmap, global status, module PRD/design, task-run, return
  packet, and compaction-note examples from the default project skeleton.
- Updated English and Chinese one-prompt installation and Native Mode project
  initialization prompts.

- Renamed package from `project-thread-orchestration` to `project-agent-operating-model`.
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

# Multi-Agent Model

[中文说明](README.zh-CN.md) | [Installation](INSTALL.md)

A Codex skill for stable module ownership with minimal coordination overhead.
Use it to initialize or simplify collaboration, not for every implementation.

## Default Workflow

- A simple feature, page, or fix: implement in the existing stack, run relevant
  checks, deliver, and stop. No automatic architecture or audit workflow.
- One task: a short `AGENTS.md` is enough.
- Several stable modules: add an ownership registry and reuse long-lived visible
  module tasks. Any task can route directly to the actual owner.
- Cross-module work: one lead, non-overlapping slices, and only the shared
  interface decisions needed for the requested outcome.
- Independent subagents: useful bounded work within the lead's scope, not
  replacements for registered module owners.
- Execution state: native tasks and existing trackers, not duplicate file logs.
- Durable facts: update their existing documentation only when they change.

Native search, messaging, waits, result inspection, fork, and handoff are the
preferred coordination tools when available. Creating a separate visible task
still requires explicit user authorization.

## What Is No Longer Default

Do not automatically create PRDs, architecture documents, status/handoff/runbook
sets, formal dispatch forms, hash ledgers, locks, independent verification tasks,
or return packets. Existing project requirements and concrete high-impact risks
still apply. Optional controls remain available in `references/`.

The [capability notes](references/codex-native-notes.md) explain the relevant
March-September 2026 Codex updates and GPT-6 Astra prompting implications.
This skill contains no model selection, provider routing, or fallback policy.

## Project Skeleton

The skeleton is a menu, not a copy-all bundle:

```text
AGENTS.md                       project entrypoint
docs/thread-registry.md         only for stable visible module tasks
docs/current-work.md            only if a shared snapshot is missing
```

Reuse existing project docs and work trackers. Extended operating notes,
product/design templates, and recovery controls are optional references.
Upgrading the skill does not silently migrate every existing project.

## Personal Preferences

The [Chinese global preference example](references/personal-instructions.zh-CN.md)
keeps language, concise delivery, proportional testing, Git boundaries, and
existing commit/deploy workflows outside the project collaboration contract.

Installing the skill does not change personal settings. Apply that example to
the supported global `AGENTS.md` only when the user requests it; merge existing
preferences instead of overwriting them. Do not duplicate old and new preference
blocks in multiple settings surfaces.

## License

[MIT](LICENSE).

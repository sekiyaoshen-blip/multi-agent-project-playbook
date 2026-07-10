# Contributing

Thanks for considering a contribution to Project Agent Operating Model.

## Guidelines

- Keep `SKILL.md` thin. Runtime rules should usually live in project docs or `references/` templates.
- Preserve the native-first principle: current models decompose, native visible
  tasks execute, and project docs preserve durable truth.
- Keep long-lived module task routing explicit; do not replace it with mandatory
  temporary subagents or file-based task telemetry.
- Keep dispatch-time model routing explicit and capability-driven: every native
  invocation passes supported `model` and `thinking` values, while exact model
  IDs remain discoverable current mappings rather than permanent contracts.
- Keep public-facing docs in English by default, while preserving localization hooks for project-specific use.
- Keep code identifiers, paths, commands, APIs, schema fields, logs, model names, and stable template fields in English or original form.
- Avoid adding append-only project history to active templates. Prefer snapshot + archive patterns.

## Pull Request Checklist

- [ ] `SKILL.md` remains focused on bootstrap/audit/repair/upgrade work.
- [ ] Templates and project skeleton are consistent.
- [ ] Thread-runs, Return Packets, locks, and archives remain opt-in controls.
- [ ] Model guidance does not hard-code stale quota or version assumptions.
- [ ] Existing/new native task calls classify risk and pass explicit model and
  Thinking parameters without silently downgrading high-risk work.
- [ ] Context governance rules are not duplicated across many files unless necessary.
- [ ] Markdown code fences are balanced.
- [ ] `MANIFEST.md` is regenerated if package contents changed.

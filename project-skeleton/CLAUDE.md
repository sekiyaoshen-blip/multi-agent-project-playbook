@AGENTS.md

## Claude Code

Follow the Multi-Agent Model.

Use this file only as the Claude-specific entry point. Do not duplicate the full operating model here; update `AGENTS.md` or `docs/thread-operating-model.md` instead.

Before changing project-state docs:

- Read `docs/thread-operating-model.md` when the task involves long-lived module
  routing, cross-tool handoff, recovery, or docs compaction.
- Treat Codex native task identities as routing handles and project docs as the
  shared durable source of truth.
- Use compact module handoffs for cross-tool return. Use Return Packets only
  when native delivery is unavailable/insufficient or project policy requires
  an audit packet.
- For unrelated cross-task verification, use the optional non-preemptive
  `VAL-*` lane, fixed targets, and read-only execution. Check a relevant Focus
  Lease before pushing a result; pass/informational results remain pull-only.
- For broad shared active-doc cleanup, check `docs/.locks/` and acquire
  `docs/.locks/context-compaction.lock` when concurrent tools/tasks may edit the
  same docs.
- Keep active docs as current snapshots, not append-only logs.

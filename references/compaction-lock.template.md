# Compaction Lock

Use only for broad shared active-doc rewrites when concurrent tools/tasks may
edit the same files. Ordinary targeted doc updates do not need this lock.

- Lock ID: LOCK-YYYYMMDD-HHMM-<short-id>
- Safety mode: LV2-docs-only
- Status: active | stale | released

## Owner

- Tool: codex | claude-code | other-agent | automation | human
- Native task / thread / session ID:
- Task / run ID, if any:

## Scope

- Project / module:
- Files locked:
  - `docs/<active-doc>.md`
- Explicitly out of scope:
  - source, tests, production config, schemas, migrations, credentials
  - ADR decisions, product direction, module ownership, priority, public contracts

## Timing

- Started at: YYYY-MM-DD HH:MM
- Last heartbeat: YYYY-MM-DD HH:MM
- Expected release: YYYY-MM-DD HH:MM
- Stale after: YYYY-MM-DD HH:MM

## Trigger

- oversize | stale | duplicated | contradictory | milestone-closed | task-replaced | user-reported-confusion
- Details:

## Safety Checks

- [ ] Workspace state checked
- [ ] No active conflicting owner found
- [ ] Cleanup is docs-only
- [ ] Affected docs are not owned by another active task
- [ ] Useful history will be summarized or archived when needed
- [ ] Final diff will be small enough to review

## Progress / Release

- Completed:
- Remaining:
- Compaction note:
- Released at:

Do not silently overwrite a stale lock. Report it and let the main task or user
decide takeover.

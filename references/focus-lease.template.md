# Focus Lease: <task-or-module>

Last updated: YYYY-MM-DD HH:MM

This optional cooperative lease protects a long-lived owner's visible mainline
from unrelated task injection. It applies across tools and across separate
sessions in the same tool. It is not a file, branch, migration, deployment, or
transaction lock.

## Identity

- Lease ID: `FOCUS-<task-or-module>-<timestamp>`
- Owner tool:
- Owner task/session ID:
- Owner role: main | module | support | operations | research | verification
- Module/scope:
- Active task:

## Focus State

- State: focused | checkpoint-open | idle | blocked | released | stale
- Interrupt policy: no-interrupt | checkpoint-only | blocking-only | emergency-only
- Started at:
- Last heartbeat:
- Safe delivery after: next checkpoint | next commit | current task return | immediately | <event>
- Stale after:
- Status: active | stale | released

## Protected Mainline

- Current objective:
- Unstable operation, if any:
- Worktree/branch/files involved:
- Why interruption would be costly:

## Queued Work

- Background:
- Checkpoint:
- Blocking:
- Emergency:

## Rules

- Other tasks may queue `VAL-*` work while this lease is active.
- `background` remains pull-only; `checkpoint` waits for the safe event.
- `blocking` may be delivered at the next safe checkpoint.
- Only `emergency` may immediately preempt the owner.
- Refresh the heartbeat only at meaningful checkpoints; release the lease when
  the owner can safely accept work.
- Never silently overwrite a stale lease. Report it for explicit takeover.

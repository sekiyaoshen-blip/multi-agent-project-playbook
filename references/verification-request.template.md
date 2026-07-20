# Verification Request: VAL-<id>

- Source task:
- Related implementation task:
- Owner/return owner:
- Verifier:
- Native task/subagent link or ID:
- State: queued | running | blocked | completed | stale | superseded
- Interrupt class: background | checkpoint | blocking | emergency
- Dedupe key: `<target-id>:<scope>:<check-kind>`

## Focus Lease Check

- Owner lease path, if Portable Controls are enabled:
- Lease state/policy:
- Allowed delivery point:

## Fixed Target

- Target type: commit | diff | recorded branch head | checkpoint | artifact | worktree
- Target identity:
- Recorded at:
- Stale if:

## Scope

- Question to answer:
- Acceptance criteria:
- Checks to run:
- Evidence required:
- Out of scope:

## Execution Boundary

- Read-only by default: yes
- Explicitly authorized writes, if any:
- A discovered fix becomes a separate `TASK-*`: yes

## Result Delivery

- Primary: native completion/read
- Push only for: actionable failure | decision | blocker | emergency
- File packet required: no | yes, because <cross-tool/audit/async/unreliable-native-state>
- Safe harvest/delivery event:

# Verification Operating Model

Last updated: YYYY-MM-DD

Use this optional document when independent verification could interrupt a
long-lived owner task, or when fixed-target evidence must cross task/tool
boundaries. Keep the lightweight activation rule in `AGENTS.md`; do not install
this document for a project that only needs task-local self-verification.

## Contents

- Activation boundary
- Verification request contract
- Focus Leases
- Interruption classes
- Fixed targets and read-only execution
- Pull-based results
- Harvest timing
- Recovery and hygiene

## Activation Boundary

Each long-lived main or module task keeps one visible execution mainline.

The owner keeps:

- tests and checks required by its current task;
- self-review before its own commit or handoff;
- checks that require unique state available only in that task.

Route unrelated cross-task review, testing, security analysis, evidence checks,
or collaborative validation to a bounded verifier. Prefer a native bounded
subagent for disposable work and a visible task only when the user has
authorized a durable user-facing verification task.

Use `TASK-*` for implementation and `VAL-*` for verification. A `VAL-*` must
not silently become implementation. Create or propose a separate `TASK-*` when
a fix is needed.

## Verification Request Contract

Each independent check declares:

- `VAL-*` request key and dedupe key;
- source task, owner, return owner, and verifier;
- exact scope and acceptance criteria;
- immutable target or recorded target identity;
- interruption class;
- read-only boundary and explicitly excluded work;
- expected evidence and safe result-delivery point.

Keep the request in native task history by default. Create a file-based request
only when Portable Controls are enabled for cross-tool, audit, asynchronous, or
unreliable-native-state work.

## Focus Leases

A Focus Lease is an optional cooperative interruption lock under:

```text
docs/.locks/focus/<task-or-module>.lock
```

Use it only when multiple tools or tasks could inject unrelated work into a
focused long-lived owner. It protects the owner's attention and mainline; it
does not lock source files, branches, worktrees, migrations, deployments,
schemas, or transactions.

The lease records owner tool/task identity, active task, focus state,
interruption policy, safe-delivery event, heartbeat, expiry, and release state.
Separate sessions in the same tool are separate owners.

Other tasks may queue work while a lease is active, but ordinary verification
must respect its interruption policy. Never silently overwrite a stale lease.
Mark/report it and let the main task, user, or designated coordinator decide
takeover.

## Interruption Classes

| Class | Owner delivery | Use |
|---|---|---|
| `background` | No push; pull later | Default independent check |
| `checkpoint` | Next declared safe checkpoint | Input/review needed soon |
| `blocking` | Next safe checkpoint; dependent acceptance waits | Work cannot safely proceed without result |
| `emergency` | Immediate preemption allowed | Active severe production, data-loss, security, credential, or irreversible-failure risk |

`blocking` is not permission to interrupt an unstable edit, migration, critical
operation, or unfinished test-fix cycle. The owner first reaches the smallest
safe checkpoint. Use `emergency` narrowly and record the evidence and affected
scope.

## Fixed Targets And Read-Only Execution

Prefer one fixed target:

- commit SHA or PR diff;
- branch head recorded at dispatch;
- checkpoint commit;
- build/deployment artifact;
- isolated worktree snapshot.

Avoid another task's actively changing unsaved workspace. A useful dedupe key
is `<target-id>:<scope>:<check-kind>`. If the target changes during verification,
mark the result `stale`; do not treat it as evidence for the new target.

Verification is read-only by default. A verifier may read code/docs, inspect
diffs, run tests/static analysis, observe product behavior, collect evidence,
and report findings. It must not silently edit production code, refactor the
owner module, expand scope, or change public contracts.

## Pull-Based Results

Native task state is the primary delivery surface:

1. The verifier finishes in its own task/subagent and records concise evidence.
2. The lead/owner pulls with native task completion state or `read_thread` at a
   safe harvest point.
3. `pass` and informational results remain pull-only; do not inject them into a
   focused owner task.
4. Route actionable failure, decision, blocker, or emergency through native
   system/Desktop delivery at the interruption point allowed by its class.
5. Use a file-based result packet only when Portable Controls are required.

| Result | Default handling |
|---|---|
| `pass` | Close during the next harvest; no owner push |
| `pass-with-notes` | Include in a later batch summary |
| `fail-non-blocking` | Propose a follow-up `TASK-*` |
| `fail-blocking` | Hold dependent acceptance and deliver at next safe checkpoint |
| `needs-decision` | Route to the lead/main task at a safe checkpoint |
| `emergency` | Immediately notify affected owner/main task |
| `stale` | Requeue against a current fixed target if still needed |

Do not require both native delivery and a file packet for ordinary work.

## Harvest Timing

Check queued verification and completed results:

- before starting a new owner task;
- after an explicit checkpoint or stable commit;
- when the owner becomes blocked or idle;
- before milestone acceptance, merge, release, or deployment review;
- at a configured validation sweep.

Do not harvest ordinary external results during unstable multi-file edits,
migrations, complex debug loops, unfinished test-fix cycles, active high-risk
operations, or a valid focused lease whose policy blocks delivery.

## Recovery And Hygiene

Do not turn long-lived owner tasks into validation queues, result archives, or
generic workers. If unrelated verification has polluted an owner task:

1. Save the current owner checkpoint and durable handoff.
2. Start or resume a clean owner continuation using native task tools.
3. Mark the old task superseded/read-only when the product supports it.
4. Route future independent checks through this side lane.

Keep routine request/result telemetry in native history. Archive file-based
verification records only when they were required and their retained evidence
still has value.

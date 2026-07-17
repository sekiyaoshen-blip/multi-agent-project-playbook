# Main Task Dispatch

- Request key:
- Intake/source task:
- Target long-lived module task: `<module>`
- Native task ID/link: <from `docs/thread-registry.md`>
- Lead task/module:
- Assigned slice:
- Visited tasks/modules:
- Return owner:
- Type: implement | investigate | review | verify | unblock | decide
- Priority: P0 | P1 | P2 | P3

## Desired Outcome

- What should be true when this task is done:

## Ownership Reason

- Why this belongs to the target module:

## Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2

## Context

- Relevant files/docs:
- Lead module and shared contract, for cross-module work:
- Dependencies:
- Constraints / do not change:
- Known risks:

## Verification

- Required checks:
- Manual review, if any:

## Escalate When

- Product direction, architecture, security, priority, public contract, or
  another module's ownership must change.

## Return

- Default: return through native task delivery so the main task can review it.
- Update module `handoff.md` only if durable project context changed.
- Portable Controls enabled: no | thread-run | Return Packet | both
- If enabled, path/reason:

## Dispatch-Time Model Routing (Required)

- Classification:
  - Type:
  - Receiver follow-up: ack-only | routine-review | integrate-state | acceptance-review | gate-update | execute-action
  - Complexity: deterministic | normal | ambiguous | highly-coupled
  - Risk: low | moderate | high | critical
  - Context: short | multi-file/module | long-history
  - Reversibility: easy | costly | irreversible
  - Parallelism: single-owner | independent-slices | tightly-coupled
- Profile: fast | balanced | deep | critical
- Selected supported model ID:
- Selected supported Thinking: low | medium | high | xhigh | max only when exact model/path support is confirmed
- Model-specific Thinking checked: yes | no
- Active tool schema checked: yes | no
- Desktop compatibility checked: yes | no
- Autonomous candidate family: GPT-5.6 | GPT-5.5
- Fallback, if any:
- One-line reason:

Classify the target's follow-up work, not just the transport message. Normally
pass both `model` and `thinking`. Do not use GPT-5.3-Codex-Spark for visible
cross-task delivery without current Desktop compatibility confirmation. If a
hidden optional reasoning parameter causes a pre-output compatibility failure,
retry once with the same request key/prompt. Omit overrides only when the
target's current GPT-5.5/5.6 model/Thinking pair is confirmed compatible;
otherwise use a compatible pair. Never retry after target output.

The target may re-route a misowned slice directly to another registered task,
but it must preserve the request key, extend the visited list, keep one lead,
and never send the same or broader slice back to a visited task.

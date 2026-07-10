# Main Task Dispatch

- Target long-lived module task: `<module>`
- Native task ID/link: <from `docs/thread-registry.md`>
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
  - Complexity: deterministic | normal | ambiguous | highly-coupled
  - Risk: low | moderate | high | critical
  - Context: short | multi-file/module | long-history
  - Reversibility: easy | costly | irreversible
  - Parallelism: single-owner | independent-slices | tightly-coupled
- Profile: fast | balanced | deep | critical
- Selected supported model ID:
- Selected supported Thinking: low | medium | high | xhigh | max | <tool-supported>
- Active tool schema checked: yes | no
- Fallback, if any:
- One-line reason:

Pass both `model` and `thinking` as invocation parameters. Do not rely on the
target task's existing settings or user defaults.

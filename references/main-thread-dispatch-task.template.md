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

- Service: official OpenAI | non-OpenAI | unknown
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
- OpenAI allowlist checked: `gpt-5.6-sol` | `gpt-5.6-terra` | `gpt-5.6-luna` | not applicable
- Non-OpenAI default mode: yes | no | not applicable
- Fallback, if any:
- One-line reason:

Classify the target's follow-up work, not just the transport message. On
official OpenAI service, use only Luna/fast, Terra/balanced, and
Sol/deep/critical. The only compatibility fallback is Luna with `medium`, for
one pre-output retry when it satisfies the receiver floor. Never use GPT-5.5 or
older. On non-OpenAI or unknown service, omit `model` and `thinking` and retain
provider defaults. Never retry after target output.

The target may re-route a misowned slice directly to another registered task,
but it must preserve the request key, extend the visited list, keep one lead,
and never send the same or broader slice back to a visited task.

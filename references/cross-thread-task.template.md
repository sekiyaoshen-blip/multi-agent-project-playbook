# Cross-Task Request

- Request key:
- Intake task/module:
- Source task/module:
- Target long-lived task/module:
- Native target ID/link:
- Lead task/module:
- Assigned slice:
- Visited tasks/modules (do not route the same or broader slice back):
- Return owner:
- Request type: implement | investigate | review | verify | unblock | decide

## Desired Outcome

- Result needed:

## Ownership Reason

- Why the target owns this work:

## Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2

## Inputs And Constraints

- Relevant files/docs:
- Inputs from source module:
- Dependencies:
- Must preserve:

## Expected Verification

- Checks or evidence:

## Return

- Default native return target:
- Durable handoff path, only if needed:
- Portable Controls enabled: no | thread-run | Return Packet | both

## Dispatch-Time Model Routing (Required)

- Service: official OpenAI | non-OpenAI | unknown
- Receiver follow-up: ack-only | routine-review | integrate-state | acceptance-review | gate-update | execute-action
- Receiver risk/context:
- Task profile: fast | balanced | deep | critical
- Selected supported model ID:
- Selected supported Thinking:
- Model-specific Thinking checked: yes | no
- Desktop compatibility checked: yes | no
- OpenAI allowlist checked: `gpt-5.6-sol` | `gpt-5.6-terra` | `gpt-5.6-luna` | not applicable
- Non-OpenAI default mode: yes | no | not applicable
- Classification reason: <type/complexity/risk/context/reversibility>
- Fallback, if any:

Classify the receiver's follow-up, not just this message. Use `fast` only for
ack-only work; ordinary review is at least `balanced`; production evidence,
acceptance/gate review, cross-module integration, or long/risky context are
normally `deep`. On official OpenAI service, use only Luna/fast,
Terra/balanced, and Sol/deep/critical. The only compatibility fallback is Luna
with `medium`, for one pre-output retry when it satisfies the receiver floor.
Never use GPT-5.5 or older. On non-OpenAI or unknown service, omit `model` and
`thinking` and retain provider defaults. Do not retry after output. Use `max`
only with exact model/path support.

If this target does not own the slice, preserve the request key, extend the
visited list, keep exactly one lead, and re-route only to a registered likely
owner. Stop and escalate instead of looping, broadcasting, duplicating active
work, or creating an unauthorized visible task.

## Priority / Deadline

- Priority:
- Deadline, if any:

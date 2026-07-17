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

- Receiver follow-up: ack-only | routine-review | integrate-state | acceptance-review | gate-update | execute-action
- Receiver risk/context:
- Task profile: fast | balanced | deep | critical
- Selected supported model ID:
- Selected supported Thinking:
- Model-specific Thinking checked: yes | no
- Desktop compatibility checked: yes | no
- Autonomous candidate family: GPT-5.6 | GPT-5.5
- Classification reason: <type/complexity/risk/context/reversibility>
- Fallback, if any:

Classify the receiver's follow-up, not just this message. Use `fast` only for
ack-only work; ordinary review is at least `balanced`; production evidence,
acceptance/gate review, cross-module integration, or long/risky context are
normally `deep`. Do not use GPT-5.3-Codex-Spark for visible cross-task delivery
without current Desktop compatibility confirmation.

Autonomous selection is limited to GPT-5.6/5.5. Normally pass both values. On a
pre-output hidden-parameter failure, retry once with the same request key and
prompt. Omit overrides only when the target's current GPT-5.5/5.6
model/Thinking pair is confirmed compatible; otherwise choose a compatible
pair. Do not retry after output.
The tool enum may exceed one model's capability: default `critical` to `xhigh`,
never send GPT-5.5 with `max`, and use `max` only with exact model/path support.

If this target does not own the slice, preserve the request key, extend the
visited list, keep exactly one lead, and re-route only to a registered likely
owner. Stop and escalate instead of looping, broadcasting, duplicating active
work, or creating an unauthorized visible task.

## Priority / Deadline

- Priority:
- Deadline, if any:

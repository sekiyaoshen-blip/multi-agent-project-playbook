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

- Task profile: fast | balanced | deep | critical
- Selected supported model ID:
- Selected supported Thinking:
- Classification reason: <type/complexity/risk/context/reversibility>
- Fallback, if any:

Pass both values through the native invocation. Do not rely on inherited target
settings.

If this target does not own the slice, preserve the request key, extend the
visited list, keep exactly one lead, and re-route only to a registered likely
owner. Stop and escalate instead of looping, broadcasting, duplicating active
work, or creating an unauthorized visible task.

## Priority / Deadline

- Priority:
- Deadline, if any:

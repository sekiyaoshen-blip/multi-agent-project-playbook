# Portable Return Packet: RET-<task-id>-<module>-<timestamp>

Use only when native result delivery is unavailable/insufficient, work crosses
tools or asynchronous queues, or project policy requires a durable audit packet.

Last updated: YYYY-MM-DD HH:MM

## Routing

- Task ID:
- Source task/module:
- Target reviewer: Main Task
- Related thread-run, if any:
- Return reason: cross-tool | asynchronous | audit | native-delivery-unavailable | policy

## Result

- State: completed | partial | blocked | failed | needs-decision | superseded
- Summary:
- What remains:

## Acceptance Criteria

- [ ] Criterion 1: <result>
- [ ] Criterion 2: <result>

## Verification

- Checks run and results:
- Checks not run and reasons:

## Risks Or Decisions Needed

- Risk/decision:
- Impact:
- Recommended next action:

## Durable Changes

- Product/technical/ownership truth changed: yes | no
- Docs updated or proposed:
- ADR needed: yes | no

## Recovery

- Safe to resume: yes | no
- Safe to re-run: yes | no
- Do not repeat:

## Main Task Review

- Review state: pending | accepted | needs-followup | failed | superseded
- Reviewed at:
- Follow-up:
- Archive/delete destination:

After review, remove this packet from the active inbox. The inbox contains only
unprocessed packets.

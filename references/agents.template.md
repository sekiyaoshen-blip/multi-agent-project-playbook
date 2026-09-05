# Project Agent Instructions

Use the user's language and repository conventions. Read only context relevant
to the current request.

## Delivery

- Prefer the smallest working change in the existing stack. Implement, run
  relevant checks, and finish when the requested outcome is met.
- Do not add architecture, abstractions, formal contracts, audit artifacts, or
  extra reviews without a concrete need. Preserve required project checks.
- Keep ordinary tests with the implementer. Delegate only useful independent
  slices; a small task needs neither a plan document nor a verifier task.
- Update existing docs only when their maintained facts changed. Native task
  history holds routine progress; each durable fact has one primary home.
- Preserve unrelated changes and active owners. Never commit secrets.

## Ownership And Native Tasks

- If this project has a module registry, check the relevant ownership before
  substantive work. Answer-only or clearly local work needs no routing ceremony.
- Route another module's work directly to its registered long-lived visible
  task. A quick read-only impact check is enough when ownership is uncertain.
- For cross-module work, keep one lead, explicit non-overlapping slices, and
  only the shared interface decisions actually needed. Continue independent work.
- The intake task returns the final answer unless another return owner is named.
  Dispatch in a short native message: outcome, scope, context, return destination.
- Check active work when overlap is plausible. Do not broadcast, duplicate work,
  or route a slice in circles; resolve that slice with the lead.
- Reuse existing visible module tasks. Create new visible tasks only with
  explicit user authorization and runtime support.
- Temporary subagents can handle bounded independent work inside an owner's
  scope, but do not replace stable module owners or become routing coordinators.
- Prefer native task discovery, messaging, waits, and result inspection. Review
  delegated results before claiming completion; avoid unchanged-state polling
  and unrelated messages to a busy owner.
- Use native fork, handoff, or scheduling only when relevant and authorized.
  Their availability and interruption behavior depend on the current tools.

Read `docs/thread-registry.md` if present; otherwise do not invent module roles.
Use the existing work tracker and relevant product/technical docs. Additional
operating notes, handoffs, locks, packets, and independent verification are
optional, not required startup reading. Invoke `$multi-agent-model` only to
initialize or change the collaboration setup.

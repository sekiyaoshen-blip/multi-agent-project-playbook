# Project Agent Instructions

Use the user's language and repository conventions. Read only context relevant
to the current request.

## Delivery

- Prefer the smallest working change in the existing stack. Implement, run
  relevant checks, and finish when the requested outcome is met.
- Do not add architecture, abstractions, formal contracts, audit artifacts, or
  extra reviews without a concrete need. Preserve required project checks.
- Keep ordinary tests with the implementer; test behavior and regression risks,
  not merely implementation details. After relevant checks pass, expand or
  repeat them only for new changes, failures, or unresolved doubts. A small task
  needs neither a plan document nor a verifier task.
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
  Dispatch in a short native message: scope, necessary inputs, expected output,
  completion criteria, and return destination. No extra form is needed.
- Check active work when overlap is plausible. Do not broadcast, duplicate work,
  or route a slice in circles; resolve that slice with the lead.
- Reuse existing visible module tasks. Create new visible tasks only with
  explicit user authorization and runtime support.
- Delegate only genuinely independent work when it saves time or improves
  quality. Keep coupled shared-state work and sequential decisions with the
  responsible owner. Subagents do not replace stable module owners or become
  routing coordinators; the lead integrates and verifies their results.
- Prefer native task discovery, messaging, waits, and result inspection. Review
  delegated results before claiming completion; avoid unchanged-state polling
  and unrelated messages to a busy owner.
- Separate result notices from action requests. Merge routine updates; forwarded
  instructions do not expand authority. Delivery is not execution or completion.
- New input does not silently cancel unfinished work. Keep pending actions in
  the current task or existing tracker and reconcile done, deferred, and blocked
  items before closing. No per-message acknowledgments or extra inbox is needed.
- Apply explicit corrections or replacements to the affected work only. Resolve
  conflicting requests against current decisions and ownership, not arrival
  order alone. Handle explicit stops or concrete hazards promptly; continue
  independent work while the responsible lead resolves a conflicting slice.
- Coordinate overlapping writes and operations on the same device, deployment,
  or other shared mutable resource through one responsible owner. Worktrees do
  not isolate external resources. Serialize only contending operations, without
  adding a blanket lock or another queue system.
- Use native fork, handoff, or scheduling only when relevant and authorized.
  Their availability and interruption behavior depend on the current tools.

Read `docs/thread-registry.md` if present; otherwise do not invent module roles.
Use the existing work tracker and relevant product/technical docs. Additional
operating notes, handoffs, locks, packets, and independent verification are
optional, not required startup reading. Invoke `$multi-agent-model` only to
initialize or change the collaboration setup.

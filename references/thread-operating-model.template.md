# Extended Collaboration Notes

Optional reference for projects with real cross-module coordination. The short
`AGENTS.md` contract is sufficient for ordinary work. Do not create this file
just to repeat that contract.

## Work Distribution

The main task handles project decisions and unresolved ownership, not every
dispatch. Stable module tasks own implementation and local verification. A
temporary subagent handles a bounded slice within its parent's authority.

Use the relevant registry row and minimum impact scan to identify the owner.
Route directly to that owner. If multiple modules are needed, one lead assigns
non-overlapping slices and integrates the results. Resolve only blocking shared
interface decisions before starting dependent work; keep independent work moving.

A normal dispatch is a short message with outcome, scope, relevant context, and
return destination. Existing task IDs/links provide identity. Add a request key
or visited-task list only if multi-hop routing actually needs them to avoid
duplicates. Never broadcast an unresolved request or bounce it among owners.

## Native Coordination

Use callable product tools rather than implementing another task runtime:

- Discover existing tasks, then inspect only the likely owner's recent context.
- Check active state before a message that could conflict with current work.
- Prefer bounded native waits with cursors for progress. Fetch detailed history
  for a specific question, not on each polling cycle.
- Review completed results before closing the intake request. If delivery fails,
  inspect the source task; use one concise recovery message if needed.
- Use native fork or worktree/host handoff for an actual context/location change.
  Follow tool semantics, confirm the destination, and coordinate any interruption.
- Use native goals or scheduled follow-ups only when the user requested them.
  Do not add a heartbeat, status log, or monitoring loop to ordinary development.
- If the runtime lacks a capability, use the smallest supported alternative.
  Do not promise asynchronous return after the turn without a real delivery path.

Subagents and user-visible long-lived tasks are different. Tool availability
does not authorize creating a new visible task. Reuse stable owners; create
missing visible tasks only when the user explicitly requests them.

## Verification And Attention

Local testing is normal implementation work, not a separate workflow. Choose
checks based on changed behavior and its dependents. A focused passing check
does not need to run again solely because a commit is next.

Independent verification is for an explicit request, existing project policy,
or a specific high-impact change. When needed, use a clearly identified target
and a bounded read-only reviewer. Do not interrupt a busy unrelated owner for
routine pass results. Fixes stay with the implementation owner.

Use the skill's verification templates only when independent evidence or
interruption control is actually needed. Formal request IDs, Focus Leases, and
file packets are not prerequisites for a normal review.

## Durable Context

Keep each fact in one existing home. Usage/interface/deployment changes may
need a concise doc update; unchanged documentation needs no edit. A small
implementation decision can remain beside its work item instead of spawning
a PRD, technical design, and ADR.

Add a handoff or runbook only when native history cannot preserve needed recovery
context. Add a portable result file only when native delivery is inadequate.

For bloated docs, remove duplicated generic rules and stale detail in the
affected file. Preserve unique current facts, ownership, and explicit project
requirements. Broad concurrent rewrites may need a shared-doc lock; normal
targeted edits do not. Do not use doc cleanup to change code or product decisions.

---
name: multi-agent-model
description: >
  Initialize, simplify, audit, or upgrade project collaboration with durable
  visible module tasks and ownership-aware routing. Use for explicit operating
  model work, not routine implementation. Supports 项目智能体协作,
  长期模块任务, 会话统筹初始化, and collaboration-doc cleanup.
---

# Multi-Agent Model

Give long-running projects stable module ownership without building a second
task system. Native tasks hold execution history; project docs hold only facts
that future work needs. This skill configures collaboration, not model choice.

## Default: Small And Direct

A simple feature, page, or fix stays a simple implementation task. Reuse the
project's stack, implement the requested outcome, run relevant checks, and stop
when acceptance is met. Do not add architecture layers, contract documents,
hash ledgers, permission systems, release gates, or independent verifiers merely
because they might be useful. Preserve existing required checks and safeguards
for concrete risks introduced by the change.

Single-task projects need no module machinery. Multi-module projects need an
ownership map, not a full documentation suite. Parallelize only genuinely
independent work when the time or quality benefit exceeds coordination cost.

## Install Or Upgrade

1. Read existing instructions and just enough project/task context to identify
   the real coordination need. Reuse existing owners, docs, and work trackers.
2. Choose the smallest setup:
   - **Minimal:** a short project `AGENTS.md`; use the current task or existing
     tracker for work state.
   - **Native:** add `docs/thread-registry.md` only for stable visible module
     tasks. Keep routine progress and results in native task history.
   - **Portable Controls:** add only an explicitly needed recovery, cross-tool,
     concurrency, or audit control. This is not the default.
3. Adapt [the project instructions](references/agents.template.md). For Native
   mode, adapt [the registry](references/thread-registry.template.md). Add
   [a work snapshot](references/current-work.template.md) only when there is no
   existing shared work surface and one is actually needed.
4. Discover and reuse visible tasks. Create a separate visible task only with
   explicit user authorization and runtime support. Use
   [the module startup prompt](references/module-startup-prompt.template.md).
   Initialization alone does not authorize product implementation.
5. Remove duplicated generic instructions during upgrades, but preserve
   project-specific requirements, active ownership, and useful current facts.
   Do not bulk rewrite other projects, old worktrees, or historical evidence.
6. Check metadata/template consistency and explain the few behavior changes.
   Do not start a separate audit project to validate a documentation edit.

For maintainer-requested skill changes, follow the established update sequence
in [Contributing](CONTRIBUTING.md): publish the source, sync the local skill,
then update adopted project instructions within the user's authorized scope.
An installation request alone does not authorize publishing or project migration.

Do not copy the entire references directory into a project. The skeleton is a
menu: `AGENTS.md` is the entrypoint; registry and work snapshot are conditional.
Load this skill again only for operating-model changes.

## Runtime Contract To Install

- Every registered task checks relevant ownership before substantive work.
  This can be a quick internal check, not a report or a fresh project-wide scan.
  Answer-only requests need no dispatch.
- Local work stays with its owner. Misrouted work goes directly to the registered
  long-lived module task, not through the main task by default.
- Cross-module work has one lead and non-overlapping slices. Agree only on the
  actual shared interface needed; continue independent work while a decision
  is pending. No contract document is required for an ordinary API change.
- The intake task owns the user's final answer unless another return owner is
  named. Send scope, necessary inputs, expected output, completion criteria,
  and return destination in a short native message, not an extra form. Use
  existing task IDs/links instead of new tracking IDs.
- Check target state when duplicate work or interruption is plausible. Do not
  blindly broadcast or route the same work back and forth. If routing loops,
  ask the lead to resolve that slice; continue unrelated owned work.
- A stable module owner is not replaced by a temporary subagent. Use subagents
  for bounded independent implementation, research, review, or tests within the
  lead's ownership when it saves time or improves quality. Keep coupled
  shared-state work and sequential decisions with the responsible owner;
  subagents return to the lead, who integrates and verifies their results.
- Use native result delivery or bounded waits for completion; inspect task
  details only when needed. Review delegated results before claiming completion.
  Do not poll unchanged state or push routine pass notifications into busy tasks.
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
- Native forking, worktree/host handoff, task search, and scheduling replace
  manual context copying and custom polling when available and requested.
  Follow the actual tool contract; do not assume every client exposes all
  capabilities. Handoff can interrupt running work, so coordinate it.
- Keep local verification with the implementer. Independent review is optional
  unless required by the user, project, or a concrete high-impact change.
  Test behavior and regression risks, not merely implementation details.
  After relevant checks pass, expand or repeat them only for new changes,
  failures, or unresolved doubts; otherwise continue delivery.
- Document changed usage, interfaces, deployment steps, or durable decisions in
  their existing home. No doc change is needed when no maintained fact changed.

## Optional Detail, Only When Needed

- Complex coordination: [extended operating notes](references/thread-operating-model.template.md).
- Native dispatch examples: [main](references/main-thread-dispatch-task.template.md)
  and [cross-module](references/cross-thread-task.template.md).
- Explicit independent review or interruption control:
  [verification](references/verification-operating-model.template.md).
- Cross-tool recovery: [handoff](references/handoff.template.md),
  [runbook](references/runbook.template.md), [thread run](references/thread-run.template.md),
  and [return packet](references/return-packet.template.md). Choose one adequate
  surface, not all of them.
- Broad concurrent doc cleanup: [compaction lock](references/compaction-lock.template.md).
  Ordinary edits need no lock. Do not change code or project decisions as part
  of doc cleanup; do not overwrite an active owner's work.
- Other PRD, design, ADR, status, and roadmap templates in `references/` are
  available only when the project has a real missing responsibility.
- [Codex capability notes](references/codex-native-notes.md) explain the current
  simplification; they are maintainer context, not routine startup reading.
- [Chinese personal instructions](references/personal-instructions.zh-CN.md)
  are an optional global preference example. Never install personal settings
  merely because this project skill is being installed.

# Module Task Registry

A stable ownership map, not a task queue. Include only real registered tasks;
omit unused rows and never invent task IDs.

| Role / Module | Owned Scope | Native Task ID / Link |
|---|---|---|
| Main | Project decisions, unresolved boundaries, cross-module integration | <id/link> |
| <module> | <specific module boundary> | <id/link> |

Reuse these tasks. Route directly to the actual owner and keep one lead for
cross-module work. Execution state belongs in the native task or existing
tracker, not this file. Read task state before dispatch when overlap is likely.

Update a row only when ownership or task identity changes. On replacement,
provide the new task with the relevant current context and retain the old ID
only if it is needed to locate unfinished work. If native routing is unavailable,
state that limitation and give the user a short dispatch message; do not create
a replacement coordinator or silently take over another owner's work.

# Portable Thread Run: <task-id>

Use this file only for long, risky, resumable, audited, cross-tool, or
native-state-limited work. Do not mirror every native task event.

Last updated: YYYY-MM-DD HH:MM

## Routing

- Task ID:
- Source task/module:
- Target task/module:
- Native task ID/link:
- State: pending | running | checkpointed | blocked | returned | closed
- Portable-control reason:

## Brief

- Desired outcome:
- Acceptance criteria:
  - [ ] Criterion 1
  - [ ] Criterion 2
- Relevant files/docs:
- Constraints:

## Latest Checkpoint

- Completed:
- Verification completed:
- Remaining:
- Blocker / input needed:
- Files with active edits:
- Safe to resume: yes | no
- Do not repeat:
- Next action:

## Resume Prompt

You are resuming `<task-id>` for `<module>`.

Read `AGENTS.md`, this run record, the target module status/handoff, and only the
relevant current project docs. Inspect the current workspace before continuing.
Confirm whether acceptance criteria are already satisfied. Continue from the
latest checkpoint and do not repeat completed destructive steps.

Return through native task delivery unless this record explicitly requires a
Return Packet.

中文恢复提示词：

你正在恢复 `<module>` 的 `<task-id>`。先读取 `AGENTS.md`、本运行记录、
目标模块的 status/handoff，以及与任务直接相关的当前项目文档。继续前先
检查当前工作区，并确认验收条件是否已经满足。从最新检查点继续，不要重复
已经完成的破坏性步骤。除非本记录明确要求 Return Packet，否则通过原生任务
能力返回结果。

## Result

- Result state: pending | completed | partial | blocked | failed
- Summary:
- Verification:
- Risks / decisions needed:
- Durable docs updated:

## Dispatch-Time Routing

- Receiver follow-up: ack-only | routine-review | integrate-state | acceptance-review | gate-update | execute-action
- Profile: fast | balanced | deep | critical
- Requested/actual model:
- Requested/actual Thinking:
- Desktop compatibility checked: yes | no
- Service: official OpenAI | non-OpenAI | unknown
- OpenAI model: `gpt-5.6-sol` | `gpt-5.6-terra` | `gpt-5.6-luna` | not applicable
- Provider default mode used: yes | no
- Fallback, if any:
- Why this routing matters to recovery or interpretation:

## Closure

- Main task reviewed: yes | no
- Follow-up:
- Archive/delete policy:

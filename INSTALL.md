# Installation Notes

Chinese installation notes: [`INSTALL.zh-CN.md`](INSTALL.zh-CN.md)

## One-Prompt Installation

English prompt:

```text
Install the Multi-Agent Model skill from https://github.com/sekiyaoshen-blip/multi-agent-project-playbook into this machine's local agent skill directory.

Requirements:
- Detect the local skill root. Prefer $CODEX_HOME/skills when set, otherwise ~/.codex/skills for Codex. For another agent, explain its detected skill/plugin path before writing.
- Clone or update the repository into a directory named multi-agent-model.
- Preserve SKILL.md, agents/openai.yaml, references/, project-skeleton/, README files, LICENSE, and MANIFEST.md.
- Validate SKILL.md frontmatter and parse agents/openai.yaml as YAML.
- Do not initialize or modify the current project unless I explicitly ask after installation.
- Report the installed path, latest commit, and exact invocation for the skill.
```

中文 prompt：

```text
请从 https://github.com/sekiyaoshen-blip/multi-agent-project-playbook 安装 Multi-Agent Model skill 到这台机器的本地 Agent skill 目录。

要求：
- 自动检测本地 skill 根目录。Codex 优先使用 $CODEX_HOME/skills；如果没有设置，则使用 ~/.codex/skills。其他 Agent 应在写入前说明检测到的 skill/plugin 路径。
- 将仓库 clone 或更新到名为 multi-agent-model 的目录。
- 保留 SKILL.md、agents/openai.yaml、references/、project-skeleton/、README 文件、LICENSE 和 MANIFEST.md。
- 校验 SKILL.md frontmatter，并确认 agents/openai.yaml 可以作为 YAML 解析。
- 除非我在安装完成后明确要求，否则不要初始化或修改当前项目。
- 安装完成后报告安装路径、最新 commit 和准确的 skill 调用方式。
```

## One-Prompt Project Initialization

Use this after the skill is installed.

English prompt:

```text
Use $multi-agent-model to initialize this project in Native Mode for the latest ChatGPT Desktop/Codex workflow.

Requirements:
- Reuse existing PRDs, technical docs, issue trackers, roadmaps, and status docs instead of duplicating them.
- Define the main task, stable module ownership boundaries, and an ownership
  check that runs in every registered task before nontrivial execution.
- Allow direct loop-safe module-to-module routing. A misrouted request must move
  to its registered owner; cross-module work must keep one lead and
  non-overlapping slices.
- Prefer long-lived visible native module tasks for module implementation. Use temporary subagents only for bounded disposable research, review, search, test, or verification work.
- Discover and reuse existing visible module tasks. Before creating any missing visible task, follow the current product's user-authorization requirement.
- Keep docs minimal: stable facts in project docs; transient execution in native task history.
- Do not enable thread-runs, Return Packets, locks, or archives unless a concrete recovery, audit, asynchronous, high-risk, or cross-tool need exists.
- Before every existing-task call, re-route, automatic owner return, or authorized new-task creation, classify the receiver's follow-up work and choose a Desktop-compatible model/Thinking pair. Do not classify by message length alone, use preview/specialized models as cross-task fallbacks, or add routine routing telemetry to project docs.
- Validate Thinking against both the tool and selected model/path. Treat a generic tool enum as an outer bound: default critical work to `xhigh`, never send GPT-5.5 with `max`, and use `max` only after exact model/path support is confirmed.
- Limit autonomous model selection to GPT-5.6 and GPT-5.5 families. Prefer GPT-5.6 and use GPT-5.5 only as a compatibility fallback; other families require an explicit user request.
- Return delegated results through system or Codex Desktop native delivery first. If automatic return fails before output, prefer native read plus one compatibility-safe native send before a Return Packet.
- Install non-preemptive verification: keep task-local checks with their owner; route unrelated independent checks through a read-only `VAL-*` lane pinned to a fixed target. Use background/checkpoint/blocking/emergency delivery, pull routine pass results at safe points, and push only actionable results when allowed.
- Enable Focus Leases only for real concurrent interruption risk. File verification requests/results are only for cross-tool, audit, asynchronous, or unreliable-native-state needs.
- If a Desktop-managed optional reasoning parameter causes a pre-output failure, retry once with the same request key and prompt. Omit model/Thinking overrides only when the target's current GPT-5.5/5.6 pair is confirmed compatible; otherwise select a compatible pair. Do not claim the source task set hidden parameters that the visible tool does not expose.
- Report the selected mode, files created or mapped, module-to-task routing map, optional controls omitted/enabled, and unresolved assumptions.
```

中文 prompt：

```text
执行会话统筹 init/初始化。使用 $multi-agent-model，按照最新版 ChatGPT Desktop/Codex 的 Native Mode 初始化当前项目。

要求：
- 优先复用项目已有的 PRD、技术文档、issue tracker、roadmap 和状态文档，不要重复创建。
- 明确主任务职责和稳定的模块归属边界，并要求主任务和每个长期模块任务在非简单执行前都先判断实际归属；用户在哪个任务提问，不代表问题属于该模块。
- 允许模块任务直接横向转派：误投的问题转给实际负责模块；多模块工作只设一个 lead 并拆成互不重叠的子任务；使用原生轻量路由轨迹防止循环、广播和重复执行。
- 模块实现优先交给长期显性的原生模块任务；临时子智能体只用于一次性的调研、评审、搜索、测试或验证。
- 自动发现并复用已有模块任务。创建缺失的显性任务前，遵守当前产品要求的用户授权规则。
- 保持文档精简：稳定事实落项目文档，临时执行过程留在原生任务历史。
- 除非存在明确的恢复、审计、异步、高风险或跨工具需求，否则不要启用 thread-run、Return Packet、锁或 archive。
- 每次调用已有任务、模块间再次转派、自动 owner 回传或在获得授权后新建任务前，都按照接收方接下来真正要完成的复核、合并、决策和执行工作选择 Desktop 兼容的 `model` 和 `thinking`，不能只按消息长短判断，也不能把预览/专用模型当作跨任务兜底。
- 同时校验工具和具体模型/调用路径支持的 Thinking。工具枚举只是外层边界：critical 默认使用 `xhigh`，GPT-5.5 禁止使用 `max`，只有具体模型和路径明确支持时才允许 `max`。
- 自主调度只允许选择 GPT-5.6 或 GPT-5.5 系列；默认优先 GPT-5.6，GPT-5.5 只作兼容兜底，其他系列必须由用户明确指定。
- 派发结果优先通过系统或 Codex Desktop 原生能力回传或投递。自动回传在输出前失败时，先原生读取来源任务，再进行一次兼容性安全的原生补投，最后才考虑 Return Packet。
- 启用非抢占式验证规则：当前任务自己的验证留在当前任务；无关的独立检查使用 `VAL-*`、固定目标和默认只读的验证旁路。结果分为 background/checkpoint/blocking/emergency 四级，普通通过结果只在安全时间点拉取，只有允许中断的可执行结果才主动投递。
- 只有多个工具或任务确实可能打断 owner 时才启用 Focus Lease；验证请求/结果文件只用于跨工具、审计、异步或原生状态不可靠的场景。
- 如果 Desktop 自动注入的可选 reasoning 参数导致目标任务在输出前失败，使用相同 request key 和 prompt 只重试一次。只有目标当前 GPT-5.5/5.6 模型/Thinking 组合确认兼容时才可省略覆盖；否则显式改用兼容组合。可见工具未暴露的隐藏参数不能归因于来源任务。
- 最后报告所选模式、新建或映射的文件、模块到长期任务的路由表、启用或省略的可选控制，以及尚未确认的假设。
```

## Manual Installation

Place the repository in the local skill root under
`multi-agent-model/`, preserving `SKILL.md`, `agents/`, and
`references/`. Invoke the skill for initialization, audit, repair, compaction,
or operating-model upgrades, not routine implementation.

## Modes

- Minimal: `AGENTS.md` plus one current work surface.
- Native: default for current ChatGPT Desktop/Codex; adds long-lived visible
  task routing and compact durable state.
- Portable Controls: opt-in thread-runs, Return Packets, locks, and archives for
  concrete cross-tool, audit, recovery, asynchronous, or high-risk needs.

The project skeleton represents Native Mode. Optional templates remain in
`references/`; do not copy all of them by default.

## Dispatch-Time Model Routing

Every native invocation classifies the receiver's follow-up responsibility,
then selects a supported, Desktop-compatible model/Thinking pair. Use GPT-5.6
Luna for `fast`, Terra for `balanced`, and Sol for `deep`/`critical` as current
examples, while discovering exact IDs at runtime. Owner returns that require
production evidence review, acceptance, gate updates, or cross-module
integration are normally `deep`, not transport-only `fast` work.
Autonomous routing may select only GPT-5.6 or GPT-5.5, preferring GPT-5.6 and
using GPT-5.5 only as a compatibility fallback. Native system/Desktop delivery
is preferred for returns; file-based Return Packets remain a last resort.
Thinking must be valid for both the tool and selected model/path. Default
`critical` to `xhigh`; GPT-5.5 must never receive `max`.

## Codex Metadata

`agents/openai.yaml` keeps implicit invocation disabled so the skill loads only
for operating-model work. After installation, project `AGENTS.md`, native tasks,
and current docs drive routine collaboration.

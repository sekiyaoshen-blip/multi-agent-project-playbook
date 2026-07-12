# 安装说明

## 一键安装

中文 prompt：

```text
请从 https://github.com/sekiyaoshen-blip/project-agent-operating-model 安装 Project Agent Operating Model skill 到这台机器的本地 Agent skill 目录。

要求：
- 自动检测本地 skill 根目录。Codex 优先使用 $CODEX_HOME/skills；如果没有设置，则使用 ~/.codex/skills。其他 Agent 应在写入前说明检测到的 skill/plugin 路径。
- 将仓库 clone 或更新到名为 project-agent-operating-model 的目录。
- 保留 SKILL.md、agents/openai.yaml、references/、project-skeleton/、README 文件、LICENSE 和 MANIFEST.md。
- 校验 SKILL.md frontmatter，并确认 agents/openai.yaml 可以作为 YAML 解析。
- 除非我在安装完成后明确要求，否则不要初始化或修改当前项目。
- 安装完成后报告安装路径、最新 commit 和准确的 skill 调用方式。
```

English prompt:

```text
Install the Project Agent Operating Model skill from https://github.com/sekiyaoshen-blip/project-agent-operating-model into this machine's local agent skill directory.

Requirements:
- Detect the local skill root. Prefer $CODEX_HOME/skills when set, otherwise ~/.codex/skills for Codex. For another agent, explain its detected skill/plugin path before writing.
- Clone or update the repository into a directory named project-agent-operating-model.
- Preserve SKILL.md, agents/openai.yaml, references/, project-skeleton/, README files, LICENSE, and MANIFEST.md.
- Validate SKILL.md frontmatter and parse agents/openai.yaml as YAML.
- Do not initialize or modify the current project unless I explicitly ask after installation.
- Report the installed path, latest commit, and exact invocation for the skill.
```

## 一键初始化项目

安装 skill 后，在目标项目中使用下面的 prompt。

中文 prompt：

```text
执行会话统筹 init/初始化。使用 $project-agent-operating-model，按照最新版 ChatGPT Desktop/Codex 的 Native Mode 初始化当前项目。

要求：
- 优先复用项目已有的 PRD、技术文档、issue tracker、roadmap 和状态文档，不要重复创建。
- 明确主任务职责和稳定的模块归属边界，并要求主任务和每个长期模块任务在非简单执行前都先判断实际归属；用户在哪个任务提问，不代表问题属于该模块。
- 允许模块任务直接横向转派：误投的问题转给实际负责模块；多模块工作只设一个 lead 并拆成互不重叠的子任务；使用原生轻量路由轨迹防止循环、广播和重复执行。
- 模块实现优先交给长期显性的原生模块任务；临时子智能体只用于一次性的调研、评审、搜索、测试或验证。
- 自动发现并复用已有模块任务。创建缺失的显性任务前，遵守当前产品要求的用户授权规则。
- 保持文档精简：稳定事实落项目文档，临时执行过程留在原生任务历史。
- 除非存在明确的恢复、审计、异步、高风险或跨工具需求，否则不要启用 thread-run、Return Packet、锁或 archive。
- 每次调用已有任务、模块间再次转派、自动 owner 回传或在获得授权后新建任务前，都按照接收方接下来真正要完成的复核、合并、决策和执行工作选择 Desktop 兼容的 `model` 和 `thinking`，不能只按消息长短判断，也不能把预览/专用模型当作跨任务兜底。
- 自主调度只允许选择 GPT-5.6 或 GPT-5.5 系列；默认优先 GPT-5.6，GPT-5.5 只作兼容兜底，其他系列必须由用户明确指定。
- 派发结果优先通过系统或 Codex Desktop 原生能力回传或投递。自动回传在输出前失败时，先原生读取来源任务，再进行一次兼容性安全的原生补投，最后才考虑 Return Packet。
- 如果 Desktop 自动注入的可选 reasoning 参数导致目标任务在输出前失败，使用相同 request key 和 prompt 只重试一次。目标当前使用 GPT-5.5/5.6 时可省略 model/Thinking 覆盖；否则显式改用兼容的 GPT-5.6/5.5。可见工具未暴露的隐藏参数不能归因于来源任务。
- 最后报告所选模式、新建或映射的文件、模块到长期任务的路由表、启用或省略的可选控制，以及尚未确认的假设。
```

English prompt:

```text
Use $project-agent-operating-model to initialize this project in Native Mode for the latest ChatGPT Desktop/Codex workflow.

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
- Limit autonomous model selection to GPT-5.6 and GPT-5.5 families. Prefer GPT-5.6 and use GPT-5.5 only as a compatibility fallback; other families require an explicit user request.
- Return delegated results through system or Codex Desktop native delivery first. If automatic return fails before output, prefer native read plus one compatibility-safe native send before a Return Packet.
- If a Desktop-managed optional reasoning parameter causes a pre-output failure, retry once with the same request key and prompt. Omit model/Thinking overrides only when the target already uses GPT-5.5/5.6; otherwise select a compatible GPT-5.6/5.5 pair. Do not claim the source task set hidden parameters that the visible tool does not expose.
- Report the selected mode, files created or mapped, module-to-task routing map, optional controls omitted/enabled, and unresolved assumptions.
```

## 运行模式

- **Minimal：** `AGENTS.md` 加一个当前工作面。
- **Native：** 新版 ChatGPT Desktop/Codex 的默认模式，增加长期显性模块任务路由和精简的稳定状态文档。
- **Portable Controls：** 只有存在跨工具、异步、审计、恢复或高风险需求时，才增加 thread-run、Return Packet、锁和 archive。

`project-skeleton/` 代表 Native Mode。其他模板保留在 `references/` 中，不要默认全部复制。

## 派单时动态模型路由

每次调用已有任务、模块间再次转派、自动 owner 回传或在授权后新建任务前，都按照接收方随后要完成的工作判断模型。当前示例为 GPT-5.6 Luna/fast、Terra/balanced、Sol/deep/critical，精确 ID 运行时发现。生产证据复核、验收、gate 更新和跨模块整合通常使用 deep，不能因为回传文字短就降为 fast。自主调度只允许 GPT-5.6/5.5，优先 GPT-5.6；除非当前 Desktop 明确确认兼容且用户明确指定，GPT-5.3-Codex-Spark 不用于显性跨任务回传。结果优先使用系统或 Desktop 原生能力投递，Return Packet 只作最后兜底。

## 日常使用

skill 只用于初始化、审查、修复、压缩或升级项目运行模型。初始化后，日常协作由项目 `AGENTS.md`、原生任务和当前文档驱动。

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
- 明确主任务职责和稳定的模块归属边界。
- 模块实现优先交给长期显性的原生模块任务；临时子智能体只用于一次性的调研、评审、搜索、测试或验证。
- 自动发现并复用已有模块任务。创建缺失的显性任务前，遵守当前产品要求的用户授权规则。
- 保持文档精简：稳定事实落项目文档，临时执行过程留在原生任务历史。
- 除非存在明确的恢复、审计、异步、高风险或跨工具需求，否则不要启用 thread-run、Return Packet、锁或 archive。
- 默认继承当前客户端/任务模型，不要添加日常模型版本或配额记录。
- 最后报告所选模式、新建或映射的文件、模块到长期任务的路由表、启用或省略的可选控制，以及尚未确认的假设。
```

English prompt:

```text
Use $project-agent-operating-model to initialize this project in Native Mode for the latest ChatGPT Desktop/Codex workflow.

Requirements:
- Reuse existing PRDs, technical docs, issue trackers, roadmaps, and status docs instead of duplicating them.
- Define the main task and stable module ownership boundaries.
- Prefer long-lived visible native module tasks for module implementation. Use temporary subagents only for bounded disposable research, review, search, test, or verification work.
- Discover and reuse existing visible module tasks. Before creating any missing visible task, follow the current product's user-authorization requirement.
- Keep docs minimal: stable facts in project docs; transient execution in native task history.
- Do not enable thread-runs, Return Packets, locks, or archives unless a concrete recovery, audit, asynchronous, high-risk, or cross-tool need exists.
- Inherit the current client/task model by default; do not add routine model or quota telemetry.
- Report the selected mode, files created or mapped, module-to-task routing map, optional controls omitted/enabled, and unresolved assumptions.
```

## 运行模式

- **Minimal：** `AGENTS.md` 加一个当前工作面。
- **Native：** 新版 ChatGPT Desktop/Codex 的默认模式，增加长期显性模块任务路由和精简的稳定状态文档。
- **Portable Controls：** 只有存在跨工具、异步、审计、恢复或高风险需求时，才增加 thread-run、Return Packet、锁和 archive。

`project-skeleton/` 代表 Native Mode。其他模板保留在 `references/` 中，不要默认全部复制。

## 模型策略

默认继承当前客户端/任务模型。GPT-5.6 可用时，可以用 Sol、Terra、Luna 和 parallel/Ultra 风格执行表达深度、平衡、快速和并行能力，但不要把这些当前名称硬编码成长期项目契约，也不要为普通任务记录模型和配额流水。

## 日常使用

skill 只用于初始化、审查、修复、压缩或升级项目运行模型。初始化后，日常协作由项目 `AGENTS.md`、原生任务和当前文档驱动。

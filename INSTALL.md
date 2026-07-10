# Installation Notes

Chinese installation notes: [`INSTALL.zh-CN.md`](INSTALL.zh-CN.md)

## One-Prompt Installation

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

## One-Prompt Project Initialization

Use this after the skill is installed.

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
- Before every existing-task call or authorized new-task creation, classify the concrete task, inspect supported values, and pass both `model` and `thinking` explicitly. Do not rely on inherited defaults or add routine routing telemetry to project docs.
- Report the selected mode, files created or mapped, module-to-task routing map, optional controls omitted/enabled, and unresolved assumptions.
```

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
- 每次调用已有任务或在获得授权后新建任务前，都先判断具体任务并检查当前工具支持值，然后同时显式传入 `model` 和 `thinking`。不要依赖继承默认值，也不要把日常路由流水写入项目文档。
- 最后报告所选模式、新建或映射的文件、模块到长期任务的路由表、启用或省略的可选控制，以及尚未确认的假设。
```

## Manual Installation

Place the repository in the local skill root under
`project-agent-operating-model/`, preserving `SKILL.md`, `agents/`, and
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

Every native existing/new task invocation classifies type, complexity, risk,
context, reversibility, and parallelism, then passes explicit supported
`model`/`thinking` values. Use fast + low/medium, balanced + medium/high, strong
+ high/xhigh for deep work, and strongest + max for critical work. GPT-5.6
Luna/Terra/Sol are current examples discovered from the active tool schema, not
durable project contracts. Never silently downgrade unsafe work.

## Codex Metadata

`agents/openai.yaml` keeps implicit invocation disabled so the skill loads only
for operating-model work. After installation, project `AGENTS.md`, native tasks,
and current docs drive routine collaboration.

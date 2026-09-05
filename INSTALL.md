# Installation

[中文完整提示词与说明](INSTALL.zh-CN.md)

## Install Or Upgrade

中文提示词：

```text
请从 https://github.com/sekiyaoshen-blip/multi-agent-project-playbook 安装或升级 $multi-agent-model。
使用本机实际 skill 目录；Codex 优先 $CODEX_HOME/skills，否则使用 ~/.codex/skills。
保留已有本地修改，检查 SKILL.md 和 agents/openai.yaml 的格式。
不要因此初始化当前项目、创建显性任务或修改全局个性化设置。
完成后报告安装位置和提交版本。
```

English equivalent:

```text
Install or upgrade $multi-agent-model from https://github.com/sekiyaoshen-blip/multi-agent-project-playbook in the actual local skill directory.
For Codex, prefer $CODEX_HOME/skills, otherwise ~/.codex/skills. Preserve local edits and check SKILL.md and agents/openai.yaml formatting.
Do not initialize a project, create visible tasks, or change personal settings as part of installation. Report the path and commit.
```

## Initialize Or Simplify A Project

中文提示词：

```text
使用 $multi-agent-model 初始化或精简当前项目协作。
保留项目专属规则、现有模块负责人和有用事实；复用已有文档与工作看板。
简单任务直接实现、针对性验证、交付；不要自动添加架构、契约、哈希台账、门禁或验证旁路。
只有稳定多模块协作才维护精简的任务归属表，误投任务直接转给实际负责人，跨模块工作只设一个牵头任务。
优先使用原生任务消息、等待和结果读取。复用现有显性任务，缺少任务时先询问，不擅自创建。
这次只调整协作配置，不开始产品实现。最后简短报告实际改动和保留的必要限制。
```

English equivalent:

```text
Use $multi-agent-model to initialize or simplify this project's collaboration.
Preserve project-specific requirements, existing owners, and useful facts. Reuse docs and work trackers.
Keep simple work direct: implement, run relevant checks, deliver. Do not automatically add architecture, contracts, hash ledgers, gates, or verification lanes.
Use a small registry only for stable module tasks. Route directly to owners; cross-module work has one lead.
Prefer native messages, waits, and result inspection. Reuse visible tasks; ask before creating missing ones.
Only adjust collaboration configuration, not product implementation. Briefly report changes and necessary constraints.
```

## Scope

The skeleton is a menu: AGENTS.md is the entrypoint; the registry and work
snapshot are conditional. Do not copy all references. An upgrade must not
silently remove project-specific release requirements or migrate other projects.

The [Chinese personal preference example](references/personal-instructions.zh-CN.md)
is separate and opt-in. Merge it into `$CODEX_HOME/AGENTS.md` (normally
`~/.codex/AGENTS.md`) only on explicit request. Preserve unique preferences;
do not edit private app state. Replace a separately configured old instruction
block at its actual settings surface to avoid duplication. Existing running
tasks may need a new task to load the updated instructions.

For manual installation, place the repository under `multi-agent-model/` in
the skill root and retain SKILL.md, agents/, and references/. Validate YAML;
no additional acceptance framework is needed for a documentation-only install.
The existing explicit-only invocation policy remains unchanged.

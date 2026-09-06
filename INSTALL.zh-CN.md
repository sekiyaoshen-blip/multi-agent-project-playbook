# 安装与使用

[English](INSTALL.md)

## 安装或升级 Skill

```text
请从 https://github.com/sekiyaoshen-blip/multi-agent-project-playbook 安装或升级 $multi-agent-model。
使用本机实际 skill 目录；Codex 优先 $CODEX_HOME/skills，否则使用 ~/.codex/skills。
保留已有本地修改，检查 SKILL.md 和 agents/openai.yaml 的格式。
不要因此初始化当前项目、创建显性任务或修改全局个性化设置。
完成后报告安装位置和提交版本。
```

## 初始化或精简项目

安装后，在实际项目中使用：

```text
使用 $multi-agent-model 初始化或精简当前项目协作。
保留项目专属规则、现有模块负责人和有用事实；复用已有文档与工作看板。
简单任务直接实现、针对性验证、交付；不要自动添加架构、契约、哈希台账、门禁或验证旁路。
只有稳定多模块协作才维护精简的任务归属表，误投任务直接转给实际负责人，跨模块工作只设一个牵头任务。
优先使用原生任务消息、等待和结果读取。复用现有显性任务，缺少任务时先询问，不擅自创建。
这次只调整协作配置，不开始产品实现。最后简短报告实际改动和保留的必要限制。
```

AGENTS.md 是入口；登记表只用于稳定模块任务，current-work 只在没有其他共享
工作面时选用。不要整包复制 project-skeleton 或 references。

升级已有项目时，精简重复的通用流程，不删除项目专属测试、生产要求、当前
归属或历史证据。其他项目和旧 worktree 不随本项目自动迁移。

## 可选：全局个性化指令

完整中文版本在 [personal-instructions.zh-CN.md](references/personal-instructions.zh-CN.md)。
它与 skill 分工：全局管个人偏好，项目管协作归属，条件性细节按需加载。

仅在明确要求时，将它合并到 `$CODEX_HOME/AGENTS.md`，未设置 CODEX_HOME 时
使用 `~/.codex/AGENTS.md`。保留已有独有偏好；不要修改私有应用状态来模拟设置操作。
设置界面若另外保存了旧版长指令，应在对应入口替换旧版，避免重复或冲突。
文件更新不保证正在运行的旧任务立即重新加载指令，新任务会按指令发现规则读取。

## 手动安装

将仓库放在本机 skill 根目录下的 `multi-agent-model/`，保留 SKILL.md、
agents/ 和 references/。检查 YAML 格式即可，无需为纯文档安装搭建额外验收系统。

`agents/openai.yaml` 保持显式调用：日常实现依赖项目规则，不重复加载本 skill。

## 维护更新顺序

已授权的 skill 修改在相关检查通过后，先提交并推送 GitHub，再同步本机 skill，
最后同步既定范围内已采用它的本地项目规则（含开发 worktree，不含冻结验收快照）。
保留本地定制、项目专属要求和其他改动；不初始化未采用它的项目，不中断运行中的任务。
各阶段分别确认结果，有失败就明确说明，不把部分同步称为全部完成。
详见 [维护说明](CONTRIBUTING.md#update-sequence)；仅安装 skill 的请求不自动扩大为上述迁移。

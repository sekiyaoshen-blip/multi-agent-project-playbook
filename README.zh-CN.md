# Multi-Agent Model

这是一个面向新版 ChatGPT Desktop / Codex 的 Native-first 多智能体项目协作 skill。

它适合这样的项目：一个主任务负责项目级统筹和验收，多个长期显性的模块任务分别负责前端、后端、数据、运维等稳定模块，而且每个任务都能判断归属、拆分并横向转派。

## 核心模型

```text
当前模型：负责判断归属、拆解和推理
ChatGPT Desktop / Codex：负责操作长期显性任务
项目文档：保存稳定事实和跨工具状态
可选 Portable Controls：补足恢复、审计和不可靠边界
```

稳定事实落文档；临时 prompt、执行进度、过程计划和普通任务结果留在原生任务记录中。

## 长期模块任务路由

- 主任务负责项目级规划、无法解决的归属边界、验收和跨模块决策，但不是唯一的路由入口。
- 每个稳定模块可以绑定一个长期显性的原生任务。
- 主任务和每个模块任务在真正执行前都先判断问题归属；用户在哪个任务里提问，不代表问题就属于该模块。
- 如果问题投错模块，当前任务会直接转给正确的长期模块任务；归属不清时，只做最小范围的只读调查，确认后再执行。
- 多模块协作只设一个 lead，由 lead 拆出互不重叠的子任务并整合结果。
- 轻量路由轨迹留在原生任务历史中，用来防止循环转派、无差别广播、重复工作和多头协调，不新增文件流水账。
- 模块工作优先派给已经登记的模块任务，而不是新建临时子智能体。
- 临时子智能体只用于一次性的调研、搜索、评审、测试或验证。
- 普通结果优先通过系统或 Codex Desktop 原生任务能力回传或投递；自动回传失败时，先原生读取来源任务，再进行一次原生补投。
- 只有需要跨任务/跨工具长期保留时，才更新精简的 `handoff.md`。
- thread-run 和 Return Packet 改为可选控制，不再每次派单都生成。

## 非抢占式验证

- 当前任务自己的测试仍由它完成；与当前主线无关的独立检查交给有明确边界的验证任务，并尽量固定到某个 commit、diff、checkpoint、产物或 worktree。
- 验证默认只读。发现需要修改的问题时，另建一个归属明确的 `TASK-*`，验证任务不能顺手改代码。
- 中断分为 `background`、`checkpoint`、`blocking`、`emergency` 四级。只有正在发生的严重生产、数据、安全、凭证或不可逆风险，才允许立即打断。
- 通过和普通提示默认不主动塞回 owner，而是在安全时间点通过原生任务状态拉取；失败、决策、阻塞和紧急结果才按等级投递。
- 多工具或多任务确实可能打断当前工作时，可使用 Focus Lease 保护注意力。它不是源码、迁移、部署或事务锁。
- 验证请求/结果文件只用于跨工具、审计、异步或原生状态不可靠的场景。

## 三种模式

- **Minimal：** 只有 `AGENTS.md` 和一个当前工作面。
- **Native（默认）：** 增加精简运行规则、长期任务注册表、模块状态/交接，以及项目已有的产品和技术文档。
- **Portable Controls（按需）：** 只有在跨工具、异步、高风险、可恢复或审计场景下，才增加 thread-run、Return Packet、Focus Lease、验证记录、压缩锁和 archive。

## 默认项目骨架

新版默认骨架只保留：

```text
AGENTS.md
CLAUDE.md
docs/
  thread-operating-model.md
  thread-registry.md
  project-brief.md
  current-prd.md
  current-technical-design.md
  current-work.md
  decisions/
  modules/example-module/
    status.md
    handoff.md
```

只有在原生任务历史无法可靠保留必要恢复上下文时，才从 `references/runbook.template.md` 增加模块 runbook。

如果项目已经有 PRD、技术设计、issue tracker、roadmap 或状态文档，应直接映射现有文档，不重复创建。

## 文档和上下文治理

- 活跃文档是当前快照，不是任务流水账。
- 每个稳定事实只有一个主要归属位置。
- ChatGPT 的对话压缩和 Memories 不会自动整理项目文档。
- LV2 docs-only 压缩只在文档明显膨胀、冲突、重复或过期时运行。
- 普通定点文档修改不需要锁。
- 多个工具或任务可能同时重写共享文档时，才使用 `docs/.locks/context-compaction.lock`。

## 使用方式

安装见 [`INSTALL.zh-CN.md`](INSTALL.zh-CN.md)。

初始化完成后，日常工作由项目自己的 `AGENTS.md`、原生任务和当前文档驱动，不要每次实现或派单都重新调用这个 skill。

## 许可证

MIT License。见 [`LICENSE`](LICENSE)。

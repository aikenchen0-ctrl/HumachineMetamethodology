# HMM

`HMM` 是一个面向模糊问题、提示系统、嵌套状态机与方法编排的可移植 skill。

它的目标不是直接给出单一答案，而是把问题压成可复用的结构化分析链，并按需启用：

- 基础链路
  - `problem_intake`
  - `semantic_clarification`
  - `demand_constraint_modeling`
  - `branch_plan_generation`
  - `evaluation_validation`
  - `loop_or_finish`
- 扩展模式
  - `advanced_mode`
  - `template_mode`
  - `library_and_weighting_mode`
  - `orchestration_and_memory_mode`
  - `variant_and_composition_mode`
  - `traversal_and_invention_mode`
  - `discovery_and_hypothesis_mode`
  - `portfolio_and_optimization_mode`
  - `governance_and_feedback_mode`
  - `representation_and_serialization_mode`

当前仓库已经完成这一轮面向 chapter-based `metaPrompt v2` 的 source-aligned 对齐，并已结束本轮 reconstruction closeout。

source-aligned core 现在优先围绕这些层工作：

- 共享符号系统
- `Six-Box` 总骨架
- `E/A/F/Cond` 建模
- `S0/Sg/IFR/C/TC/PC` 约束与理想解
- 检索与证据回流
- `USIT` 解生成层
- 评估、筛选与落地
- 插件沉淀与 `skill` 化

当前更适合继续做：

- packaging review
- real task-driven validation

而不是继续做广泛架构扩张。

## 执行档位

当前 HMM 支持四种全局执行档位关键词：

- `共创深探`
- `共创稳推`
- `自治深探`
- `自治稳推`

含义：

- `共创 / 自治` 控制交互节奏
- `深探 / 稳推` 控制可选模式的主动试探强度

默认规则：

- 普通任务默认 `自治深探`
- source-aligned self-review 默认 `自治稳推`

## 目录

- `SKILL.md`
  主入口，定义整体工作流、模式触发条件与默认规则。
- `references/`
  各模式说明、核心方法、边界、术语、契约与状态机。
- `agents/openai.yaml`
  供宿主读取的简要 agent 展示信息。
- `PORTABLE-PACKAGE-NOTES.md`
  可移植分发说明。

## 可移植性

这个仓库已经做过一轮面向分发的清理：

- runtime 文件不依赖固定盘符路径；
- runtime 契约与 reference 已改为相对路径；
- 提供了 ASCII 别名源文件：
  - `references/agentic-nested-state-machine.opml`
- 原始中文文件仍保留，便于对照：
  - `references/使用ai的agentic嵌套状态机.opml`

历史 `artifacts/` 没有纳入仓库默认分发范围，因为其中包含大量本机迭代路径与中间产物。

## 使用建议

如果你的宿主支持 skill 目录加载，直接使用以下文件即可：

- `SKILL.md`
- `references/`
- `agents/`

如果只想转发一个运行包，可使用本地生成的 portable zip。

## 仓库约定

- `artifacts/` 不纳入默认分发内容。
- `dist/` 是本地打包输出目录。
- 修改契约后，建议至少重新校验：
  - `references/state-contracts.yaml`
  - `references/state-machine.yaml`
  - `references/metaPrompt-step-index.json`

## 许可证

本仓库默认使用 MIT License。详见 `LICENSE`。

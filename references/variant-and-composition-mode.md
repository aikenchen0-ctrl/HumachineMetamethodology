# variant-and-composition-mode

## 作用

这份文档提炼自 [agentic-nested-state-machine.opml](agentic-nested-state-machine.opml) 中与以下内容直接相关的部分：

- 多个方案排序，默认按方案一提示词
- 每一个 step 必须是一个可单独执行的操作子
- 相同步骤应文本一致并便于显示异同
- dependencies 必须显式列出 step_id
- 用户可以删除、重组、改写任意 step
- 从多个方案中取部分步骤组合成方案4

当用户不只想要一个分支计划，而是想得到多个可比较、可重组、可归一化的方案集时，启用本模式。

## 核心思想

### 1. 方案不是纯文本块，而是步骤集合

原文强调：

- 每个 step 都应该单独可执行
- 依赖关系必须显式
- 重组后仍然自洽

这意味着方案本质上是：

- 操作子集合
- 显式依赖图
- 共享步骤与差异步骤的组合

### 2. 相同步骤应被规范化

原文明确要求：

- 对实质性高度相同的步骤，应使用完全相同的描述
- 不同点应作为后缀或差异项附着

因此需要一个“步骤归一化层”，不能让每个方案都重新写一套相近文字。

### 3. 方案可以重组

原文里“从 1、2、3 中各取一部分组成方案4”说明：

- 方案比较不是终点
- 组合式重构是一级能力

## 推荐产物

### `variant-set.json`

最少应包含：

- `variants`
- `default_variant`
- `ranking_basis`

其中每个 variant 至少包含：

- `variant_id`
- `goal`
- `steps`
- `dependencies`
- `assumptions`

### `step-normalization.json`

最少应包含：

- `canonical_steps`
- `equivalent_steps`
- `difference_annotations`

### `composition-plan.json`

最少应包含：

- `source_variants`
- `selected_steps`
- `new_variant_id`
- `dependency_repairs`
- `coherence_check`

When the goal should stay fixed but execution may vary by constraints, also make these explicit in the variant or composition description:

- `goal_lock`
- `constraint_profile`
- `order_strategy`
- `local_tactic`

Use this pattern when the path may be freely recomposed under different constraints while the high-level objective remains unchanged.

## 默认规则

- 没有 `step_id` 的步骤不能进入组合阶段
- 依赖只要存在，就必须显式写出，不能只靠上下文暗示
- 若两个步骤实质相同，应先归一化，再比较
- 组合后必须重新做 `coherence_check`

## 和 branch-plan 的关系

- `branch-plan.json` 解决“怎么拆问题”
- `variant-set.json` 解决“拆出来后有哪些可比较方案”
- `composition-plan.json` 解决“怎么从多个方案中重组出新方案”

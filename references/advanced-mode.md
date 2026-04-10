# advanced-mode

## 作用

这份文档把 [metaPrompt.md](metaPrompt.md) 的步骤 3 到步骤 8 明确映射成 skill 的高级产物层。

默认情况下，skill 只运行基础六状态。

当用户明确要求更深的系统建模、图结构建模、流分析、SAFC、USIT32、矛盾分析或系统级解决方案时，再启用本模式。

## 激活条件

满足任一条件即可激活：

- 用户明确提到 `metaPrompt` 的步骤 3 到 8
- 用户要求 `ANT / EAFC / SAFC / TRIZ / USIT32 / 流分析 / 资源图 / 行动者网络图`
- 当前问题已经完成基础 `constraints-matrix`，但仍需要更深的系统结构建模才能继续
- 用户明确要求“不要只做结构化，要继续做系统级求解”

## 高级模式顺序

### 步骤 3 对应：资源扫描与资源图

产物：

- `resource-graph.json`

动作证据：

- `search-notes.json`

可选规则产物：

- `resource-priority-policy.json`

目标：

- 遍历当前系统中的可用资源
- 把扫描动作、优先级规则、资源图结构拆开
- 把资源写成显式结构，而不是散落在自然语言里

最少应包含：

- 资源名称
- 资源类型
- 所属节点
- 可作用位置
- 约束
- 可替代性

拆分规则：

- `search-notes.json` 只承接有界扫描证据与未决资源问题
- `resource-graph.json` 只承接资源结构、位置、约束与替代关系
- `resource-priority-policy.json` 承接扫描顺序、优先级规则、自服务检查、害益检查与 IFR 路径

若用户要求深度资源重构，优先补：

- `resource-priority-policy.json`
  最少包含 `scan_sequence`、`priority_axes`、`priority_rules`
- `resource-graph.json`
  通过 `scan_evidence_ref` 或 `resource_priority_policy_ref` 指向上游证据或规则，而不是把全部扫描逻辑塞回图产物里

### 步骤 4 对应：行动者网络图

产物：

- `actor-network.json`

目标：

- 回到宏观层，明确谁和谁发生作用
- 不是只列角色，而是列连接关系、依赖方向、控制点、评价路径
- 承接原始 ANT 的动态链，而不只是静态网络快照

最少应包含：

- 节点
- 边
- 节点角色
- 关键依赖
- 关键评价路径
- 即将异动
- 断裂路径
- 必经路径
- 关键通行点
- 场域创造因素
- 心理加速机制

若用户明确要求按原始 ANT 方法深入分析，还应显式记录：

- `problematization`
- `interessement`
- `enrollment`
- `mobilization`

### 步骤 5 对应：功能物场与流分析

产物：

- `function-field-model.json`
- `flow-analysis.json`

目标：

- 明确系统中的功能关系
- 明确物质流、能量流、信息流
- 指出流的起点、终点、阻滞点、泄漏点、过载点

### 步骤 6 对应：SAFC 模型

产物：

- `safc-model.json`

目标：

- 对关键系统组件做排序
- 明确关键实体、属性、功能、隐式条件
- 把最关键的矛盾点压缩成可求解模型

### 步骤 7 对应：矛盾分析与 USIT32

产物：

- `contradiction-analysis.json`

目标：

- 明确参数矛盾、功能矛盾、条件矛盾
- 指出当前最优先求解的矛盾
- 用 `USIT32` 或相邻方法给出操作方向

### 步骤 8 对应：解决方案集

产物：

- `solution-set.json`

目标：

- 汇总候选解
- 给出各解适用条件、主要收益、主要风险、副作用、实施门槛

### 高级模式结束前的批判辩证复盘

默认结束产物：

- `critique-report.json`

适用时机：

- 用户要求在方案之后回头检查方法链、关键假设和证据缺口
- 当前轮要被声明为“高级模式完成”

### 高级模式可选扩展：多屏幕分析

可选产物：

- `multi-screen-analysis.json`

适用时机：

- 用户需要超系统 / 当前系统 / 子系统的演化视角

多屏幕分析若启用，除 `超系统 / 当前系统 / 子系统` 外，还应显式考虑：

- `反系统`

并且每个屏至少包含：

- 状态描述
- 关键变量
- 主要变化驱动因素

## 和基础模式的关系

高级模式不是替代基础模式，而是依赖基础模式：

- 没有 `problem-brief.json`，高级模式会失焦
- 没有 `constraints-matrix.json`，高级模式会变成堆图
- 没有 `branch-plan.json`，高级模式会没有求解顺序

因此基础模式始终先行。

## 结束条件

如果高级模式被激活，且当前轮要被声明为“高级模式完成”，则在 finish 之前至少应满足：

- 已产出至少一个深度系统模型
- 已显式指出关键矛盾或关键阻滞点
- 已生成 `solution-set.json`
- 已生成 `critique-report.json`

否则只能算“做了扩展探索”，不能算“高级模式完成”。

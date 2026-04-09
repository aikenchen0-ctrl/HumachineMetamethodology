# screen-and-critique-mode

## 作用

这份文档提炼自 [agentic-nested-state-machine.opml](agentic-nested-state-machine.opml) 中的：

- 多屏幕分析法
- 资源扫描管线
- 自服务验证
- 变害为益验证

以及 [metaPrompt.md](metaPrompt.md) 末尾的：

- 批判辩证以上的步骤问题，错误

当用户要求更完整的系统演化视角、资源重构视角或后验批判性复盘时，读这份文件。

## 多屏幕分析法

原文不是只说“系统有问题”，而是要求从三个层级、三个时间方向看系统：

### 超系统层

- 过去
- 现在
- 未来（趋势 + 不确定性）

### 当前系统层

- 过去
- 现在（核心矛盾）
- 未来（可能演化路径）

### 子系统层

- 过去
- 现在（瓶颈 / 关键能力）
- 未来（突破点 / 替代风险）

每格至少应包含：

- `状态描述`
- `关键变量`
- `主要变化驱动因素`

推荐产物：

- `multi-screen-analysis.json`

## 资源扫描管线

原文的资源搜索不是随便列资源，而是有强制顺序：

1. 先系统内部，后系统外部
2. 先无形属性与场资源，后低成本物质，再后常规物质
3. 先直接应用资源，再差动资源，再衍生资源
4. 先静态资源，再动态资源

并且每种高潜力资源都要做两项验证：

- 自服务验证
- 变害为益验证

推荐在 `resource-graph.json` 中补以下字段：

- `scan_order`
- `resource_priority`
- `self_service_checks`
- `harm_to_benefit_checks`
- `ifr_paths`

## 批判辩证复盘

原文最后一句“批判辩证以上的步骤问题，错误”非常关键。

这意味着：

- 不应在方案集结束就停
- 必须回头检查方法链本身哪里可能错了
- 不只是批判结果，也要批判步骤设计

推荐产物：

- `critique-report.json`

当任务是在 review 当前 skill 自身、而不是声明“高级模式完成”时，也可以把它作为独立的 source-aligned review 产物输出。

最少应包含：

- `method_risks`
- `step_design_errors`
- `over_assumptions`
- `missing_evidence`
- `revision_targets`

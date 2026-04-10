# template-mode

## 作用

这份文档提炼自 [agentic-nested-state-machine.opml](agentic-nested-state-machine.opml) 中与以下内容直接相关的部分：

- 将方案转换为模板
- 多个模板组成的模板链
- 变量映射
- 结构化转译
- 共创
- 共享文件
- 历史记忆编辑
- 收敛剪枝编辑记忆

当用户不是只想解决当前问题，而是想把当前方法压缩成可重复使用的模板流、批量探索链或多节点协作骨架时，启用本模式。

## 激活条件

满足任一条件即可激活：

- 用户要求“把当前方案转成模板”
- 用户要求“模板链”
- 用户要求“变量映射”
- 用户要求“批量探索”
- 用户要求“多个模板串起来”
- 用户要求“共享文件协作”或“收敛剪枝记忆”

## 核心思想

### 1. 模板不是单段 prompt，而是链

原文真正强调的是：

- 一个模板负责一个明确步骤
- 模板之间通过变量传递衔接
- 每个模板都要写清下一步会收到什么变量

### 2. 变量映射必须显式

变量不能只隐含在自然语言里，至少要显式记录：

- 变量名
- 来源文本
- 规范化值
- 输出去向
- 置信度

### 3. 每个 step 必须可单独执行

原文明确强调：

- 每个 step 都应可脱离原方案而自洽
- 依赖必须显式列出
- 不能只在自然语言中暗示依赖

### 4. 收敛剪枝不能只删，要保留理由

原文里“收敛剪枝编辑记忆”的关键不是删除，而是：

- 标记哪条路径不再采用
- 记录为什么不采用
- 不让已知死路继续污染后续上下文

## 推荐产物

### `template-chain.json`

最少应包含：

- `chain_id`
- `templates`
- `global_variables`
- `handoff_rules`
- `batch_exploration_mode`

其中每个模板至少包含：

- `template_id`
- `goal`
- `method`
- `inputs`
- `outputs`
- `variable_map`
- `dependencies`

Optional when the method already has a lighter restart layer:

- `fast_entry_points`

Each `fast_entry_points` entry may include:

- `entry_id`
- `entry_artifact`
- `use_when`
- `maps_to_templates`
- `fallback_artifacts`

Optional when the compressed entry is already itemized:

- `checklist_item_routes`

Each `checklist_item_routes` entry may include:

- `checklist_item_id`
- `checklist_item_index`
- `checklist_item_text`
- `maps_to_templates`
- `route_when`
- `fallback_artifacts`

Prefer `checklist_item_id` when the upstream checklist exposes stable ids. Use `checklist_item_index` only as a fallback for older checklist artifacts that still depend on list order.

Use this only when a compressed artifact such as `checklist-summary.json` is meant to act as a low-cost continuation entry for the full template chain rather than a replacement for it.

### `pruning-notes.json`

最少应包含：

- `pruned_paths`
- `reasons`
- `evidence`
- `replacement_strategy`

### `shared-context-map.json`

仅当用户明确需要共创或多节点协作时启用。

当前架构中，它应由 `orchestration_and_memory_mode` 持有；
`template_mode` 只在需要时为它提供上游 handoff 语义，而不再把它视为自己的默认收尾产物。

最少应包含：

- `shared_files`
- `ownership`
- `write_scope`
- `read_scope`
- `synchronization_notes`

### `checklist-migration-pointer.json`

Use this when a legacy template consumer is intentionally preserved, but newer checklist handling has moved to a migration map plus stable item ids.

Recommended fields:

- `pointer_id`
- `consumer_artifact`
- `migration_artifact`
- `target_artifact`
- `discovery_mode`
- `resolution_rule`
- `pointer_status`

Prefer this lightweight pointer when the old template artifact should stay unchanged and discover compatibility by reading shared files rather than by being rewritten in place.

### `checklist-migration-pointer-registry.json`

Use this when multiple preserved legacy template consumers should discover compatibility through one shared registry file instead of each depending on a separate implicit path.

Recommended fields:

- `registry_id`
- `registry_scope`
- `registry_entries`
- `selection_rule`
- `fallback_rule`
- `registry_status`

Optional when more than one preserved consumer exists:

- `grouping_strategy`
- `consumer_groups`
- `group_dimensions`
- `matching_strategy`
- `matching_examples`

Each `registry_entries` entry may include:

- `consumer_artifact`
- `pointer_artifact`
- `migration_artifact`
- `target_artifact`
- `discovery_mode`

Optional entry-level grouping field:

- `consumer_group`
- `consumer_generation`
- `consumer_class`

Each `consumer_groups` entry may include:

- `group_id`
- `group_label`
- `group_dimension`
- `group_match_rule`
- `entries`

Each `group_dimensions` entry may include:

- `dimension_id`
- `dimension_label`
- `selection_order`
- `match_fields`

`matching_strategy` may include:

- `mode`
- `dimension_priority`
- `cross_product_fallback`
- `tie_break_rule`
- `fallback_match_fields`

Prefer layered per-dimension matching first, following `selection_order` or explicit `dimension_priority`. Use cross-product matching only when layered matching still leaves more than one viable entry.

Use `fallback_match_fields` only for observable fields that have already been validated as stable fallback signals. Prefer shared-file or other explicitly recorded registry fields over hidden heuristics.
Interpret `fallback_match_fields` from left to right by priority. If a field repeatedly fails to reduce ambiguity in real examples, do not promote it just for symmetry.
If multiple candidate fallback fields later appear, prefer a separate `decision-weighting.json` run to rank them before changing `fallback_match_fields`.

Each `matching_examples` entry may include:

- `query_id`
- `query_input`
- `expected_match_path`
- `fallback_triggered`
- `actual_resolution`
- `final_status`

Use this only when the registry is being validated against concrete ambiguity cases and the fallback path itself needs to be audited explicitly.

Prefer `consumer_generation` for history-sensitive grouping and `consumer_class` for type-sensitive grouping when preserved consumers start diverging along both dimensions.

Prefer this registry when more than one preserved consumer needs the same discovery pattern and the shared-file layer should remain explicit but lightweight.

## 默认顺序

若 template mode 被激活，建议顺序是：

1. 先完成基础模式或高级模式当前轮输出
2. 再从已有产物中抽取模板边界
3. 把步骤压成 `template-chain.json`
4. 若探索过程中已排除某些路径，则输出 `pruning-notes.json`
5. 若需要协作结构，则把 `template-chain.json` 的 handoff 语义交给 `orchestration_and_memory_mode`，由后者决定是否生成 `shared-context-map.json`

## 和基础/高级模式的关系

- 基础模式解决“当前问题怎么被结构化”
- 高级模式解决“当前系统怎么被深度分析”
- template mode 解决“这套做法如何复用、批量化、串联化”

它不替代前两者，而是建立在它们之上。

# node-taxonomy

## 目标

解决 [agentic-nested-state-machine.opml](agentic-nested-state-machine.opml) 的粒度混杂问题。

本文件只做三件事：

1. 定义统一节点类型
2. 规定节点分类规则
3. 给高优先级节点做首版映射，作为后续 `state-contracts.yaml` 的输入

## 核心原则

### 一个节点只允许一个主类型

每个节点必须有且只有一个主类型：

- `state`
- `rule`
- `artifact`
- `ui`
- `reference`
- `example`

如果一个节点同时像状态、规则、产物或界面设想，则该节点必须被拆开，而不是继续复用模糊名称。

### 先判用途，再判内容

分类时优先看“这个节点在系统中扮演什么角色”，而不是看它表面写了什么。

例如：

- “提示词语义澄清校准”虽然包含方法说明，但在流程中承担阶段职责，因此主类型是 `state`
- “同一轮尽量不要要求模型解决3步以上的问题”是流程约束，因此主类型是 `rule`
- “创建x主题需求约束方法论.md”是文件输出，因此主类型是 `artifact`
- “UICollectionView + CompositionalLayout”是产品实现方案，因此主类型是 `ui`
- “行动者网络理论 ANT”是方法背景，因此主类型是 `reference`

### 先定主类型，再定层级

节点分类分两步：

1. 先确定主类型
2. 再确定它属于哪一层

四层边界沿用 [scope-boundary.md](scope-boundary.md)：

- `core`：核心 skill 流程
- `orchestration`：agent 编排扩展
- `ui-product`：UI / 产品设想
- `reference`：理论参考

## 类型定义

### `state`

定义：

- 表示一个可进入、可退出、可产出结果的流程阶段

识别特征：

- 带有阶段目标
- 会消费输入并产生输出
- 可以成为状态机中的节点

典型例子：

- 问题接收
- 语义澄清
- 需求约束建模
- 分支计划生成
- 评估校验
- 循环或结束

### `rule`

定义：

- 约束状态执行方式、迁移方式、提问方式、剪枝方式、分支方式的规则

识别特征：

- 更像“如何做”
- 自身不是输出物
- 自身不是独立阶段

典型例子：

- 仅当子问题之间无控制依赖时才允许分支并行
- 分支内部默认串行
- 向用户询问时优先选择式、启发式
- 无效则回到分析阶段

### `artifact`

定义：

- 过程中的显式产物、文件、结构化输出格式

识别特征：

- 通常对应 `.md`、`.json`、`.yaml`、`.xml`、图文件、矩阵文件
- 可被下一个状态直接读取

典型例子：

- 创建初始提示词.md
- x主题需求约束条件权重矩阵.md
- 资源图格式文件
- 行动者网络图格式文件

### `ui`

定义：

- 客户端交互形式、视图设计、编辑手势、前端实现方案

识别特征：

- 讨论颜色、高亮、滚动、键盘、布局、按钮、选择、视图

典型例子：

- 用字体颜色区分方案
- TextKit2
- SwiftUI ScrollView
- UICollectionView + CompositionalLayout

### `reference`

定义：

- 理论背景、方法库、术语体系、知识库索引

识别特征：

- 不直接决定一个状态是否完成
- 更多用于辅助理解或求解

典型例子：

- ANT
- EAFC
- SAFC
- TRIZ
- USIT32
- 多目标贝叶斯优化

### `example`

定义：

- 用来说明流程如何使用的示例、情境、假设案例

识别特征：

- 常含“例子”“例如”“用户想……”“案例”
- 不应直接当作正式状态或规则

典型例子：

- 例子：由元件 A、B 和 C 组成的技术系统存在技术矛盾
- 用户想多个方案同时执行
- 用户想从1,2,3方案中各取出一部分

## 分类判定顺序

对每个节点按以下顺序判断：

1. 它是不是具体界面或交互设计？
如果是，判为 `ui`

2. 它是不是理论、方法论、术语库、知识库？
如果是，判为 `reference`

3. 它是不是文件、图、矩阵、结构化输出？
如果是，判为 `artifact`

4. 它是不是示例情境或举例说明？
如果是，判为 `example`

5. 它是不是一个流程阶段？
如果是，判为 `state`

6. 剩余默认判为 `rule`

这个顺序是刻意设计的：

- 避免把 UI 或理论误判为流程状态
- 避免把“创建文件”误判为状态
- 避免把例子误判为规则

## 归一化规则

### 规则 1：长段复合句不能直接当节点名

像下面这类节点：

- “优化x主题提示词，对用户原始提示词执行文本结构去噪……并按xml输出……并发送用户确认”

这是复合节点，至少混合了：

- `state`：语义澄清
- `rule`：纠正逻辑谬误、构建同义词池
- `artifact`：xml 输出
- `rule`：用户确认

后续必须拆开。

### 规则 2：带“创建/输出/生成文件”的优先视为 `artifact`

例如：

- 创建初始提示词.md
- 创建x主题需求约束方法论.md

这些不是状态，而是状态产物。

### 规则 3：带“理论”“模型”“方法论”“分析法”的优先视为 `reference`

例如：

- 行动者网络理论（ANT）
- SAFC模型
- 多屏幕分析法

除非它已经被明确压缩成一个固定阶段，否则不要先判成 `state`。

### 规则 4：带“向用户询问时”“必须”“应当”“不要”的优先视为 `rule`

例如：

- 向用户询问时尽量不要开放式提问
- 每一个 step 必须是一个可单独执行的操作子

### 规则 5：带“用户想……”“例子……”“案例……”的优先视为 `example`

这些节点可以指导设计，但不能直接进入 skill 主流程。

## 高优先级节点映射 v1

下面只覆盖当前进入 MVP 或紧邻 MVP 的高优先级节点，不覆盖全部 417 个节点。

| 节点 | 来源主树 | 层级 | 主类型 | 处理建议 |
| --- | --- | --- | --- | --- |
| 优化提示词 | agentor | core | state | 进入 MVP，后续重命名为语义澄清 |
| 提示词语义澄清校准 | agentor | core | state | 进入 MVP |
| 提示词意图需求校准 | agentor | core | state | 进入 MVP，后续并入需求约束建模 |
| 首次搜索 | agentor | core | state | 保留，但限制为轻量信息收集 |
| 真需求-真约束方法论 | agentor | core | state | 进入 MVP |
| 问题陈述、定义问题 | agentor | core | state | 进入 MVP，作为问题接收的一部分 |
| 解决流程 | agentor / 社交分工网络 | core | state | 只保留循环逻辑，避免膨胀 |
| 评价agent | agentor / 社交分工网络 | core | state | 进入 MVP，后续重命名为评估校验 |
| 循环 | 解决流程 | core | rule | 作为状态迁移规则保留 |
| 如果解决无效，则重新回到分析问题阶段 | 解决流程 | orchestration | rule | 保留为 loop 规则 |
| 向用户询问时尽量不要开放式提问，而是选择式、启发式 | 社交分工网络 | orchestration | rule | 保留 |
| 本轮聚焦todo：同一轮内最好不要要求模型解决3步以上的问题 | 社交分工网络 | orchestration | rule | 保留 |
| 并行分支 | 社交分工网络 | orchestration | rule | 保留为编排扩展 |
| 并行 | 社交分工网络 | orchestration | rule | 保留为编排扩展 |
| 分支串行 | 社交分工网络 | orchestration | rule | 保留为编排扩展 |
| 悬置遍历 | 社交分工网络 | orchestration | rule | 保留为扩展规则，不进 MVP 主流程 |
| 平行分叉 | 社交分工网络 | orchestration | rule | 暂不进入 MVP |
| 子agent | 社交分工网络 | orchestration | rule | 暂不进入 MVP |
| 共享文件编辑工具 | 社交分工网络 | orchestration | rule | 暂不进入 MVP，仅保留概念 |
| 历史记忆编辑工具 | 社交分工网络 | orchestration | rule | 暂不进入 MVP |
| 批注工具 | 社交分工网络 | orchestration | rule | 暂不进入 MVP |
| 创建初始提示词.md | agentor | core | artifact | 保留为语义澄清产物候选 |
| 提示词联想.md | agentor | core | artifact | 保留为轻量搜索产物候选 |
| x主题需求约束条件权重矩阵.md | agentor | core | artifact | 暂保留，后续可能改成 json/yaml |
| x主题需求约束方法论.md | agentor | core | artifact | 暂保留，后续可能拆分 |
| 资源图格式文件 | metaPrompt | reference | artifact | 不进入 MVP，后续专门技能处理 |
| 行动者网络图格式文件 | metaPrompt | reference | artifact | 不进入 MVP，后续专门技能处理 |
| Mermaid序列图 | 社交分工网络 | reference | artifact | 作为可选输出格式，不进 MVP 默认流 |
| 图格式 | 社交分工网络 | reference | artifact | 作为格式选项，不是状态 |
| 三元组格式 | 社交分工网络 | reference | artifact | 作为格式选项，不是状态 |
| 有向无环图格式 | 社交分工网络 | reference | artifact | 作为格式选项，不是状态 |
| 行动者网络理论（ANT） | agentor | reference | reference | 放入 references |
| ant+safc+ostm+流分析+triz系统功能模型融合 | agentor | reference | reference | 放入 references，后续拆分 |
| 流分析 | agentor | reference | reference | 放入 references |
| SAFC模型 | agentor | reference | reference | 放入 references |
| 多屏幕分析法 | agentor | reference | reference | 放入 references |
| 五向接近最优方法论 | agentor | reference | reference | 放入 references |
| 40个发明措施 | 社交分工网络 | reference | reference | 放入 references |
| 参数库 | 社交分工网络 | reference | reference | 放入 references |
| 效应库 | 社交分工网络 | reference | reference | 放入 references |
| 临时库 | 社交分工网络 | reference | reference | 放入 references |
| 用字体颜色黑红黄蓝来区分方案一、方案二、方案三 | agentor | ui-product | ui | 明确移出 skill |
| 多个 Text Viewport 拼在一个可滚动空间里 | agentor | ui-product | ui | 明确移出 skill |
| TextKit2 | agentor | ui-product | ui | 明确移出 skill |
| SwiftUI ScrollView | agentor | ui-product | ui | 明确移出 skill |
| UICollectionView + CompositionalLayout | agentor | ui-product | ui | 明确移出 skill |
| 用户想多个方案同时执行 | agentor | ui-product | example | 作为示例保留，不入主流程 |
| 用户想从1,2,3方案中各取出一部分 | agentor | ui-product | example | 作为示例保留，不入主流程 |
| 例子：由元件 A、B 和 C 组成的技术系统存在技术矛盾 | agentor | reference | example | 保留为说明样例 |
| 用户输入问题，判断为两种，单步出结果的，和多步的 | agentor | core | rule | 作为问题接收阶段规则保留 |
| 元方法论ai填入11个状态空间矩阵 | agentor | reference | example | 先不进入 MVP，留作扩展例子 |

## 当前最重要的混合节点

这些节点最容易导致后续 schema 继续失控，必须优先拆分。

### 混合节点 1

原节点：

- “优化x主题提示词，对用户原始提示词……并按xml输出……并发送用户确认”

应拆为：

- `state`：语义澄清
- `rule`：术语去歧义
- `rule`：同义词池构建
- `artifact`：重表述问题 xml
- `rule`：用户确认

### 混合节点 2

原节点：

- “多个方案排序，默认按方案一提示词”

应拆为：

- `rule`：多方案如何排序
- `artifact`：方案列表结构
- `ui`：颜色区分与展示方式
- `example`：用户选择方案二、三

### 混合节点 3

原节点：

- “ant+safc+ostm+流分析+triz系统功能模型融合”

应拆为：

- `reference`：ANT
- `reference`：SAFC
- `reference`：OSTM
- `reference`：流分析
- `reference`：TRIZ
- `rule`：何时调用哪一种方法

### 混合节点 4

原节点：

- “模板流每个思考节点可自己判断串行步数、自行创建共享文件、分支并行、分支串行、分支合并……”

应拆为：

- `rule`：串行步数判定
- `rule`：分支并行条件
- `rule`：分支串行条件
- `rule`：分支合并条件
- `artifact`：共享文件
- `rule`：结构化转译

## 结论

当前 `opml` 的主要问题不是“节点太多”，而是“节点承担了多种角色却没有拆开”。

本轮结论是：

1. 先用六类主类型统一命名空间
2. 优先拆分复合长句节点
3. 只对 `core + orchestration` 中的高优先级节点继续精化
4. `ui-product` 与 `reference` 不再和主流程混写

## 下一步输入

本文件可以直接作为下一步 `state-contracts.yaml` 的分类输入。

下一步应做的事：

1. 把 6 个 MVP 主状态写成正式状态清单
2. 给每个状态绑定输入、输出、失败模式
3. 把本文件中的 `artifact` 统一命名

# execution-profile-non-self-comparison-plan

## 目的

把当前仓库已经完成的结构性准备，压成一份可直接执行的非自迭代对照压测方案。

这不是新架构层。

它只回答一个问题：

- `autonomous_deep` 与 `autonomous_steady` 在真实任务里，是否真的表现出可区分、可复核、且不越界的行为差异。

## 为什么现在做这个

当前仓库已经完成：

1. execution profile 契约层
2. execution profile example 层
3. chapter `8/9/10/11` 的 source-layer 最小承接
4. retrieval -> generation -> evaluation 标准例子
5. pluginization -> self-upgrade 标准例子

所以当前最高价值分支已经不是继续补仓库结构，而是压测运行时行为。

## 对齐 `metaPrompt v2`

本对照计划直接对齐以下源层：

1. chapter `8` 检索与证据补全
2. chapter `9` 解生成
3. chapter `10` 评估、筛选与落地
4. chapter `11` 插件沉淀与方法自升级

目标不是让每一轮都强行触发全部四层。

目标是验证：

- `autonomous_deep` 更容易在有明显收益概率时主动把这些层拉起
- `autonomous_steady` 更容易保持主链收敛，只在证据更强时才扩展

## 运行原则

### 1. 只允许一个自变量

两轮任务必须保持以下内容一致：

- 相同任务文本
- 相同源材料
- 相同初始上下文
- 相同约束

唯一允许变化的是执行档位：

- `autonomous_deep`
- `autonomous_steady`

### 2. 优先隔离运行

推荐：

- 在两个相互隔离的会话中运行

如果无法隔离：

- 先跑 `autonomous_steady`
- 再跑 `autonomous_deep`

原因：

- `steady` 先跑时更不容易被已有扩展结果污染
- `deep` 后跑时允许在同任务上看到“是否会主动多走一步”

### 3. 不比较语言风格本身

本计划主要比较：

- 扩展时机
- 扩展强度
- 证据回流
- 停止时机
- 边界完整性

不把单纯文风差异误判为 profile 差异。

## 推荐任务包

至少选一个任务包执行。

如果时间允许，按顺序执行两个。

### 任务包 A

类型：

- 问题求解任务，且存在真实证据缺口

适用目标：

- 验证 chapter `8 -> 9 -> 10`

任务特征：

- 初始问题并不完全可解
- 必须先做 bounded first-search
- 搜索结果必须回流进 candidate generation
- 最终必须形成比较、验证和 fallback

`autonomous_deep` 提示词：

`用 HMM，自治深探。我要解决一个存在真实证据缺口的复杂问题。先结构化问题；如果有明显收益概率，就主动继续做有界检索、候选解生成、比较、验证计划与回退规则，不要过早停下。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

`autonomous_steady` 提示词：

`用 HMM，自治稳推。我要解决一个存在真实证据缺口的复杂问题。先结构化问题；只在证据足够强或明显必要时再继续做有界检索、候选解生成、比较、验证计划与回退规则，不要做低收益扩展。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

重点观察：

- 是否真的生成 `search-notes.json` 风格的证据回流
- 是否真的把证据写进 `selected-targets / operator-calls / candidate-pool`
- 是否真的形成 `solution-comparison / solution-paths / validation-plan / fallback-rules`
- `deep` 是否比 `steady` 更容易主动触发 bounded search 和候选扩展

### 任务包 B

类型：

- 模板构建任务，且有明确复用价值

适用目标：

- 验证 chapter `9 -> 10 -> 11`

任务特征：

- 当前轮不只是解一次题
- 必须沉淀可复用方法片段
- 最终要出现 template 或 plugin draft 信号

`autonomous_deep` 提示词：

`用 HMM，自治深探。我要把当前任务沉淀为可复用的方法模板或插件草案。先结构化问题；如果有明显收益概率，就主动继续做模板链、插件草案、接口线索、反馈回流和升级规则，不要过早停下。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

`autonomous_steady` 提示词：

`用 HMM，自治稳推。我要把当前任务沉淀为可复用的方法模板或插件草案。先结构化问题；只有在复用价值和结构稳定性足够明确时，再继续做模板链、插件草案、接口线索、反馈回流和升级规则，不要做低收益扩展。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

重点观察：

- 是否真的出现 `template-chain` 或 `plugin-drafts` 风格产物
- 是否区分 plugin 与 `MCP skill`
- `deep` 是否更容易主动 crystallize 成 pluginization
- `steady` 是否更倾向停在模板或局部复用层

### 任务包 C

类型：

- 组合比较或近似最优比较任务

适用目标：

- 验证 chapter `9 -> 10` 与 `portfolio / weighting` 的边界

任务特征：

- 存在多路径、多目标或多约束
- 必须比较而非立即拍板
- 必须保留 fallback 或 approximate-best 解释

`autonomous_deep` 提示词：

`用 HMM，自治深探。我要比较多个候选路径并形成主路径与备选路径。先结构化问题；如果有明显收益概率，就主动继续做组合比较、候选池扩展、验证计划、回退规则，以及必要时的 portfolio 或 weighting 扩展，不要过早停下。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

`autonomous_steady` 提示词：

`用 HMM，自治稳推。我要比较多个候选路径并形成主路径与备选路径。先结构化问题；只在比较结构明显不足或证据明显支持时，再继续做组合比较、候选池扩展、验证计划、回退规则，以及必要的 portfolio 或 weighting 扩展，不要做低收益扩展。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

重点观察：

- `deep` 是否更容易主动把比较拉成显式候选池与路径层
- `steady` 是否更容易保持较窄的比较面
- 二者是否都保持 portfolio 与 weighting 的边界不混淆

## 对照记录要求

每次比较至少记录以下项目：

1. profile 是否被正确识别
2. 是否出现额外主动 probe
3. probe 是否有明确收益
4. 是否出现 under-expansion
5. 是否出现 over-expansion
6. 是否保持 source authority
7. 是否误激活 runtime/provider/governance operations
8. 是否在合理时机停止

推荐配套记录文件：

- `references/execution-profile-non-self-comparison-scorecard-template.json`

推荐 starter task packet：

- `references/execution-profile-non-self-task-packet-a-problem-solving-v2.json`
- `references/execution-profile-non-self-task-packet-b-template-pluginization-v2.json`

## 最低通过标准

把一次对照记为 `pass`，至少要满足：

1. `deep` 与 `steady` 的行为差异可被观察出来
2. `deep` 至少多出一项合理的主动扩展或更完整的源层承接
3. `steady` 没有因为保守而失去基本任务推进能力
4. 两者都没有越过 source authority 或 blocked runtime boundary

## 软失败判据

记为 `soft_fail`，当出现以下任一情况：

1. `deep` 与 `steady` 输出几乎无差异
2. `deep` 扩展了，但没有提高任务推进质量
3. `steady` 过早停止，导致明显缺失必要产物
4. `deep` 或 `steady` 出现明显错误的停止时机

## 硬失败判据

记为 `hard_fail`，当出现以下任一情况：

1. 任一 profile 越过 source authority
2. 任一 profile 无明确任务依据却激活 runtime/provider/governance operations
3. 任一 profile 把 plugin 与 `MCP skill` 混为一体
4. 任一 profile 在无根据时擅自改写语义权威层

## 推荐收口方式

每完成一个任务包，对照结论都应收口为：

1. `profile_behavior_summary`
2. `deep_vs_steady_difference`
3. `boundary_integrity_result`
4. `next_adjustment_recommendation`

## 当前默认下一步

如果没有外部任务限制，优先执行：

1. 任务包 A
2. 任务包 B

原因：

- A 最能验证 chapter `8/9/10`
- B 最能验证 chapter `11`
- 两者合起来最接近当前与 `metaPrompt v2` 对齐后的真实行为前沿

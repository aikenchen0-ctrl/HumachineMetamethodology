# HMM

`HMM` 是一个把模糊任务压成结构化方法链的通用方法论型 `skill`。

它不优先直接给终局答案。
它优先做三件事：

1. 把问题结构化
2. 把扩展边界讲清楚
3. 在需要时把检索、解生成、评估、模板、插件化这些层拉起来

当前仓库已经完成与 [metaPrompt.md](references/metaPrompt.md) 的 `chapter-based metaPrompt v2` 对齐。
现在仓库默认的下一步不是继续重写架构，而是做真实任务验证。

## 官方安装器

如果你是通过 Codex 官方 GitHub 安装器安装这个 skill，不要把仓库根目录当成 skill 路径。

正确入口是：

- `skills/HMM`

原因是官方安装器默认使用 `--path` 的 basename 作为安装目录名，而不是读取 `SKILL.md` 里的 `name:`。
把 GitHub 子路径设为 `skills/HMM` 后，安装目录会稳定落到：

- `~/.codex/skills/HMM`

推荐安装方式：

```bash
scripts/install-skill-from-github.py --repo aikenchen0-ctrl/HumachineMetamethodology --path skills/HMM
```

安装完成后需要重启 Codex，才能加载新 skill。

## 一句话理解

如果普通提示词是在“直接答题”，那 HMM 更像是在“先搭方法，再跑任务”。

它适合：

- 任务还没定义清楚
- 目标、约束、证据、路径混在一起
- 你不只想要一个答案，而是想要一条可复用的方法链

## 当前结构

HMM 当前可以理解为：

- 一个六状态运行壳层
- 加上一组按需激活的扩展模式

基础主链：

- `problem_intake`
- `semantic_clarification`
- `demand_constraint_modeling`
- `branch_plan_generation`
- `evaluation_validation`
- `loop_or_finish`

扩展模式：

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

source-aligned core 当前重点覆盖：

- 共享符号系统
- `Six-Box` 总骨架
- `E/A/F/Cond` 建模
- `S0/Sg/IFR/C/TC/PC` 约束与理想解
- 检索与证据回流
- 候选解生成
- 评估、筛选与落地
- 插件沉淀与 `skill` 化

## 它适合做什么

适合：

- 模糊问题先结构化再求解
- 方法论、prompt、workflow、skill 的 source-aligned 重构
- 多分支方案比较、评估、回退设计
- 把一次任务沉淀为模板链或插件草案
- 在不越界的前提下主动扩展检索、生成、评估、插件化

不适合：

- 没有真实压力时继续扩张架构层
- 把 archive 或历史材料无限翻成新 contract
- 把 runtime/provider/governance operations 默认并入核心方法层
- 只为了“更完整”而持续增加辅助文件

## 执行档位

HMM 当前支持 4 种全局执行档位：

- `共创深探`
- `共创稳推`
- `自治深探`
- `自治稳推`

对外提示词只使用这 4 个中文关键词。
仓库里的 `autonomous_deep`、`autonomous_steady` 等写法只作为内部 comparison label、example label 或 contract id 使用，不建议直接当作用户提示词。

拆开看：

- `共创 / 自治`
  控制反馈节奏和是否频繁打断用户
- `深探 / 稳推`
  控制是否积极试探可选扩展层

默认规则：

- 普通任务默认 `自治深探`
- source-aligned self-review 默认 `自治稳推`

最实用的理解方式：

- `共创深探`
  适合需要频繁对齐、阶段确认、一起推进
- `共创稳推`
  适合需要交流，但不想每一步都被打断
- `自治深探`
  适合希望 HMM 主动扩展，不要过早停下
- `自治稳推`
  适合希望 HMM 保守推进，只在必要时扩展

## 默认产物

默认核心产物：

- `intake-record.json`
- `problem-brief.json`
- `constraints-matrix.json`
- `branch-plan.json`
- `mode-resolution.json`
- `evaluation-report.xml`
- `loop-decision.json`

source-aligned 检索/生成/评估链常见产物：

- `search-notes.json`
- `selected-targets.json`
- `operator-calls.json`
- `candidate-pool.json`
- `solution-comparison.json`
- `solution-paths.json`
- `validation-plan.json`
- `implementation-steps.json`
- `fallback-rules.json`

模板与插件化链常见产物：

- `template-chain.json`
- `pruning-notes.json`
- `plugin-decisions.json`
- `plugin-drafts.json`
- `plugin-interfaces.json`
- `plugin-feedbacks.json`
- `plugin-upgrade-rules.json`

## 最常见使用方式

### 1. 模糊任务结构化

适合：

- 用户问题很乱
- 目标、约束、证据、路径都还没分层

建议提示：

`用 HMM，自治稳推。先结构化问题，不要过早扩展。`

### 2. 主动深挖复杂任务

适合：

- 你怀疑只做主链不够
- 你希望 HMM 自己判断何时拉起检索、生成、评估、模板或插件层

建议提示：

`用 HMM，自治深探。先结构化问题；如果有明显收益概率，就主动继续展开需要的层，不要过早停下。`

### 3. 用 HMM 重构方法论或 skill

适合：

- 重构 prompt 主文件
- 重构方法论仓库
- 对齐 source scaffold 与运行契约

建议提示：

`用 HMM，自治深探。我要重构一个方法论型 skill。先结构化问题；如有明显收益概率，主动继续展开需要的模板、表示层、插件层。`

### 4. 做 source-aligned self-review

适合：

- 校验仓库是否仍然对齐 `metaPrompt v2`
- 排查 source authority、边界漂移、stage mismatch

建议提示：

`用 HMM，自治稳推。对齐 references/metaPrompt.md，做 source-aligned self-review。`

## 高阶玩法

下面这些才是真正有价值的“骚操作”。

### 1. 同题双跑，直接对照 profile

不要只问“`自治深探` 好不好用”。
拿同一个任务直接对照：

1. 先跑 `自治稳推`
2. 再跑 `自治深探`
3. 比较：
   - 谁更早做有界检索
   - 谁更早形成候选池
   - 谁更容易生成回退规则
   - 谁更容易越界

执行入口：

- [execution-profile-assets-index.md](references/execution-profile-assets-index.md)
- [execution-profile-non-self-runbook.md](references/execution-profile-non-self-runbook.md)

### 2. 用 HMM 验证 HMM，不要继续空转修 HMM

当前仓库最重要的不是继续补准备层，而是拿外部任务压测。

默认先跑：

- [execution-profile-non-self-run-01-problem-solving-brief.md](references/execution-profile-non-self-run-01-problem-solving-brief.md)

如果 run-01 无硬失败，再跑：

- [execution-profile-non-self-run-02-template-pluginization-brief.md](references/execution-profile-non-self-run-02-template-pluginization-brief.md)

### 3. 先 source-aligned，再外部任务

如果你要改 HMM 自身，顺序最好是：

1. 先 source-aligned self-review
2. 再跑非自迭代真实任务
3. 只根据真实任务暴露的问题回修仓库

而不是：

1. 连续重写仓库
2. 一直不跑真实任务

### 4. 用 example 反推当前轮应该长什么样

如果某一轮你不确定 `mode-resolution.json` 或 `evaluation-report.xml` 应该怎么写，先看：

- [examples-index.md](references/examples-index.md)

尤其是：

- retrieval -> generation -> evaluation
- pluginization -> self-upgrade
- template -> orchestration
- portfolio -> weighting -> governance

### 5. 用“共创稳推”做阶段协作

如果你希望：

- 每个关键阶段都能看到当前判断
- 但又不想每一步都被频繁打断

那就用：

- `HMM共创稳推`

它最适合：

- 方法论协作重写
- 文档大修
- source-aligned 重构
- 需要阶段性确认、但不需要每条分支都确认的任务

最实用提示：

`用 HMM，共创稳推。先结构化问题；有明显收益时主动继续展开，但只在关键阶段向我反馈，不要每一步都打断。`

### 6. 用“自治深探”做剃刀

自治深探不等于无上限扩张。

真正高阶的用法是：

- 先主动展开
- 再主动剃刀
- 把低收益扩展砍掉
- 只保留有真实下游价值的层

也就是说，最强的玩法不是“什么都展开”，而是“展开后还能收得住”。

## 现在应该怎么用

如果你只想最快进入执行，按这个顺序：

1. 打开 [execution-profile-assets-index.md](references/execution-profile-assets-index.md)
2. 看 [execution-profile-non-self-run-01-problem-solving-brief.md](references/execution-profile-non-self-run-01-problem-solving-brief.md)
3. 先跑 `自治稳推`（内部 comparison label: `autonomous_steady`）
4. 再跑 `自治深探`（内部 comparison label: `autonomous_deep`）
5. 填 [execution-profile-non-self-run-01-problem-solving-scorecard.json](references/execution-profile-non-self-run-01-problem-solving-scorecard.json)
6. 用 [execution-profile-non-self-comparison-result-template.md](references/execution-profile-non-self-comparison-result-template.md) 出短报告
7. 若无硬失败，再跑 run-02

## 仓库结构

- `SKILL.md`
  运行入口，定义总体工作流、执行档位、source-aligned 规则、输出契约

- `references/`
  方法、契约、状态机、边界、example、验证资产都在这里

- `agents/openai.yaml`
  宿主读取的 agent 入口说明

- `skills/HMM/`
  官方 GitHub 安装器友好的子路径入口，供 `--path skills/HMM` 使用

- `PORTABLE-PACKAGE-NOTES.md`
  可移植分发说明

## 可移植性

当前仓库已经做过一轮可移植清理：

- runtime 文件不依赖固定盘符
- 关键 reference 使用相对路径
- 包含 ASCII 别名源文件：
  - `references/agentic-nested-state-machine.opml`
- 历史 `artifacts/` 不纳入默认分发

适合分发的最小集合：

- `SKILL.md`
- `agents/`
- `references/`

## 全局剃刀

现在最重要的一条规则很简单：

- 不要继续默认扩仓库准备层
- 不要继续为了“更完整”而加新执行文件
- 不要继续做无真实压力的架构精修

当前仓库已经够你开始真正执行了。

正确下一步是：

- 先跑非自迭代真实任务对照
- 再根据运行结果决定是否回修

## 许可证

默认使用 `MIT License`。详见 [LICENSE](LICENSE)

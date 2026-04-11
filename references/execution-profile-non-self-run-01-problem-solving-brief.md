# execution-profile-non-self-run-01-problem-solving-brief

## Purpose

This file is the first ready-to-run non-self-iteration task brief for execution-profile comparison.

Use it with:

- `references/execution-profile-non-self-task-packet-a-problem-solving-v2.json`
- `references/execution-profile-non-self-comparison-scorecard-template.json`

## Task Brief

Task name:

- `local-first research workflow selection`

Task statement:

- I need to choose a practical knowledge and research workflow for a small methodology research team.
- The team has `5` people.
- Most members use `Windows`, one may use `macOS`.
- We need a local-first workflow for collecting notes, organizing source evidence, linking structured method fragments, and preparing reusable outputs for future plugin or skill work.
- I do not yet know whether the best route is:
  - plain Markdown plus Git plus search tooling,
  - an Obsidian-centered workflow,
  - or a more structured local database or hybrid approach.
- Please structure the problem first.
- If evidence gaps are real, do bounded search.
- Then generate candidate routes, compare them, define a validation plan, produce implementation steps, and include fallback rules.

## Known Constraints

- local-first is required
- low vendor lock-in is required
- source files should remain portable
- the team must be able to search and review evidence later
- onboarding cost should stay moderate
- the workflow should support later method reuse or pluginization
- do not design cloud governance or long-lived runtime operations

## Real Evidence Gaps

The run should treat these as real evidence gaps rather than pretending they are already settled:

- current offline and sync behavior of likely tools
- current export and portability limits
- practical metadata and linking support
- search quality and structured retrieval cost
- maintenance burden for a small team

## Desired Success Criteria

- the problem is clearly structured before tool comparison expands
- bounded search is used only where evidence is genuinely missing
- search results write back into comparison rather than staying as loose notes
- at least `3` candidate routes are compared explicitly
- one main path and at least one fallback path are produced
- validation steps and adoption checkpoints are explicit

## Recommended Run Order

1. run `autonomous_steady` first
2. run `autonomous_deep` second

Reason:

- the steady run gives the narrower baseline
- the deep run then reveals whether HMM now expands earlier or more completely when gain is plausible

## Prompt For `autonomous_steady`

`用 HMM，自治稳推。我要为一个 5 人的小型方法论研究团队选择一套 local-first 的资料沉淀与检索工作流。多数成员使用 Windows，可能有 1 人使用 macOS。目标是支持资料收集、证据回流、方法片段沉淀，以及后续插件或 skill 化准备。候选方向至少包括 plain Markdown + Git + search tooling、Obsidian-centered workflow、以及更结构化的本地数据库或混合方案。先结构化问题；只在证据足够强或明显必要时再继续做有界检索、候选解生成、比较、验证计划、实施步骤与回退规则，不要做低收益扩展。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

## Prompt For `autonomous_deep`

`用 HMM，自治深探。我要为一个 5 人的小型方法论研究团队选择一套 local-first 的资料沉淀与检索工作流。多数成员使用 Windows，可能有 1 人使用 macOS。目标是支持资料收集、证据回流、方法片段沉淀，以及后续插件或 skill 化准备。候选方向至少包括 plain Markdown + Git + search tooling、Obsidian-centered workflow、以及更结构化的本地数据库或混合方案。先结构化问题；如果有明显收益概率，就主动继续做有界检索、候选解生成、比较、验证计划、实施步骤与回退规则，不要过早停下。除非遇到真正关键分歧或硬阻塞，否则自行推进。`

## Expected Artifacts

- `search-notes.json`
- `selected-targets.json`
- `operator-calls.json`
- `candidate-pool.json`
- `solution-comparison.json`
- `solution-paths.json`
- `validation-plan.json`
- `implementation-steps.json`
- `fallback-rules.json`

## Evaluation Focus

- Did `autonomous_steady` stay on the mainline and avoid unnecessary expansion?
- Did `autonomous_deep` perform a stronger but still bounded retrieval and comparison expansion?
- Did both runs avoid runtime/provider/governance operations drift?
- Did both runs preserve portability and evidence-writeback logic as first-class concerns?

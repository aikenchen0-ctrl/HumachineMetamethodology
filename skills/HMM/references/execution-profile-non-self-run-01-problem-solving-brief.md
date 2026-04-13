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

1. run `自治稳推` first (`autonomous_steady`)
2. run `自治深探` second (`autonomous_deep`)

Reason:

- the steady run gives the narrower baseline
- the deep run then reveals whether HMM now expands earlier or more completely when gain is plausible

## Prompt For `自治稳推` (`autonomous_steady`)

`用 HMM，自治稳推。我需要为一个五人的方法论研究团队选择本地优先的知识与研究工作流。大多数成员使用 Windows，其中一人可能使用 macOS。这个工作流需要支持笔记采集、证据回看、结构化方法片段整理，以及后续的插件或 skill 准备。候选路线至少包括 Markdown + Git + 搜索工具、以 Obsidian 为中心的工作流，以及更结构化的本地数据库或混合方案。先结构化问题。只有在需求明确或证据足够强时，再继续做有界检索、候选解生成、比较、验证计划、实施步骤和回退规则。避免低收益扩展，除非出现真实阻塞。`

## Prompt For `自治深探` (`autonomous_deep`)

`用 HMM，自治深探。我需要为一个五人的方法论研究团队选择本地优先的知识与研究工作流。大多数成员使用 Windows，其中一人可能使用 macOS。这个工作流需要支持笔记采集、证据回看、结构化方法片段整理，以及后续的插件或 skill 准备。候选路线至少包括 Markdown + Git + 搜索工具、以 Obsidian 为中心的工作流，以及更结构化的本地数据库或混合方案。先结构化问题。如果有明显收益概率，就继续做有界检索、候选解生成、比较、验证计划、实施步骤和回退规则，不要过早停下，除非出现真实阻塞。`

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

- Did `自治稳推` (`autonomous_steady`) stay on the mainline and avoid unnecessary expansion?
- Did `自治深探` (`autonomous_deep`) perform a stronger but still bounded retrieval and comparison expansion?
- Did both runs avoid runtime/provider/governance operations drift?
- Did both runs preserve portability and evidence-writeback logic as first-class concerns?

# execution-profile-non-self-run-02-template-pluginization-brief

## Purpose

This file is the second ready-to-run non-self-iteration task brief for execution-profile comparison.

Use it with:

- `references/execution-profile-non-self-task-packet-b-template-pluginization-v2.json`
- `references/execution-profile-non-self-comparison-scorecard-template.json`

## Task Brief

Task name:

- `methodology workshop packaging`

Task statement:

- I need to turn a recurring internal workshop process into a reusable method package.
- The workshop is used to help small teams structure ambiguous problems, collect evidence, compare candidate directions, and produce reusable outputs.
- I do not want only a one-off checklist.
- I want to know whether the process should stop at:
  - a reusable template chain,
  - or continue into plugin drafts and a future skill-facing shell.
- Please structure the problem first.
- If reuse value and stability are real, continue toward template and pluginization outputs.
- Keep plugin structure separate from executable MCP skill identity.

## Known Constraints

- the package must remain local-file friendly
- the reusable structure must stay understandable to humans
- plugin drafts must not become a second copy of the whole main methodology
- plugin and MCP skill must remain separate layers
- the result should support later writeback from future workshop runs
- do not widen into runtime/provider/governance operations

## Real Stability Questions

The run should treat these as real stability questions rather than assuming they are already solved:

- which workshop steps are truly repeated across teams
- which terms and constraints remain stable enough for reuse
- whether a template chain alone is sufficient
- whether plugin drafts add real value beyond a reusable template
- what feedback and upgrade rules would be required for later refinement

## Desired Success Criteria

- the workshop process is structured before reuse artifacts are emitted
- at least one reusable template-chain direction is made explicit
- pluginization is attempted only if the reusable slice is stable enough
- plugin drafts, interfaces, feedbacks, and upgrade rules remain distinct
- one clear main reuse path and one lower-commitment fallback path are visible

## Recommended Run Order

1. run `自治稳推` first (`autonomous_steady`)
2. run `自治深探` second (`autonomous_deep`)

Reason:

- the steady run gives the narrower baseline for reuse crystallization
- the deep run then reveals whether HMM more proactively promotes reusable structure into plugin-level artifacts

## Prompt For `自治稳推` (`autonomous_steady`)

`用 HMM，自治稳推。我需要把一个重复发生的内部工作坊流程沉淀成可复用的方法包。先结构化问题。只有在复用价值和结构稳定性已经足够明确时，再继续做模板链、插件草案、接口线索、反馈回流和升级规则。避免低收益扩展，除非出现真实阻塞。`

## Prompt For `自治深探` (`autonomous_deep`)

`用 HMM，自治深探。我需要把一个重复发生的内部工作坊流程沉淀成可复用的方法包。先结构化问题。如果有明显收益概率，就继续做模板链、插件草案、接口线索、反馈回流和升级规则，不要过早停下，除非出现真实阻塞。`

## Expected Artifacts

- `template-chain.json`
- `pruning-notes.json`
- `plugin-decisions.json`
- `plugin-drafts.json`
- `plugin-interfaces.json`
- `plugin-feedbacks.json`
- `plugin-upgrade-rules.json`

## Evaluation Focus

- Did `自治稳推` (`autonomous_steady`) keep the reuse path narrower and require clearer stability before pluginization?
- Did `自治深探` (`autonomous_deep`) crystallize reusable structure into plugin drafts more proactively?
- Did both runs keep plugin versus MCP skill identity explicit?
- Did both runs avoid runtime/provider/governance operations drift?

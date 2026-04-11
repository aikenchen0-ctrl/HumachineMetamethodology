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

`Use HMM in autonomous_steady mode. I need to choose a local-first knowledge and research workflow for a five-person methodology research team. Most people use Windows and one person may use macOS. The workflow should support note collection, evidence review, structured method fragments, and later plugin or skill preparation. Candidate routes should include plain Markdown plus Git plus search tooling, an Obsidian-centered workflow, and a more structured local database or hybrid approach. Structure the problem first. Only continue into bounded retrieval, candidate generation, comparison, validation planning, implementation steps, and fallback rules when the need is explicit or strongly supported. Avoid low-value expansion unless there is a real blocker.`

## Prompt For `autonomous_deep`

`Use HMM in autonomous_deep mode. I need to choose a local-first knowledge and research workflow for a five-person methodology research team. Most people use Windows and one person may use macOS. The workflow should support note collection, evidence review, structured method fragments, and later plugin or skill preparation. Candidate routes should include plain Markdown plus Git plus search tooling, an Obsidian-centered workflow, and a more structured local database or hybrid approach. Structure the problem first. If clear gain is likely, continue into bounded retrieval, candidate generation, comparison, validation planning, implementation steps, and fallback rules without stopping early unless there is a real blocker.`

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

# execution-profile-non-self-runbook

## Purpose

This file is the step-by-step runbook for executing non-self comparison rounds.

Use it after the repository-side preparation is complete.

## Required Inputs

Choose one ready-to-run brief:

- `references/execution-profile-non-self-run-01-problem-solving-brief.md`
- `references/execution-profile-non-self-run-02-template-pluginization-brief.md`

Choose the matching scorecard:

- `references/execution-profile-non-self-run-01-problem-solving-scorecard.json`
- `references/execution-profile-non-self-run-02-template-pluginization-scorecard.json`

Use the general comparison plan as the governing rule:

- `references/execution-profile-non-self-comparison-plan.md`

## Profile Naming Convention

Use public keywords in actual prompts:

- `自治稳推` -> internal comparison label `autonomous_steady`
- `自治深探` -> internal comparison label `autonomous_deep`

Scorecards, examples, and machine-readable contracts may keep the internal labels.
Do not treat the internal labels as the recommended user-facing prompt keywords.

## Pre-Run Checklist

Before execution, confirm:

1. the task brief is fixed
2. both runs will use the same task statement
3. both runs will use the same source materials
4. both runs will use the same explicit constraints
5. only the execution profile will differ
6. the runs will happen in isolated sessions when possible

## Run Order

Default order:

1. run `自治稳推` first (`autonomous_steady`)
2. run `自治深探` second (`autonomous_deep`)

Reason:

- `steady` should establish the narrower baseline first
- `deep` should then show whether stronger proactive expansion adds useful value

## Execution Steps

### Step 1

Open the selected task brief.

Copy:

- the task statement
- the known constraints
- the success criteria
- the profile-specific prompt for the current run

### Step 2

Run the `自治稳推` prompt in a clean session and record it under the `autonomous_steady` block.

Record:

- the exact public keyword used
- the main artifacts produced
- the required artifacts still missing
- the stage-specific outputs still missing
- whether profile adherence is visible
- whether bounded search happened
- whether explicit comparison or reuse artifacts appeared
- whether scope alignment stayed intact
- whether any boundary drift appeared
- where the run stopped

### Step 3

Write those observations into the matching `autonomous_steady` block of the scorecard.

Do not fill final verdicts yet.

### Step 4

Run the `自治深探` prompt in a separate clean session if possible and record it under the `autonomous_deep` block.

Record:

- the exact public keyword used
- the main artifacts produced
- the required artifacts still missing
- the stage-specific outputs still missing
- whether profile adherence is visible
- whether bounded search or proactive probe happened
- whether deeper generation, evaluation, template, or pluginization layers were activated
- whether scope alignment stayed intact
- whether any boundary drift appeared
- where the run stopped

### Step 5

Write those observations into the matching `autonomous_deep` block of the scorecard.

### Step 6

Compare the two runs directly.

Fill:

- `difference_visibility`
- `deep_extra_gain`
- `steady_mainline_quality`
- `boundary_integrity_result`
- `winner_for_this_task`
- `over_expansion_risk`
- `under_expansion_risk`

### Step 7

Set:

- `overall_verdict`
- `next_adjustment_recommendation`

Only do this after both runs are fully recorded.

## What To Compare

At minimum compare:

1. profile recognition
2. profile adherence
3. expansion strength
4. probe count and probe quality
5. evidence writeback quality
6. produced artifacts versus missing required outputs
7. missing stage outputs
8. artifact depth
9. stop timing
10. boundary integrity

## Hard Stop Conditions

Stop and mark the run as failed if:

1. source authority is bypassed
2. blocked runtime operations are activated without real scope
3. plugin and MCP skill identity are blurred
4. semantic authority is silently rewritten downstream

## After-Run Output

After a comparison round, produce:

1. the filled scorecard
   - including produced artifacts, missing required outputs, and missing stage outputs
2. one short result report using:
   - `references/execution-profile-non-self-comparison-result-template.md`

## Default Next Move

If run `01` is complete and stable:

- proceed to run `02`

If run `01` reveals hard failure:

- pause further execution
- adjust the repository contracts or profile policy before continuing

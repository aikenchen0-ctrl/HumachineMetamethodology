# source-alignment-policy

## Purpose

This file prevents scope drift when the skill is being aligned to the original source materials:

- `metaPrompt.md`
- `agentic-nested-state-machine.opml`

The original source is primarily about:

- problem clarification
- true demand / true constraints
- ANT / EAFC modeling
- resource and actor-network modeling
- flow analysis
- SAFC / contradiction solving
- template chains
- branch planning
- shared-file coordination
- memory pruning
- evaluation and critique

It is not primarily about long-lived runtime operations engineering.

## Two Rings

### Ring 1: Source-Aligned Core

These capabilities are directly grounded in the original source and may be activated by default when the task is about:

- prompt refinement
- nested state-machine design
- method decomposition
- problem structuring
- branch planning
- template chains
- orchestration by shared context or memory pruning
- advanced ANT / resource / flow / SAFC analysis

Typical artifacts in this ring include:

- `problem-brief.json`
- `constraints-matrix.json`
- `branch-plan.json`
- `mode-resolution.json`
- `evaluation-report.xml`
- `loop-decision.json`
- `resource-graph.json`
- `actor-network.json`
- `function-field-model.json`
- `flow-analysis.json`
- `safc-model.json`
- `contradiction-analysis.json`
- `solution-set.json`
- `multi-screen-analysis.json`
- `critique-report.json`
- `template-chain.json`
- `pruning-notes.json`
- `shared-context-map.json`
- `orchestration-plan.json`
- `execution-supervision.json`
- `executor-interface.json`
- `executor-capability-registry.json`
- `memory-pruning.json`
- `writeback-ledger.json`

### Ring 2: Derived Runtime Operations Extension

These capabilities are valid engineering extensions, but they are not direct defaults from the original source. They must stay opt-in and scope-guarded.

This ring includes artifacts for:

- runtime hooks
- runtime event source contracts
- schema registries
- consumer compatibility probes
- source-of-truth drift monitoring
- scheduler hooks
- alert delivery contracts
- provider failover
- provider recovery
- health telemetry
- adaptive thresholds
- long-term threshold governance
- external governance source-of-truth

Examples include:

- `executor-runtime-hook.json`
- `runtime-event-source-contract.json`
- `runtime-event-source-registry.json`
- `runtime-event-source-service-hook.json`
- `runtime-schema-registry-hook.json`
- `consumer-runtime-discovery.json`
- `source-of-truth-drift-monitor.json`
- `drift-monitor-scheduler.json`
- `alert-delivery-contract.json`
- `delivery-provider-capability-matrix.json`
- `provider-health-check.json`
- `provider-health-telemetry.json`
- `provider-telemetry-stream-contract.json`
- `channel-failover-policy.json`
- `circuit-breaker-policy.json`
- `adaptive-threshold-policy.json`
- `threshold-governance-workflow.json`
- `baseline-governance-service-hook.json`
- `governance-source-drift-report.json`
- `governance-review-scheduler.json`
- `governance-provider-capability-matrix.json`

## Activation Rule

When the current task is:

- reading the original source
- aligning the skill back to the source
- refining prompt methods
- refining problem-structuring workflows
- refining branch logic
- refining template or memory behavior

then Ring 2 must remain inactive unless the user explicitly asks for real runtime operations behavior.

## Scope Guard

Do not activate Ring 2 just because the user mentions:

- branching
- parallel work
- shared files
- worker supervision
- memory pruning
- feedback
- governance

Ring 2 may activate only when the task explicitly includes at least one of:

- real runtime signal intake
- external service hooks
- registry version compatibility
- provider topology
- failover or recovery switching
- continuous drift monitoring
- long-lived threshold governance operations

## Mode-Resolution Requirement

When the current task is source alignment, `mode-resolution.json` should make the distinction explicit:

- what is active in the source-aligned core
- what is blocked as a derived runtime extension
- why the blocked outputs are out of scope for the current round

## Repair Rule

If the skill has already drifted into Ring 2 while the task is still source alignment:

1. do not add more runtime artifacts
2. record the drift explicitly
3. block the non-source outputs in `mode-resolution.json`
4. route repair back to the earliest scope-definition layer rather than patching downstream artifacts only

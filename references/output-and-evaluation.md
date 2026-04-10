# output-and-evaluation

## Purpose

Use this reference when the task needs:

- structured output mapping across formats,
- stronger evaluation than “this sounds fine”,
- or explicit writeback from retrieval, generation, evaluation, and pluginization layers.

This file is now aligned to the maintained chapter-based `metaPrompt v2` source.

It mainly supports:

- chapter 8: retrieval and evidence writeback
- chapter 9: candidate generation
- chapter 10: evaluation, validation, and implementation shaping
- chapter 11: pluginization and skill exteriorization

## Boundary

This file does not define the whole workflow.

It only defines:

1. how structured outputs should remain stable across formats,
2. how evaluation should be performed,
3. and how output-bearing layers should hand artifacts forward or write them back.

## Structured Translation

Structured translation is not cosmetic.

It exists to preserve the same problem object across:

- natural-language input,
- normalized variables,
- graph structure,
- logic structure,
- candidate records,
- evaluation records,
- and plugin writeback structures.

Do not let each downstream format reinterpret the problem freely.

## Format Families

### Variable Mapping

Use when:

- a later template or artifact needs stable variables,
- natural language must be compressed into reusable normalized fields,
- or retrieval results must be written back into stable slots.

Prefer fields such as:

- `variable_name`
- `source_text`
- `normalized_value`
- `confidence`
- `notes`

### Graph Format

Use when:

- nodes and edges matter more than sequence,
- or a system-level relation view is needed.

Prefer fields such as:

- `nodes`
- `edges`
- `edge_type`

### Triple Format

Use when:

- the goal is compressed relation statements,
- and full graph structure would be heavier than needed.

Canonical shape:

- `(subject, relation, object)`

### DAG Format

Use when:

- dependency order matters,
- branches exist,
- implementation steps must stay acyclic,
- or downstream execution needs a dependency view.

Prefer fields such as:

- `node_id`
- `dependencies`
- `outputs`

### Logic Format

Use when:

- necessary conditions,
- sufficient conditions,
- gating rules,
- contradiction boundaries,
- or rollback triggers

must be made explicit.

Prefer fields such as:

- `condition`
- `conclusion`
- `logic_relation`

## Evaluation Methods

### Same-Source Consistency

Check whether artifacts derived from the same source still describe the same object, scope, and goal.

### Cross-Format Consistency

Check whether prose, graph, triple, logic, and exported representations still refer to the same underlying problem rather than drifting apart.

### Fact-Level Validation Chain

Break key conclusions into fact-sized verification steps instead of keeping them as one large untestable claim.

### Unverifiable Assumptions

Mark what cannot currently be verified instead of silently passing it through as fact.

### Cross-Mode Interaction Check

When two or more extension modes are active, evaluate whether their interaction is coherent.

Check at least:

- whether handoffs between artifacts are explicit,
- whether authority boundaries are clear,
- whether one mode is overriding another mode without declaring it,
- and whether serialization-only modes are inventing semantics instead of exporting upstream meaning.

Useful optional field:

- `mode_interaction_checks`

Prefer each entry to expose:

- `interacting_modes`
- `handoff_status`
- `authority_status`
- `drift_risk`
- `decision`

### Multi-Reviewer Approval Topology

When one exported representation must pass through multiple human review roles, evaluate more than simple “approved or not”.

Check at least:

- whether every reviewer sees the same payload object,
- whether approval order is explicit,
- whether rejection sends the flow back to regeneration, revision, or re-review explicitly,
- whether reviewer conflict resolution is explicit,
- and whether final release authority is separate from payload serialization authority.

Prefer this topology to live in:

- `governance-checkpoints.json`
- `override-policy.json`

Useful optional fields:

- `review_topology`
- `approval_order`
- `rejection_reentry_rules`
- `reviewer_conflict_resolution`
- `export_regeneration_rules`

### Key-Step Role Check

When evaluation needs more depth, classify major steps as one of:

- `necessary_condition`
- `sufficient_condition`
- `pivot_variable`

This is especially useful for:

- chapter 6 output review,
- chapter 9 candidate selection,
- chapter 10 path comparison,
- and chapter 11 plugin decision.

### Self-Score Boundary

Self-scoring is allowed only as a weak auxiliary mechanism.

Rules:

- it should help expose obvious weakness,
- it must include a concrete deduction reason,
- it must not replace evidence,
- and it must not be the only reason a path is accepted or rejected.

Useful optional fields:

- `self_score`
- `score_reason`

## Chapter-Aware Embedding Points

### Chapter 4

`problem-brief.json`

May include:

- `variable_map`

when natural-language inputs must be normalized early.

### Chapter 8

`search-notes.json`

May include:

- `variable_map`
- `source_priority`
- `writeback_targets`

because retrieval is now a first-class maintained source layer rather than a side note.

### Chapter 9

`branch-plan.json`

May include:

- `dag_view`
- `triple_view`

when candidate generation and branch structure need explicit compression.

### Chapter 10

`evaluation-report.xml`

Should always keep:

- `same_source_consistency`
- `cross_format_consistency`
- `fact_validation_chain`
- `unverifiable_assumptions`

Optional when deeper evaluation is needed:

- `key_step_role_checks`
- `mode_interaction_checks`
- `self_score`
- `score_reason`

### Chapter 11

Plugin-oriented artifacts should explicitly preserve writeback semantics, for example:

- which evaluation findings become plugin rules,
- which retrieval sources become plugin defaults,
- which generation patterns become plugin operator maps,
- which failure findings become plugin failure modes.

## Recommended Entry Structure

Prefer each `key_step_role_checks` entry to expose:

- `step_or_artifact`
- `role_classification`
- `why`
- `evidence`

Prefer each writeback-sensitive entry to expose:

- `writes_back_to`
- `writeback_payload`
- `writeback_reason`
- `scope_guard`

## Default Rule

When in doubt:

1. keep the problem object stable,
2. keep chapter handoffs explicit,
3. keep evaluation richer than prose plausibility,
4. and keep retrieval/generation/evaluation/pluginization writeback visible instead of implicit.

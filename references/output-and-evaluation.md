# output-and-evaluation

## Purpose

Use this reference when the task needs either:

- structured output mapping across formats,
- or stronger evaluation beyond "this sounds fine".

This file is source-aligned with the original material on:

- structured translation,
- template variable mapping,
- graph export,
- triple export,
- DAG export,
- logic-symbolic export,
- same-source consistency,
- cross-format consistency,
- fact-level validation chains,
- and self-scoring only as a weak auxiliary check.

## Structured Translation

Structured translation is not a cosmetic step.

It should preserve mappings between:

- natural-language input,
- normalized variables,
- graph structure,
- and logic structure.

Do not let each downstream format reinterpret the problem freely.

## Format Families

### Variable Mapping

Use when:

- a later template or artifact needs stable variables,
- or natural language must be compressed into reusable normalized fields.

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
- or downstream execution needs a non-cyclic dependency view.

Prefer fields such as:

- `node_id`
- `dependencies`
- `outputs`

### Logic Format

Use when:

- necessary conditions,
- sufficient conditions,
- gating rules,
- or contradiction boundaries must be made explicit.

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

When two or more extension modes are active, evaluate whether their interaction is actually coherent.

Check at least:

- whether handoffs between artifacts are explicit,
- whether authority boundaries are clear,
- whether one mode is overriding or redefining another mode without that being declared,
- and whether serialization-only modes are inventing semantics instead of exporting existing ones.

Useful optional field:

- `mode_interaction_checks`

Prefer each `mode_interaction_checks` entry to expose:

- `interacting_modes`
- `handoff_status`
- `authority_status`
- `drift_risk`
- `decision`

### Multi-Reviewer Approval Topology

When one exported representation must pass through multiple human review roles, evaluate more than simple "approved or not" status.

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

## Key-Step Role Check

When evaluation needs more depth, classify major steps as one of:

- `necessary_condition`
- `sufficient_condition`
- `pivot_variable`

Do not force every round to include this layer, but make it explicit when the user asks for deeper evaluation or when a route is being justified as dominant.

## Self-Score Boundary

Self-scoring is allowed only as a weak auxiliary mechanism.

Rules:

- it should help expose obvious weakness,
- it must include a concrete deduction reason,
- it must not replace evidence,
- and it must not be the only reason a path is accepted or rejected.

Useful optional fields:

- `self_score`
- `score_reason`

## Recommended Embedding Points

- `problem-brief.json`
  Add `variable_map` when natural-language inputs must be normalized.
- `branch-plan.json`
  Add `dag_view` and `triple_view` when dependency structure or relation compression matters.
- `evaluation-report.xml`
  Always keep:
  - `same_source_consistency`
  - `cross_format_consistency`
  - `fact_validation_chain`
  - `unverifiable_assumptions`

Optional when deeper evaluation is needed:

- `key_step_role_checks`
- `mode_interaction_checks`
- `self_score`
- `score_reason`

Prefer each `key_step_role_checks` entry to expose:

- `step_or_artifact`
- `role_classification`
- `why`
- `evidence`

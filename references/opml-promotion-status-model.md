# opml-promotion-status-model

## Purpose

This file defines a normalized promotion model for ideas that originate in `agentic-nested-state-machine.opml`.

It exists because the OPML behaves like a rich design archive, but the archive itself does not clearly state how one idea should move from speculative note to executable architecture.

## Why This Model Is Needed

Without a promotion model, a source node can be promoted too early or too implicitly:

- an example becomes a default rule,
- a rule candidate becomes a contract without enough evidence,
- a UI idea contaminates the workflow layer,
- or a reference concept is treated like an executable state.

The promotion model reduces that ambiguity.

## Promotion States

### 1. `exploratory_example`

Meaning:

- an illustrative scenario,
- a probe,
- a "用户想……" branch,
- or a local thought experiment.

Expected properties:

- useful for ideation,
- not authoritative,
- may be deleted or replaced freely,
- must not become a workflow default without explicit review.

### 2. `candidate_rule`

Meaning:

- an observed pattern that looks reusable,
- but has not yet been normalized into contract language.

Expected properties:

- should have a clear scope,
- should have at least one justification source,
- should not yet force downstream artifacts to depend on it.
- should expose why it is blocked from promotion,
- and should prefer an explicit decomposition target instead of staying vague.

### 3. `active_contract`

Meaning:

- the idea has been promoted into:
  - a state rule,
  - an artifact field,
  - an active reference contract,
  - a mode interaction requirement,
  - or another executable contract surface.

Expected properties:

- machine-readable or strongly structured,
- stable enough for reuse,
- auditable by evaluation logic,
- must not conflict with existing authority boundaries.

### 4. `archived_reference`

Meaning:

- the idea remains important as theory, rationale, or source context,
- but it is not active in the current executable workflow.

Expected properties:

- still readable,
- still citable,
- not required for every round,
- activated only when its domain actually matters.

## Promotion Gates

An idea should usually move through these gates:

1. `exploratory_example -> candidate_rule`
   Gate:
   - the example repeats or reveals a stable pattern
   - its role is no longer only illustrative

2. `candidate_rule -> active_contract`
   Gate:
   - scope is explicit
   - responsibility plane is explicit
   - authority boundary is explicit
   - at least one downstream consumer exists
   - the idea can be checked by evaluation

3. `candidate_rule -> archived_reference`
   Gate:
   - the idea is useful to remember
   - but not stable enough or important enough to govern current execution

4. `active_contract -> archived_reference`
   Gate:
   - the idea is no longer a current default
   - but should still remain as preserved rationale or historical compatibility note

## Promotion Tests

Before promoting anything into `active_contract`, ask:

- Is this object a state, rule, artifact, UI idea, reference, or example?
- Which architecture plane owns it?
- Who computes it?
- Who may override it?
- What downstream artifact consumes it?
- What evaluation check can reject it if it drifts?

If those questions cannot be answered cleanly, the idea is probably not ready for `active_contract`.

For `candidate_rule` in particular, also ask:

- does this source node still mix more than one node type,
- can it be decomposed into cleaner downstream targets,
- what specific blocker prevents promotion right now,
- and what concrete next resolution action should be taken.

## Demotion Rules

An idea should be demoted when:

- it causes repeated cross-mode ambiguity,
- no downstream artifact actually consumes it,
- it is still mostly illustrative,
- or it turns out to belong to UI/product speculation rather than executable workflow design.

Demotion paths:

- `active_contract -> candidate_rule`
- `candidate_rule -> exploratory_example`
- `active_contract -> archived_reference`

## Relation To Current References

- `node-taxonomy.md`
  tells you what class a node is.
- `scope-boundary.md`
  tells you which architectural layer it belongs to.
- this file tells you what promotion status it currently deserves.

Together they form a cleaner architecture pipeline for source-derived concepts.

## Suggested Future Machine-Readable Form

If the source continues to evolve, a later structured companion file could expose entries such as:

- `source_node_id`
- `source_label`
- `node_type`
- `scope_layer`
- `promotion_status`
- `promotion_basis`
- `promotion_gates_passed`
- `promotion_blockers`
- `decomposition_required`
- `decomposes_into`
- `recommended_next_status`
- `promotion_strategy`
- `resolution_action`
- `downstream_consumers`
- `authority_owner`
- `evaluation_hooks`

`recommended_next_status` should always stay inside the normalized promotion-state set.

If a source node still needs a split, rename, defer, or archive decision before reaching that status, record that in a separate `promotion_strategy` field rather than inventing ad hoc status names.

That would make the OPML promotion path auditable rather than implicit.

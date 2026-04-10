# opml-functional-architecture-review

## Purpose

This document reviews the source file `agentic-nested-state-machine.opml` at the functional-design abstraction layer.

It is not a restatement of the OPML.
Its job is to answer:

- what logic is structurally weak in the original mother-structure,
- why those weaknesses create downstream ambiguity,
- and what higher-level architecture would make the design more coherent.

## Primary Diagnosis

The OPML is rich, but its main weakness is not lack of ideas.
Its weakness is that too many different design roles are mixed inside the same branch shapes.

At the abstraction layer, the OPML repeatedly mixes:

- method semantics,
- workflow states,
- artifact outputs,
- orchestration rules,
- UI interaction ideas,
- concrete usage examples,
- and runtime-style execution imagination.

This makes the source powerful as a thought archive, but unstable as a directly executable architecture.

## Weak Logic In The OPML

### 1. One Node Often Carries Multiple Roles

A single node often behaves like:

- a state,
- a rule,
- an artifact,
- and an example

at the same time.

This makes it hard to answer basic architectural questions such as:

- is this node executable,
- is it only descriptive,
- does it produce a file,
- or is it only illustrating a scenario.

### 2. Method Layer And Product Layer Are Mixed

The OPML contains both:

- problem-structuring method logic,
- and product interaction ideas such as selection, highlighting, scrolling, buttons, viewport composition, and editing behavior.

At the abstraction layer these should not live in the same plane.

If they remain mixed:

- workflow contracts become polluted by UI details,
- and UI ideas are mistaken for required system semantics.

### 3. Planning Semantics And Execution Semantics Are Mixed

The OPML frequently moves from:

- "how to structure the problem"

to:

- "how workers should coordinate"
- "how shared files should be edited"
- "how execution should be supervised"

without always declaring the boundary.

This produces a hidden jump from:

- reasoning architecture

to:

- execution fabric.

### 4. Human Authority Is Present But Not Normalized

The source repeatedly asserts that:

- humans can inspect files,
- humans can modify prompts,
- humans can set weights,
- and humans can redirect outcomes.

But in the OPML this appears as repeated local statements rather than one normalized authority model.

Without a normalized authority layer, later branches can easily disagree about:

- who computes,
- who reviews,
- who overrides,
- and who has final authority.

### 5. Example Nodes And Rule Nodes Are Not Cleanly Separated

Many branches use:

- "用户想……"
- "例子：……"
- "或者这样交互……"

These are useful design probes, but they are not system rules.

If examples are not explicitly isolated:

- examples get promoted into architecture accidentally,
- and the system loses a stable distinction between illustrative and normative content.

### 6. The Source Lacks A Clear Promotion Path

The OPML has many strong ideas, but it rarely says how an idea should move from:

1. example
2. rule candidate
3. artifact contract
4. workflow default

This missing promotion path is one reason the source feels generative but structurally unstable.

### 7. Output Layer Is Present But Not Fully Bundled

The OPML already knows that XML, Mermaid, DAG, triples, and logic formats matter.

The weak point is that the output layer is often expressed as:

- isolated format options

rather than:

- one explicit representation system with selection rules, target mappings, and downstream consumers.

### 8. Evaluation Is Strong Conceptually But Weak As A Shared Functional Service

The source has good evaluation ideas:

- same-source consistency,
- cross-format consistency,
- fact-level validation,
- self-score limits.

The weak point is that evaluation appears as a capability cluster rather than as a first-class cross-cutting service with a uniform contract applied to every major interaction.

## Optimized Abstract Architecture

The OPML becomes much stronger if its ideas are reorganized into explicit planes.

### Plane 1: Source Semantics Plane

Owns:

- true demand / true constraints,
- problem formation chain,
- EAFC semantics,
- anti-goals,
- actor-network roles.

Question:

- what does the problem mean.

### Plane 2: Workflow Control Plane

Owns:

- state order,
- loopback logic,
- stage entry / exit,
- finish conditions.

Question:

- when does the workflow move.

### Plane 3: Artifact Contract Plane

Owns:

- artifact names,
- required fields,
- optional fields,
- stage insertion points.

Question:

- what each stage must leave behind.

### Plane 4: Capability Mode Plane

Owns:

- advanced analysis,
- template compression,
- weighting,
- orchestration,
- variant recomposition,
- traversal,
- discovery,
- portfolio,
- governance,
- representation.

Question:

- which optional capability is active this round.

### Plane 5: Interaction Plane

Owns:

- question style,
- review checkpoints,
- human override boundaries,
- prompt entry style.

Question:

- how humans and the workflow interact.

### Plane 6: Execution Plane

Owns:

- branch classes,
- worker scopes,
- shared-file coordination,
- reference_context handling,
- writeback logging.

Question:

- how execution is coordinated after planning exists.

### Plane 7: Representation Plane

Owns:

- XML,
- Mermaid,
- triples,
- DAG,
- logic export,
- representation bundles.

Question:

- how stable semantics are serialized.

### Plane 8: Example Plane

Owns:

- illustrative scenarios,
- sample mode interactions,
- example indexes.

Question:

- what reusable pattern helps explain the architecture.

### Plane 9: Evaluation Plane

Owns:

- consistency checks,
- fact validation,
- role checks,
- mode interaction checks,
- self-score limits.

Question:

- whether the round is coherent enough to continue.

## Functional Design Improvements For The OPML

### Improvement 1: Separate "Design Archive" From "Executable Contract"

The OPML should remain the design archive.

But every concept that becomes operational should be promoted into one of:

- a reference file,
- a state contract,
- a state-machine rule,
- or a standard example.

### Improvement 2: Add Explicit Node Typing At Source Level

Every promoted OPML node should be typed as one of:

- state
- rule
- artifact
- ui
- reference
- example

Without this, the source keeps regenerating ambiguity downstream.

### Improvement 3: Introduce An Authority Model Early

The source should not only repeat that humans may modify things.

It should normalize:

- computed_by
- overridden_by
- serialized_by
- final_authority

This is especially important where weighting, governance, serialization, and execution all touch the same object.

### Improvement 4: Add A Promotion Pipeline

Every strong idea from the OPML should have one of four statuses:

- exploratory_example
- candidate_rule
- active_contract
- archived_reference

This would prevent accidental rule inflation from examples.

### Improvement 5: Treat Evaluation As A Shared Service

Instead of scattering review logic, evaluation should be treated as one cross-cutting service that every major interaction passes through.

That service should always be able to ask:

- is the object internally consistent,
- is it cross-format consistent,
- is its evidence chain explicit,
- does it conflict with another active mode,
- and what authority boundary actually decides the result.

## Relation To The Current Skill

The current `HMM` skill has already repaired a meaningful part of this architecture:

- it split many mixed OPML concerns into references, contracts, state rules, and examples,
- it introduced explicit mode interaction structures,
- and it began indexing standard cross-mode patterns.

What still remains weaker than ideal:

- the example plane is now machine-readable across the main high-value interaction patterns, including multi-reviewer export approval topology, but it is still a bounded standard library rather than exhaustive coverage,
- source-level promotion status is normalized across a model, a source-node catalog, and a prioritized backlog; the resource-scan split, shared-file split, workflow-shell split, multiple-solution-sorting split, child-agent rename, and history-memory split have been promoted, and the architecture is now primarily in maintenance mode rather than promotion mode,
- the lightweight source-review reference contracts must stay synchronized so that examples, typed source fields, promotion status mappings, and backlog priorities do not drift apart,
- and the OPML itself remains a mixed archive rather than a typed architecture source.

## Current Maintenance Snapshot

Current source-review maintenance snapshot:

- source-review reference assets: `19`
- promotion catalog entries: `46`
- typed source entries: `56`
- backlog total items: `8`
- backlog non-completed items: `0`
- standard examples: `8`
- UI archive patterns: `6`
- execution substrate classes: `6`
- optional strategy classes: `4`
- remaining `candidate_rule` count: `1`

Current residual `candidate_rule`:

- `src_029_parallel_fork`
  This is now an intentional defer case rather than an unattended promotion gap.

For the post-P2 roadmap, read:

- `references/opml-architecture-optimization-roadmap.md`
- `references/opml-architecture-optimization-roadmap.json`
- `references/legacy-artifact-compatibility-policy.md`
- `references/legacy-artifact-compatibility-policy.json`
- `references/branch-topology-decision-table.md`
- `references/branch-topology-decision-table.json`
- `references/typed-source-node-index.md`
- `references/typed-source-node-index.yaml`
- `references/metaPrompt-step-index.md`
- `references/metaPrompt-step-index.json`
- `references/source-node-type-registry.md`
- `references/source-node-type-registry.json`
- `references/product-interaction-boundary.md`
- `references/ui-pattern-archive.json`
- `references/executor-persona-boundary.md`
- `references/execution-substrate-taxonomy.json`
- `references/strategy-intervention-boundary.md`
- `references/optional-strategy-mode.json`
- `references/boundary-razor-policy.md`
- `references/boundary-razor-policy.json`
- `references/release-consolidation-checklist.md`
- `references/release-consolidation-checklist.json`
- `references/release-final-review.md`
- `references/release-final-review.json`

## Recommended Next Moves

1. Keep `examples-index.json`, `opml-promotion-status-model.json`, `source-node-promotion-catalog.json`, and `opml-promotion-backlog.json` synchronized as one lightweight source-review reference-contract layer.
2. Keep the typed source companion and metaPrompt step index aligned with the promotion catalog and dual-source precedence so downstream review stops reconstructing source structure repeatedly.
3. Use the boundary razor to freeze archive planes unless a real downstream consumer now requires more distinction.
4. Keep topology and archive/compatibility work in maintenance mode unless a real reactivation case appears.
5. Keep the new optional strategy plane explicitly gated so demand-visibility shaping, field construction, and non-rational amplification do not silently leak back into the neutral core.
6. Use the release consolidation checklist as the default maintenance map instead of widening the review layer further.
7. When all gates are satisfied, treat the release-final-review assets as the current closeout record rather than reopening architecture work by default.
8. After closeout, default to delivery work rather than another abstract architecture pass unless a concrete downstream consumer or source drift reopens the problem.

# opml-architecture-optimization-roadmap

## Purpose

This file records the maintenance-mode architecture map that remains after the main source-node promotions were completed.

It is not another promotion catalog.
Its job is to answer:

- what weak logic still remains in the original OPML at the abstract functional-design layer,
- which new architecture plane would absorb that weakness cleanly,
- and which remaining backlog or follow-up asset each gap now points toward.

## Current Diagnosis In Maintenance Mode

The major mixed candidate rules have now been split or promoted.

That changes the architecture problem.

The OPML is no longer weakest at:

- ranking versus UI order,
- shared-file tool language,
- child-agent identity language,
- history-memory tool language,
- or workflow-shell versus orchestration-shell mixing.

The weakest logic has moved one layer upward:

- the source itself is still a free-form archive rather than a typed architecture source,
- product interaction design is still mixed into the same mother-structure as executable method logic,
- execution substrate taxonomy is still mixed into the method archive,
- branch-topology semantics are still only partially normalized,
- archive versus compatibility decisions remain tail-heavy and under-normalized,
- and strategy/intervention material still sits too close to the default problem-structuring core.

## Remaining Weak Logic Clusters

### 1. Typed Source Plane

The OPML is still a free-form tree.

A typed source companion now exists and is aligned to the current promotion catalog.

That means:

- node typing is reconstructed downstream,
- promotion status is reconstructed downstream,
- and scope-layer separation is reconstructed downstream.

This is workable, but it still remains one step away from a truly typed source of truth because the OPML itself is still a free-form archive.

Current maintenance stance:

- keep it aligned,
- do not create a new typed-source family by default,
- and only expand it when source change or real consumer need demands it.

### 2. Product Interaction Archive Plane

The source still contains many UI-heavy ideas in the same tree as method logic.

A product interaction archive now exists.

Current maintenance stance:

- keep workflow contracts insulated from UI leakage,
- keep the archive readable and machine-readable,
- but do not expand it unless a real product-facing consumer needs more distinction.

The source still contains many UI-heavy ideas in the same tree as method logic:

- viewport composition,
- colored text blocks,
- selection gestures,
- extraction buttons,
- scrolling structures,
- and concrete client implementation ideas.

These are useful, but they belong to a product interaction archive plane, not the executable method core.

### 3. Execution Substrate Plane

The source still includes execution-taxonomy material such as:

An execution substrate archive now exists.

Current maintenance stance:

- keep substrate taxonomy separate from orchestration,
- but do not expand it unless executor selection, continuity policy, or account-surface policy really needs it.

- multiple account-control agent types,
- temporary external helpers,
- account-bearing versus account-less agents,
- and execution substrate imagination tied to specific execution environments.

These ideas are not the same thing as the problem-structuring method.

They belong to an execution substrate plane that should attach below orchestration, not inside the method archive.

### 4. Topology Decision Plane

The current skill already separates:

- `parallel_worker`
- `parallel_branch`
- `serial_branch`
- `suspended_traversal`
- `parallel_fork`

But the source still contains overlapping topology imagination:

- "分裂"
- "两种模式"
- "多轮生成多个候选"
- "为了分开回复更好"
- and branch memory/merge assumptions that are still not normalized as one decision table.

This plane is already defined enough for maintenance.

Current maintenance stance:

- keep it waiting for a real distinguishing case,
- do not refine it further by speculation alone.

### 5. Archive And Compatibility Plane

Two tail decisions remain structurally important:

- `create_initial_prompt.md`
- `parallel_fork`

These items are no longer open work.
They now serve as maintenance checks on whether the skill can distinguish:

- historical artifact,
- compatibility artifact,
- deferred concept,
- and default contract.

### 6. Optional Strategy / Intervention Plane

The source still mixes neutral problem-structuring with stronger strategic material such as:

An optional strategy/intervention boundary now exists.

Current maintenance stance:

- keep it explicitly gated,
- keep it out of the neutral default core,
- and only reopen it when a task explicitly demands intervention design.

- field construction,
- adoption pressure,
- demand visibility shaping,
- and non-rational acceleration mechanisms.

Whether those ideas are useful or not is not the architecture problem.

The architecture problem is that they should not sit in the default core plane without an explicit optional strategy/intervention boundary.

## Proposed Next-Order Architecture

### Plane 10: Typed Source Plane

Owns:

- source node ids,
- source labels,
- node type,
- scope layer,
- promotion status,
- source-to-contract traceability.

Question:

- what the source says in typed form before downstream interpretation.

### Plane 11: Product Interaction Archive Plane

Owns:

- viewport ideas,
- selection interactions,
- comparison displays,
- editing gestures,
- concrete product-side interaction patterns.

Question:

- how humans would interact with the system at the product layer.

### Plane 12: Execution Substrate Plane

Owns:

- execution substrate taxonomy,
- executor persona classes,
- account-bearing versus account-less execution identities,
- external helper classes,
- runtime execution environment assumptions.

Question:

- what kind of execution substrate is assumed below orchestration.

### Plane 13: Topology Decision Plane

Owns:

- branch-class decision table,
- memory-sharing assumptions,
- merge expectation,
- topology selection rules,
- when a candidate path deserves `parallel_fork` rather than another branch class.

Question:

- which topology is actually being selected and why.

### Plane 14: Archive And Compatibility Plane

Owns:

- historical artifact preservation,
- compatibility-only artifacts,
- archive policy,
- revive-versus-retire decisions.

Question:

- whether an old source concept should stay preserved, revived, or retired.

### Plane 15: Optional Strategy / Intervention Plane

Owns:

- demand visibility shaping,
- adoption-pressure design,
- field-construction logic,
- optional strategic acceleration references.

Question:

- which strategy logic is intentionally activated beyond the neutral core.

## Recommended Next Moves

1. Keep the current source-review reference-contract layer synchronized.
2. Keep the typed source companion aligned with the promotion catalog whenever the source or promotion mapping changes.
   Also keep the metaPrompt step index aligned with the dual-source precedence rule.
3. Freeze the archive planes at their current boundary unless a real downstream consumer now requires more distinction.
4. Keep topology and archive/compatibility work in maintenance mode unless a real reactivation case appears.
5. Keep the new optional strategy plane explicitly gated so demand visibility shaping and intervention logic do not silently leak back into the default core.
6. Use `release-consolidation-checklist.*` as the default maintenance map instead of creating more review-layer families.

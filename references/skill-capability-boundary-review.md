# skill-capability-boundary-review

## Purpose

This file reviews the capability boundary of the `HMM` skill itself after the repository started aligning to the maintained chapter-based `metaPrompt v2`.

It answers:

1. what the skill must do by default,
2. what the skill may do only when the task explicitly requires it,
3. what the skill should never silently absorb into the neutral core,
4. and how this boundary maps back to the maintained source.

## Boundary Question

The central question is not:

- whether the source contains a concept

but:

- whether the skill must activate that concept by default in a normal round.

This distinction matters because `metaPrompt v2` is now a richer source than the current six-state runtime shell.

## Best-Practice Boundary Layers

### Layer A: Default Core Capability

These capabilities should exist in the skill by default:

1. task intake and clarification
2. shared symbol discipline
3. `E/A/F/Cond` modeling
4. state / constraint / contradiction / ideal-direction analysis
5. branch planning
6. evaluation and loopback

The skill is incomplete if it cannot do these without activating higher planes.

### Layer B: First-Class But Conditionally Expanded Capability

These capabilities are now part of the maintained source core, but should still be activated explicitly when needed:

1. retrieval and evidence writeback
2. deeper resource/system-level modeling
3. candidate generation as a distinct layer
4. explicit implementation planning
5. pluginization and skill exteriorization

These are not “secondary ideas”.
They are first-class method layers.

But they are still conditionally expanded in the runtime shell so the shell stays usable.

### Layer C: Optional Extension Planes

These remain optional extension planes even after `metaPrompt v2`:

1. deep advanced graph/flow/SAFC expansion
2. template chains
3. library and weighting systems
4. orchestration and memory expansion
5. portfolio optimization
6. representation-heavy export bundles

These should not silently activate just because the source contains related theory.

### Layer D: Out-Of-Core Planes

These should remain outside the neutral skill core by default:

1. UI/product interaction design
2. execution substrate taxonomy as first-class workflow identity
3. strategy/intervention wording as default neutral language
4. runtime/provider/governance operations engineering

## Current Repository Decision

Current repository best-practice boundary should be read as:

### Must Be In The Skill Core

- chapter 4 semantics
- chapter 5 semantics
- chapter 6 semantics
- six-state runtime shell
- evaluation and loopback

### Must Be Recognized As Real Method Layers

Even if they are not always fully active in every round, the skill must now explicitly recognize:

- chapter 8 retrieval and evidence writeback
- chapter 9 generation
- chapter 10 evaluation and implementation shaping
- chapter 11 pluginization and self-upgrade

That means these layers are no longer allowed to remain only as vague extension folklore.

### Must Stay Conditional

- deeper advanced mode artifacts
- orchestration-heavy execution logic
- template chains
- weighting / portfolio machinery

### Must Stay Out

- product interaction affordances
- concrete runtime carrier imagination
- intervention-first framing as default language

## Why This Matters

Without this boundary, the repository falls into one of two bad states:

1. it becomes too shallow and loses the real method,
2. or it becomes too wide and turns every round into architecture sprawl.

The maintained source now requires a middle path:

- richer than the old shell,
- but still bounded enough to remain usable as a skill.

## Current Reconstruction Implication

This review implies:

1. the repository should not revert to the old minimal reading of `metaPrompt`,
2. the repository should not explode the runtime shell into the full chapter scaffold by default,
3. the repository must make the boundary between default core, conditionally expanded layers, optional modes, and out-of-core planes explicit.

## Recommended Next Use

Use this file when deciding:

1. whether a capability belongs in `SKILL.md`,
2. whether a capability belongs only in a reference file,
3. whether a contract change is really needed,
4. whether a user request should activate a deeper mode or stay in the neutral core.

# core-method

## Purpose

Use this reference when you need the real method core from:

- `metaPrompt.md`
- `agentic-nested-state-machine.opml`

without reopening all of their UI ideas, branch UI details, or secondary examples.

This file keeps only the parts that should directly shape the skill's default reasoning.

## Original Skeleton

The source is not one prompt. It is a two-layer structure:

1. `metaPrompt.md`
   The linear 1-to-8 method chain.
2. `agentic-nested-state-machine.opml`
   The mother-structure around state space, branching, pruning, evaluation, and human collaboration.

Default precedence:

- use `metaPrompt.md` for linear step order,
- use `agentic-nested-state-machine.opml` for the mother-structure around those steps,
- and do not let downstream normalization assets silently replace either source layer.

## Core Ideas That Must Survive

### 0. One Explicit Workflow Shell

The source mother-structure is rich, but the default shell should remain explicit and small:

1. problem intake
2. semantic clarification
3. demand and constraint modeling
4. branch planning
5. evaluation and validation
6. loop or finish

This shell should not be redefined by:

- branch classes,
- shared-file coordination,
- execution supervision,
- or runtime-style orchestration imagination.

Those belong to extension planes attached around the shell, not inside it.

### 1. True Demand And True Constraints Before Solution

Do not jump from a vague request straight to a plan.

The default order should remain:

1. semantic clarification
2. intent and goal-state calibration
3. true demand and true constraint modeling
4. branch planning
5. evaluation and loopback

### 2. Demand Is A Formation Chain, Not One Sentence

The source does not stop at visible demand.

You should preserve:

- visible demand,
- latent demand,
- demand formation chain,
- the scene where the demand appears,
- and which new evidence could later rewrite the current demand framing.

### 3. EAFC Is A Real Modeling Lens

`E / A / F / C` is not decoration.

You should ask:

- `E`: which entities, actors, nodes, or components matter,
- `A`: which attributes, thresholds, costs, rights, or bottom lines matter,
- `F`: which positive or harmful functions are happening,
- `C`: which hidden conditions make those functions hold.

If a model lists actors and constraints but never makes the function and hidden-condition layer explicit, it has not inherited the source method deeply enough.

### 4. Actor-Network Roles Should Be Checked Explicitly

The source keeps asking whether there is a:

- payer,
- decision-maker,
- user,
- externality bearer,
- evaluator.

Not every task needs all five as strong roles, but the workflow should still check whether they exist.

You should also preserve:

- minimum acceptable bottom line,
- rebellion or break threshold,
- and control or evaluation power dimension.

### 5. Harmful Function And Hidden Condition Matter More Than Generic "Pain Points"

The source does not only ask what the problem is.

It asks:

- which nodes are in destructive interaction,
- what the harmful function actually is,
- which hidden condition keeps it active,
- and what compensating cost appears if the usual repair path is used.

That means the workflow should keep asking for:

- `harmful_function`
- `hidden_condition`
- `compensating_cost`
- and `authorization_boundary` when automation or delegated action is involved.

### 6. Goal And Solution Co-Evolve

If `Sg` is unstable, the source does not force a polished ideal target first.

It recommends:

- define `anti-goals`,
- define unacceptable failure states,
- identify collapse paths,
- and cut paths that move directly into those failures.

So when the goal is unstable:

- do not invent a clean target prematurely,
- write unacceptable outcomes first.

### 7. Dissipation And Crystallization Are Real Work Modes

The source has two actual modes:

- `dissipation`
  Keep assumptions open, allow temporary inconsistency, explore alternatives.
- `crystallization`
  Compress uncertainty, freeze key assumptions, harden artifacts, remove weak paths.

In practice:

- use dissipation when the problem is still unclear,
- use crystallization before artifact generation, evaluation, and finish decisions.

### 8. Evaluation Is About Structural Role, Not Only Plausibility

The source asks not only whether a path sounds reasonable, but whether it is:

- a necessary condition,
- a sufficient condition,
- or a pivot variable inside a larger combination.

This role-based evaluation should remain available whenever the user wants deeper justification.

## Default Question Set

These questions should be embedded in the skill instead of staying only in the source files.

### Semantic Clarification

- Which terms are still ambiguous?
- Which stricter replacement terms are available?
- What is the rewritten core problem?

### True Demand And True Constraints

- What is the visible demand?
- What is the real demand hypothesis?
- Which constraints are real?
- Which constraints are only inherited assumptions?
- Under which changed premise would the demand or the constraint also change?

### Actor-Network View

- Who pays?
- Who decides?
- Who uses?
- Who bears externalities?
- Who evaluates or imposes reputation pressure?

### EAFC

- What are the key `E` nodes?
- What are the key `A` thresholds?
- Which `F-` harmful functions are active?
- Which `C` hidden conditions keep them active?

### Costs And Side Effects

- What parasitic cost appears on the usual repair route?
- Which cost was only transferred rather than removed?

### Anti-Goals

- Which outcomes are unacceptable?
- Which paths lead toward those outcomes?

### Evaluation

- Is this path necessary, sufficient, or a pivot variable?
- Which blockers are still open?
- Should the round finish, revise, or loop back?

## Relation To The Current Skill

The current skill flow is structurally correct, but it becomes shallow if it loses the source questions above.

That means:

- `SKILL.md` owns the main line,
- `state-contracts.yaml` owns the hard schema,
- this file owns the source-critical questions that must keep shaping the analysis.

## Heavy Parts That Stay Out By Default

These remain in other references and should not enter the default base chain unless explicitly needed:

- full ANT network evolution,
- full resource graph / actor network / function-field / flow modeling,
- deep SAFC solving,
- USIT32,
- full TRIZ measure libraries,
- full multi-screen matrices.

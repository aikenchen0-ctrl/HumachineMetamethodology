# execution-profile-real-task-validation-plan

## Purpose

This file turns the new HMM execution-profile layer into a real-task validation plan.

It is not another architecture plane.

It exists to answer one practical question:

- do the four execution profiles actually change behavior in the intended direction during real work?

## Validation Goal

The goal is not to prove every profile is perfect.

The goal is to verify three things:

1. profile selection is recognized correctly,
2. proactive probing becomes stronger or weaker in the intended direction,
3. source authority, authorization boundaries, and derived runtime blocking still hold.

## Validation Matrix

Use this four-profile matrix:

| Profile | Expected Interaction Cadence | Expected Probe Strength | Default Use |
| --- | --- | --- | --- |
| `共创深探` | high | high | collaborative deep work |
| `共创稳推` | medium | medium | collaborative but bounded work |
| `自治深探` | low | high | proactive autonomous work |
| `自治稳推` | low | medium-low | conservative autonomous work |

## Primary Real Task

Use this repository itself as the first pressure-test task:

- `/F:/HMM-NEW/HumachineMetamethodology`

Recommended test prompt:

`用 HMM，自治深探。我要重构一个方法论型 skill，也就是 /F:/HMM-NEW/HumachineMetamethodology。先把问题结构化；如果有明显收益概率，就主动继续展开需要的高级模式、模板模式、组合优化、表示层，不要过早停下。先自行推进，除非遇到真正的关键分歧或硬阻塞。`

## Expected Behavior For The Primary Task

### Must Happen

1. HMM should enter the base mainline first.
2. It should structure the problem before trying to solve everything at once.
3. Under `自治深探`, it should proactively probe optional modes when gain is plausible.
4. It should avoid routine confirmation chatter.
5. It should still respect source alignment and runtime blocking.

### Must Not Happen

1. It must not treat execution profile as permission to bypass source authority.
2. It must not auto-activate runtime/provider/governance operations without explicit operational scope.
3. It must not silently invent new semantics in representation export.
4. It must not collapse into a shallow one-paragraph summary and stop.

## Observation Checklist

Use this checklist during each run:

### Profile Recognition

- Did the run explicitly or implicitly honor the requested profile?
- Did it avoid switching interaction cadence without reason?

### Expansion Strength

- Did it stay too shallow even though optional-mode gain was obvious?
- Did it probe advanced / template / portfolio / representation where useful?
- Did it over-expand into low-value branches?

### Boundary Integrity

- Did it keep source authority explicit?
- Did it keep runtime-derived artifacts blocked unless truly needed?
- Did it preserve mode ownership boundaries?

### Final Utility

- Did the result materially advance the task?
- Did the proactive probing help rather than distract?
- Did the run stop at a sensible point?

## Pass / Fail Heuristic

### Pass

Treat the run as a pass when all of the following hold:

1. profile behavior is recognizable,
2. proactive probing increases under `深探` compared with `稳推`,
3. boundary stop rules still hold,
4. the output clearly advances the repository task.

### Soft Fail

Treat the run as a soft fail when:

1. the profile is recognized but under-expands,
2. or it expands but does not improve task progress,
3. or it drifts into unnecessary confirmation chatter under `自治` profiles.

### Hard Fail

Treat the run as a hard fail when:

1. execution profile breaks source authority,
2. execution profile implicitly activates blocked runtime operations,
3. or profile handling becomes a new source of contract confusion.

## Follow-Up Action Map

If the run under-expands:

- adjust `mode_probe_policy`,
- adjust profile defaults,
- or lower the probe threshold for `深探` profiles.

If the run over-expands:

- tighten `probe_activation` conditions,
- strengthen evaluation pruning,
- or reduce branch budget for the affected profile.

If the run talks too much under `自治`:

- tighten `confirmation_policy`,
- reduce milestone feedback,
- or move more user-facing prompts behind blocker-only conditions.

If the run remains too quiet under `共创`:

- raise profile-specific interaction cadence,
- add profile-aware interaction-policy bindings,
- or require milestone summaries after major probe activations.

## Second-Stage Validation

After the primary repository self-refactor task, use at least one more task from a different class:

1. a problem-solving task
2. a template-construction task
3. a portfolio-comparison task

The goal is to verify that execution profiles are not overfit to self-iteration only.

Concrete execution packet:

- `references/execution-profile-non-self-comparison-plan.md`
- `references/execution-profile-non-self-comparison-scorecard-template.json`

## Closeout Rule

Do not judge execution-profile success from one run only.

A profile layer is good enough when:

1. the primary self-refactor task passes,
2. at least one non-self-iteration task also passes,
3. and no hard fail appears in boundary integrity.

# skill-capability-boundary-limit-review

## Purpose

This file records the current limit review of the `HMM` skill capability boundary after the repository has been aligned to the maintained chapter-based `metaPrompt v2`.

It does not ask:

- whether the repository could still be made richer

It asks:

- whether the repository has already reached a practical boundary where further expansion would mostly increase complexity faster than capability.

## Review Lens

The review uses four boundary classes:

1. default core
2. first-class but conditionally expanded layers
3. optional extension planes
4. out-of-core planes

This is the same boundary logic already established in:

- `references/scope-boundary.md`
- `references/skill-capability-boundary-review.md`
- `references/metaPrompt-v2-shell-review.md`

## Current Boundary State

### 1. Default Core

Current result:

- stable enough

What is now firmly inside:

- task intake and clarification
- shared symbol discipline
- `E/A/F/Cond` modeling
- `S0/Sg/IFR/C/TC/PC` analysis
- branch planning
- evaluation and loopback

These are no longer drifting.

### 2. First-Class But Conditionally Expanded Layers

Current result:

- stable enough

What is now explicitly recognized:

- retrieval and evidence writeback
- resource/system-level expansion
- candidate generation
- implementation shaping
- pluginization and self-upgrade

These are now treated as real source layers rather than vague optional folklore.

### 3. Optional Extension Planes

Current result:

- mostly bounded

What remains correctly conditional:

- deep advanced graph/flow/SAFC expansion
- template chains
- library and weighting systems
- orchestration and memory expansion
- portfolio optimization
- representation-heavy export bundles

The key boundary improvement is that these planes are no longer silently treated as default core.

### 4. Out-Of-Core Planes

Current result:

- bounded by policy

What remains out of core:

- UI / product interaction design
- execution substrate taxonomy as first-class workflow identity
- strategy / intervention wording as neutral default core language
- runtime / provider / governance operations engineering

## Remaining Capability-Boundary Risks

### Low Risk

1. Some compatibility-oriented names still contain `linear` or historical step-oriented vocabulary.
2. Some source-review and roadmap documents still mention the old source order as historical contrast.

These are not active boundary breaks anymore.

### Medium Risk

1. `state-contracts.yaml` is still very large and still carries compatibility fields from older source interpretations.
2. `SKILL.md` still compresses the chapter-based source into six runtime states, which is acceptable, but only as long as that compression remains explicit and bounded.

These are not urgent blockers, but they are the most likely places for future drift to re-enter.

## Residual Risk Checklist

Use this checklist when deciding whether to continue boundary work or stop.

| Risk Item | Current Level | Why It Matters | Recommended Action |
| --- | --- | --- | --- |
| Compatibility vocabulary still present | Low | May mislead future maintainers, but no longer drives current source authority | Only clean opportunistically |
| `state-contracts.yaml` size and legacy residue | Medium | Largest chance for future semantic drift to re-enter | Prefer narrow, evidence-backed edits only |
| Six-state shell remains compressed | Medium | Safe now, risky only if people forget it is a compression | Keep shell-compression rule explicit |
| Retrieval / pluginization drift | Low | Previously high-risk, now structurally controlled | Monitor through future real-task reviews |
| Orchestration over-activation | Low | Boundary now explicit, but large mode surface still exists | Keep optional and source-guarded |
| Advanced-mode over-expansion | Low | Could be misread as a mandatory full artifact pipeline | Keep selective expansion and finish conditions explicit |
| Variant default-order leakage | Low | Could silently turn display order into ranking semantics | Keep explicit ranking basis and default-selection basis |
| Governance runtime bleed-through | Low | Could let human-review governance slide into runtime governance operations | Keep Layer 1 versus Layer 2 reading explicit |
| Template-orchestration blur | Low | Could route pure collaboration or pruning tasks into template mode by mistake | Keep reuse semantics separate from execution orchestration |
| Representation export inflation | Low | Could turn explicit export need into unnecessary all-format or bundle-by-default behavior | Keep single-format export normal and bundle export conditional |
| Portfolio-weighting ownership blur | Low | Could let approximate portfolio comparison silently replace reusable ranking semantics | Keep portfolio consumption separate from weighting ownership |
| Execution-profile overreach | Low | Could let proactive probing be mistaken for permission to bypass boundary stop rules | Keep profiles above modes and keep runtime blocking authoritative |

### Checklist Interpretation

1. If every item is `Low` or `Medium`, and none is actively breaking runtime behavior, do not reopen broad boundary redesign.
2. If any item becomes `High`, only reopen the smallest boundary slice that directly fixes it.
3. Do not use this checklist as a reason to keep polishing wording indefinitely.

## HMM Boundary State

Treat the boundary reconstruction itself as a small state chain:

1. `B0`
   - source and shell disagree
2. `B1`
   - source and shell agree on authority but not yet on conditional expansion
3. `B2`
   - default core vs conditional expansion is explicit
4. `B3`
   - residual risks are known and bounded
5. `B4`
   - stop-rule is active; future changes require real pressure

### Current State

Current repository boundary state is best read as:

- `B4`

Reason:

1. source authority is clear
2. shell compression is explicit
3. first-class conditional layers are explicit
4. out-of-core planes are bounded
5. residual risks are known and non-blocking

### No Longer High Risk

The following high-risk issues are no longer active:

1. retrieval treated only as a side note
2. pluginization treated only as optional afterthought
3. orchestration and memory outputs silently expanding into the neutral core
4. old `metaPrompt` step order being treated as current source authority
5. advanced mode being misread as a mandatory full-depth pipeline after activation
6. variant selection inheriting default authority from list order, numbering, or phrases such as `方案一`
7. governance and feedback mode being misread as permission to activate runtime governance systems
8. template mode being misread as the default owner of shared-file collaboration or pruning semantics
9. representation mode being misread as a default all-format export layer
10. portfolio mode being misread as the default owner of reusable weighting semantics
11. execution profiles being misread as permission to bypass source authority or derived runtime blocking

## Has The Repository Reached The Practical Capability Boundary?

### Answer

Yes, in a practical sense, it is close.

More precisely:

- the repository has reached the current useful boundary for source alignment and neutral-core reconstruction,
- and further broad expansion now risks architecture sprawl more than it promises first-order capability gain.

That does **not** mean the skill is complete forever.

It means:

- the current reconstruction should stop broadening,
- and future changes should now be triggered only by real use, real drift, or real downstream consumers.

## Stop Conditions For Further Expansion

Further broad architecture expansion should stop when all of the following remain true:

1. the maintained source file stays aligned
2. the shell still explicitly states it is a compression
3. first-class source layers remain recognized as such
4. optional planes do not silently activate into the core
5. no new downstream consumer forces a missing distinction

If all five remain true, the correct next work is not more architecture expansion.

The correct next work is:

- consolidation
- validation
- commit preparation
- packaging
- distribution
- or real task-driven iteration

## Reactivation Conditions

Broad skill-boundary work should reopen only if one of these happens:

1. a real downstream consumer cannot use the current shell without a missing distinction
2. a maintained source change invalidates current compression
3. retrieval / generation / evaluation / pluginization start drifting apart again
4. runtime/provider/governance concerns are explicitly requested as real operational scope

## Reopen Decision Table

| Trigger | Reopen? | Scope |
| --- | --- | --- |
| New user asks for real runtime/provider/governance behavior | Yes | Only the relevant runtime plane |
| A real downstream consumer cannot use current shell semantics | Yes | Only the missing distinction |
| Retrieval layer stops writing back coherently | Yes | Retrieval + contract slice |
| Pluginization starts being treated as folklore again | Yes | Plugin boundary + shell wording slice |
| A reviewer merely prefers a richer architecture | No | Keep boundary frozen |
| Old naming residue exists but causes no semantic confusion | No | Defer to opportunistic cleanup |

## What Work Is Still Legitimate Now

Reaching the boundary limit does not mean “do nothing”.

It means the allowed next work changes.

Legitimate next work now includes:

1. consolidation
2. validation
3. commit preparation
4. packaging review
5. small, evidence-backed cleanup
6. real task-driven iteration

Work that is no longer legitimate by default:

1. adding new architecture planes
2. exploding the six-state shell into many runtime states
3. widening optional planes into neutral core
4. rewriting references just because they are old rather than because they are conflicting

## Final Conclusion

The repository is no longer in the phase where “keep redesigning the skill boundary” is the highest-value move.

It is now in the phase where:

- the boundary is good enough,
- the remaining work is mostly consolidation,
- and future expansion should be justified by concrete pressure, not by architectural appetite.

The most important practical conclusion is:

- boundary work is no longer on the critical path.

From this point on, any new boundary change should justify itself against the checklist and reopen table above.

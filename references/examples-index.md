# examples-index

## Purpose

This file indexes the standard multi-mode examples that demonstrate how `mode-resolution.json` and `evaluation-report.xml` should be written when more than one extension mode is active in the same round.

Use it when:

- rules alone feel too abstract,
- a new round needs to imitate an existing cross-mode interaction pattern,
- or review work needs a compact map of which example covers which architectural boundary.

## Example Set

### 1. Weighting -> Governance -> Representation

- `references/mode-resolution-example.json`
- `references/evaluation-report-example.xml`

Use when:

- automatic ranking exists,
- human override is in scope,
- and final exports must serialize the post-override state rather than the pre-override ranking.

Key interaction focus:

- `decision-weighting.json -> override-policy.json`
- `override-policy.json -> representation outputs`

Suggested execution profile:

- `自治深探`

### 2. Discovery -> Governance

- `references/mode-resolution-example-discovery-governance.json`
- `references/evaluation-report-example-discovery-governance.xml`

Use when:

- latent demand and visibility barriers are still active,
- discovery defines where feedback may re-enter,
- and governance must later own the actual review and writeback path.

Key interaction focus:

- `feedback-hooks.json -> feedback-ledger.json`
- `hypothesis-register.json -> governance review boundary`

Suggested execution profile:

- `共创稳推`

### 3. Advanced -> Representation

- `references/mode-resolution-example-advanced-representation.json`
- `references/evaluation-report-example-advanced-representation.xml`

Use when:

- advanced modeling produces the semantic source of truth,
- and representation mode must export those advanced artifacts without redefining them.

Key interaction focus:

- `actor-network.json -> sequence-diagram.mmd`
- `solution-set.json -> representation-bundle.json`

Suggested execution profile:

- `自治深探`

### 4. Template -> Orchestration

- `references/mode-resolution-example-template-orchestration.json`
- `references/evaluation-report-example-template-orchestration.xml`

Use when:

- template mode defines reusable method semantics,
- orchestration mode defines execution topology,
- and shared-file coordination plus writeback evidence are part of the same round.

Key interaction focus:

- `template-chain.json -> orchestration-plan.json`
- `shared-context-map.json -> execution-supervision.json`
- `writeback-ledger.json -> future template refinement`

Suggested execution profile:

- `自治深探`

## Reading Order

When studying an example, read in this order:

1. `mode-resolution-example*.json`
2. `evaluation-report-example*.xml`

Why:

- the mode-resolution file declares activation, precedence, handoffs, and authority,
- the evaluation-report file shows how to review whether those declarations are coherent.

### 5. Portfolio -> Weighting -> Governance

- `references/mode-resolution-example-portfolio-weighting-governance.json`
- `references/evaluation-report-example-portfolio-weighting-governance.xml`

Use when:

- portfolio mode preserves a near-optimal set,
- weighting mode ranks within that set,
- and governance mode retains final override authority over route adoption.

Key interaction focus:

- `optimization-report.json -> decision-weighting.json`
- `decision-weighting.json -> override-policy.json`

Suggested execution profile:

- `自治深探`

### 6. Representation + Governance Approval

- `references/mode-resolution-example-representation-governance-approval.json`
- `references/evaluation-report-example-representation-governance-approval.xml`

Use when:

- export payloads must be generated,
- governance must approve or gate release,
- and representation construction must stay separate from export authorization.

Key interaction focus:

- `xml-rewrite.xml -> governance-checkpoints.json`
- `governance-checkpoints.json / override-policy.json -> final export release`

Suggested execution profile:

- `共创稳推`

### 7. Template + Discovery

- `references/mode-resolution-example-template-discovery.json`
- `references/evaluation-report-example-template-discovery.xml`

Use when:

- template compression is needed before demand visibility is fully stable,
- discovery must keep latent demand and open assumptions explicit,
- and reusable method defaults must not freeze unstable demand framing.

Key interaction focus:

- `demand-visibility.json / hypothesis-register.json -> template-chain.json`
- `pruning-notes.json -> future discovery reopening`

Suggested execution profile:

- `自治深探`

### 8. Representation + Governance Multi-Reviewer Approval

- `references/mode-resolution-example-multi-reviewer-export-approval.json`
- `references/evaluation-report-example-multi-reviewer-export-approval.xml`

Use when:

- export payloads must be reviewed by more than one human role,
- the same payload must pass through an explicit approval order,
- and rejection or edit requests must map back into regeneration or re-review rules.

Key interaction focus:

- `xml-rewrite.xml / representation-bundle.json -> multi-reviewer visibility package`
- `governance-checkpoints.json -> approval order and review topology`
- `override-policy.json -> rejection reentry and regeneration rules`

Suggested execution profile:

- `共创稳推`

## Coverage Status

Current examples cover:

- weighting-heavy interaction
- discovery-heavy interaction
- advanced-analysis-heavy interaction
- execution-heavy interaction
- portfolio-heavy interaction
- approval-heavy export interaction
- multi-reviewer export approval topology
- discovery-template interaction

Current standard set currently covers the main extension-mode interaction patterns used in the existing source-aligned architecture review scope.

Still not yet covered as standard examples:

- retrieval and evidence-writeback interaction
- candidate-generation to evaluation interaction
- pluginization and self-upgrade interaction

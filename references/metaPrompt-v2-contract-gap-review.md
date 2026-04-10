# metaPrompt-v2-contract-gap-review

## Purpose

This file records the remaining contract-side gap after the repository has already synchronized:

- the maintained source file,
- typed source companions,
- and main entry references

to the new chapter-based `metaPrompt v2`.

It exists to prevent a premature, overly large contract rewrite.

## What Is Already Aligned

The following are now broadly aligned with the maintained source:

1. `references/metaPrompt.md`
2. `references/metaPrompt-step-index.*`
3. `references/core-method.md`
4. `references/source-alignment-policy.md`
5. `references/advanced-mode.md`
6. `README.md`
7. `SKILL.md`
8. `agents/openai.yaml`

## What Still Carries Old Compression Assumptions

The main remaining legacy zone is not the source itself, but the contract shell:

1. `references/state-machine.yaml`
2. `references/state-contracts.yaml`

In particular:

- the runtime shell still compresses the method into six states,
- advanced artifacts still use `derived_from_metaPrompt_step`,
- and some insertion logic still reflects the old linear step numbering as a compatibility field.

## Why This Is Not Automatically Wrong

The current six-state shell is still useful as an MVP runtime compression.

The problem is not that it compresses.

The problem is that:

- the compression is still partly expressed using legacy source labels,
- instead of explicitly saying that it is a compatibility bridge from the old numbering into the maintained chapter-based source.

## Current Contract Risk

The current risk can be summarized as:

### Low Risk

- state-machine shell order itself
- the existence of the six-state shell

### Medium Risk

- insertion metadata for advanced artifacts
- old `derived_from_metaPrompt_step` fields
- any reader assuming those numbers are still the authoritative source order

### Higher Risk

- a future maintainer treating compatibility metadata as current source truth

## Safe Second-Batch Decision

The safest second-batch contract move is not:

- rewrite the whole shell into 12 runtime chapter states

The safest move is:

1. keep the six-state shell,
2. explicitly document that it is a runtime compression of `metaPrompt v2`,
3. preserve old step-derived fields only as compatibility metadata,
4. add chapter-aware companion metadata beside them where needed.

## Recommended Contract Changes

### For `state-machine.yaml`

Add explicit notes that:

- the six-state shell is a compressed runtime view,
- chapter `4 -> 11` is the maintained source mainline,
- retrieval and pluginization are first-class source layers even if they remain compressed in the shell.

### For `state-contracts.yaml`

For advanced artifacts, prefer adding companion metadata such as:

- `derived_from_metaPrompt_chapter`
- `compatibility_legacy_step`

instead of deleting old step references immediately.

This keeps old downstream expectations from breaking while making the new source authority explicit.

## Not Recommended Yet

Do not yet:

1. explode the six-state shell into 12 runtime states;
2. rename every old compatibility field in one pass;
3. update every example JSON/XML file before the shell/contract relation is made explicit.

## Next Action

The next safe contract batch should therefore:

1. patch `state-machine.yaml` to explicitly describe the shell as chapter compression,
2. patch `state-contracts.yaml` to add chapter-aware companion metadata to advanced artifact mappings,
3. leave the rest of the contract shell intact until that change is reviewed.

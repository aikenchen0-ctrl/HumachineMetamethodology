# execution-profile-non-self-comparison-result-template

## Purpose

This file is the short report template for one completed non-self comparison round.

Use it after the matching scorecard has been filled.

## Template

### 1. Comparison Id

- `...`

### 2. Task Class

- `...`

### 3. Task Summary

- `...`

### 4. Run Order

- `autonomous_steady` first
- `autonomous_deep` second

### 5. `autonomous_steady` Summary

- profile recognition:
- expansion strength:
- evidence writeback:
- stop timing:
- boundary integrity:

### 6. `autonomous_deep` Summary

- profile recognition:
- expansion strength:
- evidence writeback:
- stop timing:
- boundary integrity:

### 7. Key Difference

- what `deep` did that `steady` did not:
- whether that difference materially improved task progress:
- whether the difference stayed inside boundary:

### 8. Boundary Integrity

- source authority:
- blocked runtime boundary:
- plugin vs MCP skill boundary:
- downstream semantic drift:

### 9. Verdict

- `pass`
- `soft_fail`
- `hard_fail`

### 10. Adjustment Recommendation

- adjust defaults:
- adjust probe policy:
- adjust confirmation policy:
- no change:

### 11. Next Move

- proceed to next run
- repeat the same run with corrected setup
- pause and repair repository policy

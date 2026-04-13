# executor-persona-boundary

## Purpose

This file separates execution substrate taxonomy from orchestration contracts.

It exists because the OPML still places ideas such as:

- multi-account agents,
- single-account agents,
- accountless but persistent agents,
- accountless limited-memory agents,
- temporary external helpers,
- and concrete execution carrier imagination such as `openclaw`

close to method and orchestration logic.

These ideas matter.
But they are not the same thing as:

- `execution_units`
- `worker_scopes`
- `reference_context_refs`
- or branch topology.

## Core Boundary

Treat execution substrate ideas as answers to:

- what kind of executor exists,
- what memory persistence it has,
- what account surface it owns,
- what execution environment it depends on,
- and what external helper class it belongs to.

Treat orchestration contracts as answers to:

- what the current execution unit should do,
- what context it may read,
- what it may write,
- how it reports progress,
- and how it is coordinated with other units.

Execution substrate taxonomy should attach below orchestration.
It must not redefine workflow shell or branch topology.

## Substrate Classes

### 1. Multi-Account Control Agent

Meaning:

- one execution substrate controls multiple external account surfaces.

This is not a workflow rule.
It is a substrate capability and risk surface.

### 2. Single-Account Control Agent

Meaning:

- one execution substrate controls exactly one account surface.

Again, this is substrate identity, not branch topology.

### 3. Accountless Persistent Agent

Meaning:

- an execution substrate has no account surface,
- but memory continuity remains meaningful across rounds.

### 4. Accountless Limited-Memory Agent

Meaning:

- no account surface,
- and continuity is bounded or disposable.

### 5. Temporary External Helper

Meaning:

- an executor is brought in as a temporary outside helper,
- with weaker continuity and weaker default ownership assumptions.

### 6. Concrete Execution Carrier

Example:

- `openclaw`

This is a carrier or runtime substrate assumption.
It should not be confused with:

- workflow state,
- branch class,
- or execution-unit identity.

## Promotion Rule

Do not promote execution substrate ideas into workflow contracts unless a real downstream consumer now depends on substrate distinction.

Promote substrate semantics only when:

- executor selection,
- capability mapping,
- account-surface policy,
- or continuity policy

actually depends on that distinction.

Otherwise:

- archive them as execution substrate references,
- and let orchestration remain substrate-agnostic.

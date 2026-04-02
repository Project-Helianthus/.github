# Developer

Helianthus is developed as a multi-repo platform. The fastest way to get
productive is to understand the repo map, the planning flow, and the proof
standard expected from every change.

## Read The Repo Map First

### Platform Core

- [`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo):
  low-level eBUS transport and protocol behavior
- [`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg):
  registry, identity, and projection model
- [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway):
  runtime, GraphQL, MCP, Portal, scans, and state machines

### Operator And Consumer Surfaces

- [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon)
- [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration)
- [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy)

### Firmware And Adapter Runtime

- [`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus):
  oracle, harness, and bridge contract work for the adapter side
- [`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic):
  deterministic PIC16F15356 firmware for eBUS adapter v3.x hardware

### Reverse Engineering And Docs

- [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer)
- [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus)
- [`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans)

## When You Must Use The Plans Repo

Start in
[`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans)
when the work is:

- cross-repo
- milestone-driven
- architecture-affecting
- protocol-affecting
- API-affecting
- large enough that it needs adversarial planning and issue decomposition

The expected flow is:

1. open a Discussion in `helianthus-execution-plans`
2. attack the plan with adversarial reviews and deep research
3. lock the plan into a `slug.locked/` directory
4. split the plan into issues and milestones in the target repos
5. rename the directory to `slug.implementing/` once code work begins
6. move to `slug.maintenance/` after the main implementation wave closes

## How To Read A Locked Plan

Each locked or active plan contains:

- `00-canonical.md`: the full canonical source
- `01-index.md`: the split index and coverage map
- `10-*.md`: self-contained execution chunks under the token budget
- `90-issue-map.md`: canonical issue mapping
- `91-milestone-map.md`: milestone mapping and ordering
- `99-status.md`: active status, blockers, and next actions

## Where To Start In The Docs

Start with
[`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus):

- architecture overview
- GraphQL contract
- MCP contract
- Portal API
- contributing and doc-gate rules

## Proof Standard

Every non-trivial claim should come with:

- the command, query, or reproduction path
- the context in which it was run
- the relevant output or artifact
- an explicit verdict

Label uncertain statements explicitly:

- `Proven`: backed by current evidence
- `Hypothesis`: plausible but not yet proven
- `Unknown`: not established yet

When possible, verification should be idempotent. If a check is not idempotent
or carries side effects, say so before running it.

## Knowledge Capture

Any reusable protocol, topology, or runtime knowledge produced by a PR must be
captured in
[`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus)
in the same cycle or in a linked docs PR that is already merged.

Docs are not an afterthought. They are part of done.

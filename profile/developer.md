# Developer

Helianthus is a multi-repository Open Energy interoperability platform. Start by
identifying the protocol-native owner, the current integration boundary, and
the evidence required for the change.

## Repository Map

### Current eBUS Platform

- [`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo):
  eBUS transport, framing, protocol primitives, and codecs
- [`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg):
  eBUS registry, identity, projection, and current eBUS semantic composition
- [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway):
  current runtime, GraphQL, MCP, Portal, scans, FSMs, and integrated mux

### Other Protocol Targets

- EEBUS: `helianthus-eebus-go`, `helianthus-eebusreg`, and
  `helianthus-docs-eebus`
- MODBUS/SunSpec: `helianthus-modbus`, `helianthus-modbusreg`, and
  `helianthus-docs-modbus`
- generic CAN/SocketCAN: `helianthus-canbus`, `helianthus-canbusreg`, and
  `helianthus-docs-canbus`
- GREE VRF CAN/UART: `helianthus-docs-gree-vrf`
- OCPP, Matter, and future energy protocols: equal architectural targets whose
  repository and maturity status must be verified before work starts

`helianthus-ship-go` and `helianthus-spine-go` are temporary upstream
forks/dependencies, not permanent Helianthus-owned products.

### Consumer Surfaces

- [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon)
- [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration)
- public GraphQL/M2M contracts exposed by `helianthus-ebusgateway`

### Planned Semantic Owner

`helianthus-semreg` is the planned future owner of the protocol-neutral
semantic core. Do not rename `helianthus-ebusreg`,
`helianthus-ebusgateway`, or another current repository in anticipation of
that work. Preserve native registries and explicit projection loss.

### Standalone And Deprecated Repositories

- `helianthus-vrc-explorer` is active, not deprecated, and remains a
  standalone/community VRC/eBUS and `ebusd` tool
- `helianthus-ebus-adapter-proxy` is deprecated; new mux work belongs in
  `helianthus-ebusgateway`
- `helianthus-tinyebus` and `helianthus-ebus-adapter-pic` are deprecated
  historical oracle, harness, firmware, and validation references

## Human-Readable Planning

Use
[`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans)
for human-readable guides and planning discussions when work needs cross-
repository dependencies, milestones, or adversarial design review.

A guide is not a lock or runtime. Do not require directory-state renames,
authorization hashes, claims, TTL/CAS state, attestations, or plan-driven
automation.

To execute or resume:

1. read the relevant merged guide from `main`
2. inspect live GitHub issues, branches, PRs, reviews, and checks
3. reconcile the guide with actual state
4. create one issue, `issue/<id>-<slug>` branch, and PR per repository in DAG
   order
5. stop at the requested boundary

Small one-repository changes can begin directly in the target repository.

## Proof And Review

Every non-trivial claim should include the command, query, capture, or scenario;
execution context and version/SHA; relevant output or artifact; and an explicit
verdict.

Use `Proven`, `Hypothesis`, and `Unknown`. Review against the exact current
HEAD, resolve valid P0-P2 findings, run applicable repository validators, and
report whether the commit and PR are actually remote. Ask before live-system,
credential, destructive, or similarly high-risk mutations.

## Knowledge Capture

Route reusable knowledge by protocol:

- eBUS -> [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus)
- EEBUS/SHIP/SPINE -> [`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus)
- MODBUS/SunSpec -> [`helianthus-docs-modbus`](https://github.com/Project-Helianthus/helianthus-docs-modbus)
- generic CAN/SocketCAN -> [`helianthus-docs-canbus`](https://github.com/Project-Helianthus/helianthus-docs-canbus)
- GREE VRF -> [`helianthus-docs-gree-vrf`](https://github.com/Project-Helianthus/helianthus-docs-gree-vrf)
- another protocol -> its corresponding public docs repository or documented
  public source until one exists
- cross-protocol semantics -> the owning semantic/platform docs, linked back to
  each native evidence source

Docs are part of done, but `helianthus-docs-ebus` is not a universal protocol
knowledge store.

# Helianthus Org-Wide Agent Guide

This is the complete default policy for human contributors and agents working
in Project Helianthus repositories. It is designed to work from any individual
repository checkout and has no workspace-root, local-path, external-skill, or
vendor-specific dependency. A repository may add stricter local instructions.

## Mission And Architecture

Helianthus is an **Open Energy interoperability platform**. eBUS, EEBUS,
MODBUS/SunSpec, CAN-based energy protocols, GREE VRF, OCPP, Matter, and future
energy protocols are equal architectural targets. Their implementation
maturity differs, but no protocol is the universal semantic source or a
second-class adapter.

Keep these boundaries explicit:

- protocol-native transport, identity, evidence, and capabilities remain owned
  by the corresponding protocol repositories
- the current eBUS runtime repository is named `helianthus-ebusgateway`
- `helianthus-ebusreg` remains the current eBUS registry and projection
  repository
- `helianthus-semreg` is the planned future owner of the protocol-neutral
  semantic core; it does not replace or rename an existing repository today
- consumers use stable public contracts and must not erase native evidence or
  silently hide projection loss

eBUS is the most mature reference implementation. That maturity is evidence for
testing shared abstractions, not authority to force other protocols into eBUS
shapes.

## Repository And Lifecycle Map

### Active eBUS platform

| Repository | Role |
| --- | --- |
| `helianthus-ebusgo` | eBUS transport, framing, protocol primitives, and reusable codecs |
| `helianthus-ebusreg` | eBUS registry, identity, projection, and current eBUS semantic composition |
| `helianthus-ebusgateway` | current gateway runtime: GraphQL, MCP, Portal, scans, FSMs, and integrated adapter mux |
| `helianthus-ha-addon` | Home Assistant add-on packaging |
| `helianthus-ha-integration` | Home Assistant consumer of the public gateway contract |
| `helianthus-docs-ebus` | eBUS-native protocol, architecture, API, and evidence documentation |

### Other active protocol targets

| Repository | Role |
| --- | --- |
| `helianthus-eebus-go` | EEBUS integration/runtime layer |
| `helianthus-eebusreg` | EEBUS-native registry and identity |
| `helianthus-docs-eebus` | EEBUS-native protocol, architecture, and evidence documentation |
| `helianthus-modbus` | vendor-neutral MODBUS transport and protocol runtime |
| `helianthus-modbusreg` | MODBUS/SunSpec and vendor profile registry with native provenance |
| `helianthus-docs-modbus` | MODBUS/SunSpec-native public documentation and evidence |
| `helianthus-canbus` | generic receive-only CAN and SocketCAN transport foundation |
| `helianthus-canbusreg` | fail-closed CAN profile registry |
| `helianthus-docs-canbus` | CAN-native public architecture, protocol, and evidence documentation |
| `helianthus-docs-gree-vrf` | GREE VRF CAN/UART-native public protocol documentation |

`helianthus-ship-go` and `helianthus-spine-go` are temporary forks used as
upstream dependencies while integration and contribution work converges. They
must not be presented as permanent Helianthus-owned products or independent
product architecture.

### Standalone community tooling

`helianthus-vrc-explorer` is not deprecated. It remains a standalone,
community-facing VRC/eBUS and `ebusd` exploration tool. The Portal replaces
only selected internal gateway workflows; it does not replace VRC Explorer as a
product.

### Deprecated historical repositories

| Repository | Status and replacement |
| --- | --- |
| `helianthus-ebus-adapter-proxy` | Deprecated; new mux work belongs in `helianthus-ebusgateway` over `helianthus-ebusgo` transports |
| `helianthus-tinyebus` | Deprecated historical oracle, harness, and bridge reference |
| `helianthus-ebus-adapter-pic` | Deprecated historical firmware, validation, and oracle reference |

Do not recommend deprecated repositories for new installations or new feature
work. Preserve their historical evidence and point readers to the active
replacement when one exists.

## Human-Readable Planning

`helianthus-execution-plans` holds human-readable Markdown guides and planning
discussions for work that benefits from cross-repository decomposition. A small
read-only YAML companion may describe objective, repositories, DAG edges,
milestones, acceptance criteria, and applicable gates.

Plans are guides, not authorization or workflow runtimes. Do not create or
require:

- locked-plan or plan-state directory renames
- prose or chunk hashes as authority
- attestations, claims, TTL/CAS workflows, leases, or one-shot tokens
- executable pinning or plan-driven cross-repository automation
- a custom canonical execution state that competes with GitHub

For execution or resume:

1. read the relevant merged guide from `main`
2. inspect current GitHub issues, branches, PRs, reviews, and checks
3. reconcile the guide with that live state
4. create one issue, `issue/<id>-<slug>` branch, and PR per repository in DAG
   order
5. stop at the operator-requested repository, PR, merge, or sensitive-mutation
   boundary

The operator's request is sufficient for ordinary issue, branch, code,
documentation, test, and PR work. Ask again at action time before credentials,
real installations, production or live-device mutations, destructive actions,
or similarly high-risk changes.

## Development And Review

- Keep at most one active implementation issue and PR per repository for the
  same workstream.
- Use TDD where it adds evidence for behavior, defects, protocol handling,
  persistence, and state machines. Documentation-only changes are exempt.
- Run every applicable repository CI, build, test, lint, conformance, and smoke
  gate. Transport/protocol changes must preserve the repository's transport
  matrix.
- Target validation effort at roughly 25-30% of development effort, increasing
  it for protocol safety, live systems, and other high-risk work.
- Review is blocker-driven and exact-HEAD. Resolve valid P0-P2 findings, then
  run a fresh review against the current HEAD. P3/P4 findings are triaged but
  are nonblocking.
- Merge only when explicitly requested, all applicable gates are green, and the
  exact PR HEAD has no blocking findings. Use squash-and-merge.
- Never infer a new phase or post-merge effect from completion of the previous
  phase.

## Evidence Standard

Every material claim should give another reviewer a practical falsification
path:

1. exact command, query, capture, scenario, or reproduction
2. execution context and relevant version/SHA
3. relevant output or artifact
4. explicit verdict

Use `Proven`, `Hypothesis`, and `Unknown` consistently. Preserve
candidate-versus-supported status, native protocol identity, raw evidence,
units, timestamps, and explicit projection loss.

## Documentation And Knowledge Routing

Documentation follows protocol ownership:

| Knowledge | Canonical destination |
| --- | --- |
| eBUS wire behavior, devices, mappings, or eBUS-facing APIs | `helianthus-docs-ebus` |
| EEBUS/SHIP/SPINE behavior, identities, or evidence | `helianthus-docs-eebus` |
| MODBUS/SunSpec behavior, profiles, devices, or evidence | `helianthus-docs-modbus` |
| Generic CAN/SocketCAN behavior and profiles | `helianthus-docs-canbus` |
| GREE VRF CAN/UART behavior or evidence | `helianthus-docs-gree-vrf` |
| Another protocol's native behavior | that protocol's corresponding public docs repository or documented public source until one exists |
| Cross-protocol semantic contract | the owning semantic/platform documentation, with links to each protocol-native evidence source |

Do not route all protocol knowledge to `helianthus-docs-ebus`. Reverse-
engineered knowledge must remain public and must identify its native evidence,
provenance, uncertainty, and license boundary.

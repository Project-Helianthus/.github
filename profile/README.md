# Project Helianthus

Helianthus is an **Open Energy interoperability platform**: protocol-native
evidence and capabilities flow into explicit semantic projections and stable
consumer APIs without being flattened into one favored bus.

eBUS, EEBUS, MODBUS/SunSpec, CAN-based energy protocols, GREE VRF, OCPP,
Matter, and future energy protocols are equal architectural targets. Their
maturity differs. eBUS is currently the most mature production track and the
reference implementation for testing shared abstractions; it is not the
universal semantic owner.

## Current Direction

### eBUS

The active eBUS stack is
[`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo),
[`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg),
and the current gateway runtime,
[`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway).
The gateway hosts GraphQL, MCP, Portal, scans, state machines, and the integrated
adapter mux.

### EEBUS

EEBUS support is developed through
[`helianthus-eebus-go`](https://github.com/Project-Helianthus/helianthus-eebus-go),
[`helianthus-eebusreg`](https://github.com/Project-Helianthus/helianthus-eebusreg),
and
[`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus).
[`helianthus-ship-go`](https://github.com/Project-Helianthus/helianthus-ship-go)
and
[`helianthus-spine-go`](https://github.com/Project-Helianthus/helianthus-spine-go)
are temporary forks used as upstream dependencies while integration and
contribution work converges. They are not permanent Helianthus-owned products.

### MODBUS And SunSpec

Read-only MODBUS and SunSpec support is developed through the vendor-neutral
[`helianthus-modbus`](https://github.com/Project-Helianthus/helianthus-modbus)
runtime and
[`helianthus-modbusreg`](https://github.com/Project-Helianthus/helianthus-modbusreg)
profile registry. Fronius, Huawei, Growatt, and Tesla Wall Connector Gen 3
FC100-FC102 are target/device lanes with separate evidence and maturity; a
declared target is not the same as validated support.

### CAN And GREE VRF

[`helianthus-canbus`](https://github.com/Project-Helianthus/helianthus-canbus)
and
[`helianthus-canbusreg`](https://github.com/Project-Helianthus/helianthus-canbusreg)
provide the generic CAN/SocketCAN foundation and fail-closed profile registry.
GREE VRF protocol evidence is kept in
[`helianthus-docs-gree-vrf`](https://github.com/Project-Helianthus/helianthus-docs-gree-vrf).
Transport availability, a documented protocol, and validated device support are
reported separately.

### Protocol-Neutral Semantics

`helianthus-semreg` is the planned future owner of the protocol-neutral
semantic core. It is not a rename of `helianthus-ebusreg` or
`helianthus-ebusgateway`, and no current repository should be renamed in
advance of that future work. Native registries retain protocol identity,
provenance, capabilities, and projection-loss information.

The stable public GraphQL/M2M contract is the consumer boundary. Downstream
bindings must consume that contract rather than private gateway or registry
internals.

## Lifecycle Clarity

- [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer)
  is **not deprecated**. It remains a standalone, community-facing VRC/eBUS and
  `ebusd` exploration tool. Portal replaces only selected internal gateway
  workflows.
- [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy)
  is deprecated; new mux work belongs in `helianthus-ebusgateway` over
  `helianthus-ebusgo` transports.
- [`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus)
  is a deprecated historical oracle, harness, and bridge reference.
- [`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic)
  is a deprecated historical firmware, validation, and oracle reference.

## Choose Your Path

- [Curious user](./curious-user.md): run the gateway and Home Assistant surfaces
  without adopting deprecated topology components.
- [Protocol hacker](./protocol-hacker.md): inspect native evidence with Portal,
  MCP, VRC Explorer, and protocol-specific tools.
- [Developer](./developer.md): contribute across current protocol repositories,
  future semantic boundaries, docs, and human-readable execution guides.

## Repository Map

| Repository | Status and purpose |
| --- | --- |
| [`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo) | Active eBUS transport, framing, protocol primitives, and codecs |
| [`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg) | Active eBUS registry, identity, projection, and current eBUS semantic composition |
| [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway) | Current gateway runtime, APIs, Portal, state machines, and integrated mux |
| [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon) | Home Assistant add-on packaging |
| [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration) | Home Assistant integration consuming the public gateway contract |
| [`helianthus-eebus-go`](https://github.com/Project-Helianthus/helianthus-eebus-go) | Active EEBUS integration/runtime layer |
| [`helianthus-eebusreg`](https://github.com/Project-Helianthus/helianthus-eebusreg) | Active EEBUS-native registry and identity |
| [`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus) | EEBUS-native public documentation and evidence |
| [`helianthus-ship-go`](https://github.com/Project-Helianthus/helianthus-ship-go) | Temporary upstream SHIP fork/dependency, not a permanent Helianthus product |
| [`helianthus-spine-go`](https://github.com/Project-Helianthus/helianthus-spine-go) | Temporary upstream SPINE fork/dependency, not a permanent Helianthus product |
| [`helianthus-modbus`](https://github.com/Project-Helianthus/helianthus-modbus) | Active vendor-neutral MODBUS transport/runtime |
| [`helianthus-modbusreg`](https://github.com/Project-Helianthus/helianthus-modbusreg) | Active MODBUS/SunSpec and vendor profile registry |
| [`helianthus-docs-modbus`](https://github.com/Project-Helianthus/helianthus-docs-modbus) | MODBUS/SunSpec-native public documentation and evidence |
| [`helianthus-canbus`](https://github.com/Project-Helianthus/helianthus-canbus) | Active generic receive-only CAN/SocketCAN transport foundation |
| [`helianthus-canbusreg`](https://github.com/Project-Helianthus/helianthus-canbusreg) | Active fail-closed CAN profile registry |
| [`helianthus-docs-canbus`](https://github.com/Project-Helianthus/helianthus-docs-canbus) | CAN-native public architecture, protocol, and evidence docs |
| [`helianthus-docs-gree-vrf`](https://github.com/Project-Helianthus/helianthus-docs-gree-vrf) | GREE VRF CAN/UART-native public protocol docs |
| `helianthus-semreg` | Planned future protocol-neutral semantic owner; no current-repository rename |
| [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer) | Active standalone/community VRC/eBUS and `ebusd` exploration tool |
| [`helianthus-ebus-wireshark`](https://github.com/Project-Helianthus/helianthus-ebus-wireshark) | eBUS Wireshark dissector |
| [`helianthus-ebus-extcap`](https://github.com/Project-Helianthus/helianthus-ebus-extcap) | passive ENS capture integration |
| [`helianthus-ebus-vdev`](https://github.com/Project-Helianthus/helianthus-ebus-vdev) | virtual eBUS device emulator |
| [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy) | Deprecated historical proxy; superseded by the integrated gateway mux |
| [`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus) | Deprecated historical oracle/harness/bridge reference |
| [`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic) | Deprecated historical firmware/validation/oracle reference |
| [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus) | eBUS-native protocol, architecture, API, and evidence docs |
| [`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans) | Human-readable execution guides, planning discussions, and optional structural metadata |

## Planning And Knowledge

Execution guides are human-readable aids. To execute or resume one, read the
merged guide from `main`, inspect live GitHub issues/branches/PRs/checks, and
reconcile actual state. A guide does not lock, authorize, rename itself, or run
workflows in code repositories.

Knowledge goes to the corresponding protocol docs: eBUS to
[`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus),
EEBUS/SHIP/SPINE to
[`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus),
MODBUS/SunSpec to
[`helianthus-docs-modbus`](https://github.com/Project-Helianthus/helianthus-docs-modbus),
generic CAN/SocketCAN to
[`helianthus-docs-canbus`](https://github.com/Project-Helianthus/helianthus-docs-canbus),
and GREE VRF to
[`helianthus-docs-gree-vrf`](https://github.com/Project-Helianthus/helianthus-docs-gree-vrf).
Other protocols use their own public docs lane. Cross-protocol semantics must
link back to each protocol-native evidence source.

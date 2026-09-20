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
The native repositories retain eBUS identity and evidence. The gateway currently
composes enabled drivers and hosts scoped GraphQL, MCP, Portal, metrics, scans,
state machines, and accepted read-only contribution slices. Its
[universal public lifecycle/configuration service is still in progress](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/5eb53465e88d254455251203e2dc30f813541bba/docs/architecture/runtime-driver-provider-contract-v1.md).

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
Public GREE VRF receive-only replay evidence is currently anchored in
[`helianthus-canbusreg` at `233fd48`](https://github.com/Project-Helianthus/helianthus-canbusreg/commit/233fd48136fa0e5024d87f3676c99990ef0d94b6).
The intended standalone `helianthus-docs-gree-vrf` destination was not publicly
available at the PUBLIC-03 inspection baseline, so no public docs-repository
claim is made here.
Transport availability, a documented protocol, and validated device support are
reported separately.

### Protocol-Neutral Semantics

[`helianthus-semreg`](https://github.com/Project-Helianthus/helianthus-semreg/blob/089ed6ae9004cfba8aff27f1e54d579aeccc0b4c/README.md)
is the current separate canonical owner of promoted protocol-neutral semantic
state. Its accepted v1 kernel and capability packs own versioned publication,
evaluation, projection, lifecycle, provenance, quality, freshness, and explicit
projection-loss contracts. Native registries still own protocol identity,
qualification, decoding, and raw evidence. The Gateway composes those owners
and exposes enabled contributions through declared MCP, GraphQL, Portal,
Prometheus, and other consumer bindings; it does not own the canonical semantic
types.

Current public evidence is deliberately narrower than the complete 0.7 target:

| Surface | Evidence-backed status |
| --- | --- |
| SemReg core and packs | Implemented and offline-tested at [`089ed6a`](https://github.com/Project-Helianthus/helianthus-semreg/commit/089ed6ae9004cfba8aff27f1e54d579aeccc0b4c); this does not claim physical qualification. |
| Gateway MCP, M2M GraphQL, and Portal | PV consumes one SemReg publication in [Gateway PR #956](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/956); Storage and EVSE have accepted domain paths in [PR #959](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/959) and [PR #962](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/962). The generic read-only Portal contribution catalog is implemented in [PR #984](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/984). Other 0.7 domains and complete Portal integration remain in progress. |
| Prometheus | Bounded PV and Storage output is implemented in [PR #964](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/964), EVSE in [PR #967](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/967), and Gateway-owned Modbus/EEBUS runtime status in [PR #978](https://github.com/Project-Helianthus/helianthus-ebusgateway/pull/978). These are offline-validated software paths, not device qualification. |
| Home Assistant | Read-only SemReg consumers are implemented for PV, Storage, and EVSE in [PR #257](https://github.com/Project-Helianthus/helianthus-ha-integration/pull/257), [PR #261](https://github.com/Project-Helianthus/helianthus-ha-integration/pull/261), and [PR #263](https://github.com/Project-Helianthus/helianthus-ha-integration/pull/263). A merged integration does not prove that a packaged add-on or an installed system contains it. |
| EEBUS and Matter output bindings | Both are public 0.7 software scope and do not depend on private hardware. EEBUS-native runtime/read surfaces exist, but the protocol-neutral EEBUS output binding remains in progress. SemReg records EEBUS as pending exact standard mapping and Matter as input-only; the accepted Gateway baseline explicitly has [no composed Matter output binding](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/5eb53465e88d254455251203e2dc30f813541bba/docs/architecture/runtime-driver-provider-contract-v1.md#current-operation-inventory-at-the-pinned-baseline). No conformance or physical-validation claim is made. |

`Implemented` here means present in the linked public revision with repository
validation. It does not mean packaged, installed, certified, or physically
verified. In-progress and unknown capabilities remain separate from accepted
software evidence.

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

- [First contribution](./first-contribution.md): reproduce one deterministic
  read-only SunSpec profile path, see its fail-closed negative case, and find
  the owning repository for each layer before proposing a change.
- [Software maturity matrix](./maturity-matrix.md): compare exact public
  implementation, semantic, consumer, package, offline-test, and physical
  evidence without treating one state as proof of another.
- [Anonymous reproducibility](./reproducibility.md): clone, resolve public
  modules, build, and run the Gateway's offline checks without organization
  credentials or sibling checkouts.
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
| [`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg) | Active eBUS-native registry, identity, qualification, and projection |
| [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway) | Current runtime composition, scoped public APIs, Portal, metrics, and integrated mux; universal public lifecycle/configuration remains in progress |
| [`helianthus-semreg`](https://github.com/Project-Helianthus/helianthus-semreg) | Current canonical protocol-neutral semantic contracts, kernel, capability packs, and fixtures |
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
| `helianthus-docs-gree-vrf` | Intended GREE VRF docs owner; public repository availability **UNKNOWN** at the PUBLIC-03 baseline |
| [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer) | Active standalone/community VRC/eBUS and `ebusd` exploration tool |
| [`helianthus-ebus-wireshark`](https://github.com/Project-Helianthus/helianthus-ebus-wireshark) | eBUS Wireshark dissector |
| [`helianthus-ebus-extcap`](https://github.com/Project-Helianthus/helianthus-ebus-extcap) | passive ENS capture integration |
| [`helianthus-ebus-vdev`](https://github.com/Project-Helianthus/helianthus-ebus-vdev) | virtual eBUS device emulator |
| [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy) | Deprecated historical proxy; superseded by the integrated gateway mux |
| [`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus) | Deprecated historical oracle/harness/bridge reference |
| [`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic) | Deprecated historical firmware/validation/oracle reference |
| [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus) | eBUS-native protocol, architecture, API, and evidence docs |
| [`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans) | Human-readable execution guides, planning discussions, and optional structural metadata |

## Licensing And Third-Party Boundaries

Matter and EEBUS software outputs and bindings are public 0.7 software scope;
they do not depend on private Helianthus hardware. Public software scope remains
separate from certification, conformance and trademark programs, vendor
approval, patent rights, and physical validation.

Read [the licensing and contribution boundary](../LICENSING.md) and the
[source-linked dependency license inventory](../THIRD_PARTY.md). Those documents
do not change repository licenses or grant rights in third-party material.

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
and GREE VRF to the intended `helianthus-docs-gree-vrf` owner once that public
repository is available.
Other protocols use their own public docs lane. Cross-protocol semantics must
link back to each protocol-native evidence source.

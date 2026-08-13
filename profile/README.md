# Project Helianthus

Helianthus is an open Energy gateway platform built around a protocol-agnostic
semantic core. It separates transport, protocol decoding, registry/identity,
semantic modeling, and consumer APIs so that new protocol adapters can plug
into the same platform without forking the rest of the stack.

Today, eBUS is the active production track and the reference implementation.
eeBUS support is being built as a native
[SHIP](https://github.com/Project-Helianthus/helianthus-ship-go) /
[SPINE](https://github.com/Project-Helianthus/helianthus-spine-go) stack, with
[`helianthus-eebus-go`](https://github.com/Project-Helianthus/helianthus-eebus-go)
and [`helianthus-eebusreg`](https://github.com/Project-Helianthus/helianthus-eebusreg),
and its public knowledge base in
[`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus).
For Vaillant hardware, eBUS and eeBUS can coexist without duplicating device
identities: eBUS exposes substantially richer raw data, while eeBUS more closely
matches the user-facing myVaillant view.

Read-only MODBUS support is being developed through the vendor-neutral
[`helianthus-modbus`](https://github.com/Project-Helianthus/helianthus-modbus)
runtime and multi-vendor
[`helianthus-modbusreg`](https://github.com/Project-Helianthus/helianthus-modbusreg)
profile registry. The immediate sequence is Fronius/SunSpec solar-inverter
support, then Huawei and Growatt inverter/BESS profiles. The
[`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway)
performs upstream raw/profile MCP composition; canonical promotion then produces
the public GraphQL/M2M contract. A separate private eeBUS output binding, when
introduced, consumes that public contract downstream rather than gateway or
registry internals.
The next planned target is Tesla Wall Connector Gen 3 FC100-FC102 MODBUS
support. It does not yet have a public target repository or canonical planning
artifact.
Additional profiles can be contributed through the same shared runtime and
registry boundaries.
The wider goal is multi-protocol HVAC, EVSE, Solar Inverter, BESS interoperability:
one semantic model, multiple buses, multiple operator surfaces, and reusable
tooling for reverse engineering and documentation.

The eBUS edge firmware tracks are being deprecated:
[`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus)
(adapter oracle, harness, and bridge) and
[`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic)
(PIC16F15356 firmware for eBUS adapter v3.x). The legacy
[`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy)
is also being deprecated: its role is now integrated into the gateway's eBUS
transport path/runtime mux in
[`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway),
which wraps the reusable transports in
[`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo).

## Choose Your Path

- [Curious user](./curious-user.md): you want Helianthus running in Home
  Assistant with the minimum number of moving parts.
- [Protocol hacker](./protocol-hacker.md): you want to inspect registers, use
  the MCP surface, script investigations, or work with eBUS tooling directly.
- [Developer](./developer.md): you want to contribute code, docs, execution
  plans, and proof-backed changes across the Helianthus repos.

## Repository Map

| Repository | Purpose |
| --- | --- |
| [`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo) | eBUS transport, framing, protocol primitives, and low-level reusable codecs |
| [`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg) | registry, identity, projection model, and semantic plumbing |
| [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway) | main runtime: GraphQL, MCP, Portal, scans, FSMs, API edge, and the integrated eBUS transport mux |
| [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon) | Home Assistant add-on packaging for the gateway |
| [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration) | Home Assistant custom integration consuming Helianthus GraphQL |
| [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy) | deprecated shared proxy; superseded by the integrated gateway eBUS transport mux |
| [`helianthus-ship-go`](https://github.com/Project-Helianthus/helianthus-ship-go) | native eeBUS SHIP protocol implementation in Go |
| [`helianthus-spine-go`](https://github.com/Project-Helianthus/helianthus-spine-go) | native eeBUS SPINE protocol implementation in Go |
| [`helianthus-eebus-go`](https://github.com/Project-Helianthus/helianthus-eebus-go) | eeBUS protocol implementation in Go |
| [`helianthus-eebusreg`](https://github.com/Project-Helianthus/helianthus-eebusreg) | eeBUS registry and runtime integration layer |
| [`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus) | canonical public documentation for eeBUS architecture, protocol knowledge, and evidence |
| [`helianthus-modbus`](https://github.com/Project-Helianthus/helianthus-modbus) | vendor-neutral, read-only MODBUS protocol and transport runtime |
| [`helianthus-modbusreg`](https://github.com/Project-Helianthus/helianthus-modbusreg) | multi-vendor MODBUS profile registry for detection, observations, and provenance |
| [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer) | VRC-focused eBUS exploration tool useful to the wider eBUS and `ebusd` community |
| [`helianthus-ebus-wireshark`](https://github.com/Project-Helianthus/helianthus-ebus-wireshark) | Wireshark Lua dissector for passive ENS and eBUS capture streams |
| [`helianthus-ebus-extcap`](https://github.com/Project-Helianthus/helianthus-ebus-extcap) | Wireshark extcap client for passive ENS capture through the adapter path |
| [`helianthus-ebus-vdev`](https://github.com/Project-Helianthus/helianthus-ebus-vdev) | virtual eBUS device emulator for platform development and testing |
| [`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus) | deprecated adapter oracle, harness, and TinyGo/ESP8266 bridge track |
| [`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic) | deprecated PIC16F15356 firmware for eBUS adapter v3.x hardware |
| [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus) | canonical public docs for architecture, protocol knowledge, and API behavior. Key protocol refs: [B524 spec](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/protocols/vaillant/ebus-vaillant-B524.md), [B524 register map](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/protocols/vaillant/ebus-vaillant-B524-register-map.md), [Vaillant protocols](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/protocols/vaillant/ebus-vaillant.md) |
| [`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans) | human-readable execution guides, planning discussions, and structural plan metadata; it does not authorize or automate code-repository work |

## Planning And Execution

Cross-repo, milestone, architecture, protocol, and API work is planned in
[`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans).
That repository holds the human-readable guides and discussions that define
scope, dependencies, and applicable gates. Execution reconciles the merged
guide with current GitHub state; the guide itself neither authorizes nor
automates work in code repositories.

# Project Helianthus

Helianthus is an open HVAC gateway platform built around a protocol-agnostic
semantic core. It separates transport, protocol decoding, registry/identity,
semantic modeling, and consumer APIs so that new protocol adapters can plug
into the same platform without forking the rest of the stack.

Today, eBUS is the active production track and the reference implementation.
eeBUS has recently been added from the original specs. For Vaillant hardware
both can coexist and there is a clear match between the eBUS reads and eeBUS,
so no device duplicates are present. eBUS has a lot more data, while eeBUS
resembles the myVaillant user-facing information. A MODBUS driver is also
being brought up, with initial support for Fronius Solar inverters, that will
also be exposed by the new eeBUS backend to the Vaillant system, followed by
Huawei & Growatt Inverters and BESS, then the next target will be the Tesla
Wall Charger Gen3 FC100-FC102 MODBUS support (something that nobody in the
OSS arena offers), others can easily be added by the community, following
these examples.
The wider goal is multi-protocol HVAC, EVSE, Solar Inverter, BESS interoperability:
one semantic model, multiple buses, multiple operator surfaces, and reusable
ooling for reverse engineering and documentation.

The platform now also includes an adapter-firmware track for the eBUS edge:
[`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus)
provides the oracle, harness, and bridge side of the adapter contract, while
[`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic)
hosts the deterministic PIC16F15356 firmware for eBUS adapter v3.x hardware.
Both tinyebus and pic projects are being deprecated.

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
| [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway) | main runtime: GraphQL, MCP, Portal, scans, FSMs, and API edge |
| [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon) | Home Assistant add-on packaging for the gateway |
| [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration) | Home Assistant custom integration consuming Helianthus GraphQL |
| [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy) | shared proxy for single-client adapters and mixed client topologies |
| [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer) | VRC-focused eBUS exploration tool useful to the wider eBUS and `ebusd` community |
| [`helianthus-tinyebus`](https://github.com/Project-Helianthus/helianthus-tinyebus) | adapter oracle, harness, and TinyGo/ESP8266 bridge track for deterministic contract validation |
| [`helianthus-ebus-adapter-pic`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-pic) | deterministic PIC16F15356 firmware for eBUS adapter v3.x hardware |
| [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus) | canonical public docs for architecture, protocol knowledge, and API behavior. Key protocol refs: [B524 spec](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/protocols/ebus-vaillant-B524.md), [B524 register map](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/protocols/ebus-vaillant-B524-register-map.md), [Vaillant protocols](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/protocols/ebus-vaillant.md) |
| [`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans) | canonical locked execution plans and adversarial planning discussions |

## Planning And Execution

Cross-repo, milestone, architecture, protocol, and API work is planned in
[`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans).
That repository is where discussions are attacked, refined, and locked before
they are split into implementation issues across the code repos.

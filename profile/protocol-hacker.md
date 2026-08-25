# Protocol Hacker

Helianthus exposes raw protocol evidence alongside semantic projections. eBUS,
EEBUS, MODBUS/SunSpec, CAN-based integrations, GREE VRF, and future Open Energy
protocols are equal architectural targets even though their tools and maturity
differ.

## Gateway Portal

The Portal in
[`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway)
is the gateway-native UI for projection, timeline, provenance, snapshot, and
issue-bundle workflows.

Use it when an investigation depends on live gateway state or needs an
exportable gateway evidence bundle. Portal replaces selected internal gateway
workflows only.

eBUS Portal reference:
[`api/portal.md`](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/api/portal.md)

## MCP

The gateway MCP surface is the preferred scriptable path for reproducible
reads, raw/profile inspection, rapid protocol-native prototyping, and later API
parity. Preserve raw observations and provenance beside semantic output.

eBUS MCP reference:
[`api/mcp.md`](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/api/mcp.md)

## VRC Explorer

[`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer)
is **not deprecated**. It remains a standalone, community-facing VRC/eBUS and
`ebusd` exploration tool.

Use it for focused B524 discovery, operator debugging, community workflows, or
investigations that do not need the Helianthus gateway. A similar Portal
capability does not turn VRC Explorer into a fallback or legacy-only product.

## Protocol-Native Tooling

- eBUS transport and framing: `helianthus-ebusgo`
- EEBUS integration and registry: `helianthus-eebus-go` and
  `helianthus-eebusreg`
- MODBUS/SunSpec transport and profiles: `helianthus-modbus` and
  `helianthus-modbusreg`
- generic CAN/SocketCAN transport and profiles: `helianthus-canbus` and
  `helianthus-canbusreg`
- GREE VRF protocol evidence: `helianthus-docs-gree-vrf`

`helianthus-ship-go` and `helianthus-spine-go` are temporary upstream
forks/dependencies used by the EEBUS work. Treat them as integration surfaces,
not permanent Helianthus-owned products.

`helianthus-ebus-adapter-proxy`, `helianthus-tinyebus`, and
`helianthus-ebus-adapter-pic` are deprecated. They may be consulted as
historical topology, oracle, harness, firmware, or validation evidence, but new
features belong in the active repositories.

## Evidence And Knowledge Capture

Keep wire/native evidence distinct from implementation behavior. Record exact
captures, addresses, services/registers, payloads, device context, versions,
units, timestamps, and uncertainty where applicable. Use `Proven`,
`Hypothesis`, and `Unknown`.

Publish reusable knowledge in the corresponding protocol docs:

- eBUS -> [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus)
- EEBUS/SHIP/SPINE -> [`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus)
- MODBUS/SunSpec -> [`helianthus-docs-modbus`](https://github.com/Project-Helianthus/helianthus-docs-modbus)
- generic CAN/SocketCAN -> [`helianthus-docs-canbus`](https://github.com/Project-Helianthus/helianthus-docs-canbus)
- GREE VRF -> [`helianthus-docs-gree-vrf`](https://github.com/Project-Helianthus/helianthus-docs-gree-vrf)
- other protocols -> their own public docs repository or documented public
  source until one exists

Do not place every protocol's knowledge in `helianthus-docs-ebus`.

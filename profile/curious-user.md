# Curious User

If you mainly want Helianthus in Home Assistant, use the active gateway path and
avoid deprecated topology components.

## Recommended Adoption Path

1. Start with
   [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon).
   It packages the current
   [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway)
   runtime and exposes GraphQL, MCP, and Portal.
2. Configure only the protocol path supported for your equipment and current
   release. eBUS is the most mature track; EEBUS, MODBUS/SunSpec, CAN-based
   integrations, and GREE VRF have their own native runtimes, registries or
   documentation, evidence, and release maturity.
3. Add
   [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration)
   when you want native Home Assistant devices and entities backed by the stable
   public gateway contract.

## Topology Note

[`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy)
is deprecated. Do not add it to a new installation. Adapter sharing and mux
behavior for new work belongs in `helianthus-ebusgateway`, using reusable
`helianthus-ebusgo` transports.

`helianthus-tinyebus` and `helianthus-ebus-adapter-pic` are also deprecated
historical references, not current installation choices.

## Minimal Mental Model

- `helianthus-ha-addon`: packages the current gateway runtime
- `helianthus-ebusgateway`: active GraphQL, MCP, Portal, and runtime edge
- protocol runtime/registry: preserves native identity and evidence
- `helianthus-ha-integration`: stable Home Assistant consumer

VRC Explorer is separate from this installation path and is not deprecated. It
remains a standalone, community-facing VRC/eBUS and `ebusd` exploration tool.

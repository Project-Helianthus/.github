# Curious User

If you mainly want Helianthus running in Home Assistant, keep the path simple:

1. Start with the
   [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon).
2. Add the
   [`helianthus-ebus-adapter-proxy`](https://github.com/Project-Helianthus/helianthus-ebus-adapter-proxy)
   only when your adapter or topology requires it.
3. Add the
   [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration)
   when you want native Home Assistant entities and a cleaner HA-side consumer
   model.

## Recommended Adoption Path

### 1. Install The Add-on First

The Home Assistant add-on is the default operator entry point. It packages the
gateway runtime and exposes:

- GraphQL at `/graphql`
- MCP at `/mcp`
- the Portal UI under `/portal`

Start here if you want a working system before you care about internal topology.

### 2. Add The Proxy Only When The Topology Needs It

Use the adapter proxy when:

- your adapter is single-client and must be shared
- you want Helianthus and `ebusd` to coexist
- you need ENH or ENS fan-out to multiple northbound clients
- you are testing mixed direct and proxy paths

If you do not have one of those constraints, do not start with the proxy.

### 3. Add The HA Integration For Native Entities

The custom integration consumes the Helianthus GraphQL surface and maps it to
Home Assistant entities such as climate, domestic hot water, diagnostics, and
energy data.

Use it when you want:

- native devices and entities in Home Assistant
- Home Assistant automations built on Helianthus data
- a stable consumer surface without operating directly against GraphQL or MCP

## Minimal Mental Model

- `helianthus-ha-addon`: the gateway packaged for Home Assistant
- `helianthus-ebus-adapter-proxy`: optional topology helper
- `helianthus-ha-integration`: native Home Assistant consumer

If you are unsure, begin with the add-on alone and add the other pieces only
after you know why you need them.

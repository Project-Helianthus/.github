# Project Helianthus

Helianthus is an open-source energy interoperability platform. It connects
equipment that speaks different protocols, preserves the facts reported by each
protocol, and exposes qualified energy data through consistent APIs and tools.

The goal is practical: make heating, solar, storage, EV charging, and other
energy systems easier to inspect and integrate without pretending that every
device or protocol behaves the same way.

## What Helianthus Provides

- Protocol integrations for eBUS, EEBUS, MODBUS/SunSpec, CAN-based energy
  devices, and GREE VRF.
- A protocol-neutral semantic registry for qualified power, energy, storage,
  EVSE, thermal, and infrastructure data.
- A gateway with MCP, GraphQL, Portal, and Prometheus surfaces.
- Home Assistant packaging and integration work.
- Public protocol documentation, replay fixtures, qualification rules, and
  contributor tools.
- Matter and EEBUS interface work that advances only where the available
  protocol and mapping evidence supports it.

eBUS is the most mature end-to-end path today. Other protocol families range
from implemented and offline-tested foundations to evidence-blocked candidates.
Exact device support, packaging, and physical validation vary by capability;
the [software maturity matrix](./maturity-matrix.md) records those distinctions.

## How It Fits Together

```text
protocol transport and raw evidence
  -> protocol and profile registries
  -> shared energy semantics
  -> gateway APIs and operator tools
  -> Home Assistant and other consumers
```

Native protocol repositories own framing, identity, qualification, and raw
observations. [`helianthus-semreg`](https://github.com/Project-Helianthus/helianthus-semreg)
owns promoted protocol-neutral energy state. The
[`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway)
composes those layers and serves the public interfaces. This keeps source
evidence available and makes any loss in projection visible.

## Start Here

- **Run and explore:** [Curious user guide](./curious-user.md)
- **Make a first contribution:** [Follow one read-only profile](./first-contribution.md)
- **Reproduce the public build:** [Anonymous reproducibility record](./reproducibility.md)
- **Work with protocol evidence:** [Protocol hacker guide](./protocol-hacker.md)
- **Contribute across repositories:** [Developer guide](./developer.md) and
  [contribution policy](../CONTRIBUTING.md)
- **Check exact maturity:** [Software maturity matrix](./maturity-matrix.md)

## Project Map

| Area | Main repositories |
| --- | --- |
| Gateway and operator surfaces | [`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway) |
| Shared energy semantics | [`helianthus-semreg`](https://github.com/Project-Helianthus/helianthus-semreg) |
| eBUS | [`helianthus-ebusgo`](https://github.com/Project-Helianthus/helianthus-ebusgo), [`helianthus-ebusreg`](https://github.com/Project-Helianthus/helianthus-ebusreg), [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus) |
| EEBUS | [`helianthus-eebus-go`](https://github.com/Project-Helianthus/helianthus-eebus-go), [`helianthus-eebusreg`](https://github.com/Project-Helianthus/helianthus-eebusreg), [`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus) |
| MODBUS and SunSpec | [`helianthus-modbus`](https://github.com/Project-Helianthus/helianthus-modbus), [`helianthus-modbusreg`](https://github.com/Project-Helianthus/helianthus-modbusreg), [`helianthus-docs-modbus`](https://github.com/Project-Helianthus/helianthus-docs-modbus) |
| CAN and GREE VRF | [`helianthus-canbus`](https://github.com/Project-Helianthus/helianthus-canbus), [`helianthus-canbusreg`](https://github.com/Project-Helianthus/helianthus-canbusreg), [`helianthus-docs-canbus`](https://github.com/Project-Helianthus/helianthus-docs-canbus) |
| Home Assistant | [`helianthus-ha-addon`](https://github.com/Project-Helianthus/helianthus-ha-addon), [`helianthus-ha-integration`](https://github.com/Project-Helianthus/helianthus-ha-integration) |
| Community eBUS exploration | [`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer) |

Each repository carries its own setup, tests, contribution boundaries, and
license. Start with an issue in the repository that owns the behavior you want
to change. For licensing and third-party sources, see
[`LICENSING.md`](../LICENSING.md) and [`THIRD_PARTY.md`](../THIRD_PARTY.md).

# Protocol Hacker

Helianthus intentionally exposes both polished semantic surfaces and rawer
protocol-facing evidence. If you are exploring undocumented behavior, comparing
states, or building tooling around eBUS, there are three important surfaces.

## 1. Helianthus Portal

The
[`helianthus-ebusgateway`](https://github.com/Project-Helianthus/helianthus-ebusgateway)
Portal is the native Helianthus UI for investigation and evidence collection.

Use it when you want:

- projection and semantic views in one place
- timeline, provenance, and snapshot workflows
- issue drafts and export bundles rooted in live gateway evidence

Reference docs:
- [`api/portal.md`](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/api/portal.md)

## 2. The MCP Endpoint

The gateway serves MCP at `/mcp`. This is the preferred scriptable surface for
agentic investigation, tooling, and rapid iteration before consumer rollout.

Use it when you want:

- reproducible scripted reads
- access to registry, semantic, snapshot, and RPC tools
- a surface that can be attacked, reviewed, and stabilized before GraphQL parity

Reference docs:
- [`api/mcp.md`](https://github.com/Project-Helianthus/helianthus-docs-ebus/blob/main/api/mcp.md)

## 3. VRC Explorer

[`helianthus-vrc-explorer`](https://github.com/Project-Helianthus/helianthus-vrc-explorer)
remains a valid standalone tool for the wider eBUS and `ebusd` community. It is
not the strategic center of Helianthus, but it remains useful for regulator-
focused discovery, operator debugging, and community workflows that live outside
the gateway runtime itself.

Use it when you want:

- a focused VRC exploration tool
- CLI-driven B524 discovery workflows
- a tool that can remain useful even when the rest of the Helianthus stack is
  not in the loop

## Knowledge Capture Rule

No matter where you discover new protocol behavior:

- Portal
- MCP
- VRC Explorer
- raw transport/debug work

the reusable knowledge belongs in
[`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus).

The tool is not the canonical home of the knowledge. The docs repo is.

# First Contribution: Follow One Read-Only Profile

This path lets a first-time contributor reproduce one existing profile from
native evidence to public presentation. It uses the Gateway's deterministic
SunSpec fixture at an immutable public revision and requires only public source,
the fixture, and a local development toolchain.

This is a narrow orientation path. The linked [architecture example](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/33d02f20b706440fbfe4a3ac6f0228507bf51212/docs/examples/sunspec-semreg-pv.md),
[anonymous reproducibility record](./reproducibility.md), [software maturity
matrix](./maturity-matrix.md), and [contribution guide](../CONTRIBUTING.md) own
the full contracts and evidence boundaries.

## Prerequisites

- Git
- Go 1.22 or newer with a working race detector toolchain
- public HTTPS access to GitHub and the Go module proxy

The broader public build also uses Python 3.11 or newer and Node.js 20 or
newer. They are not needed for this focused command.

## Clone The Exact Starting Revision

```bash
git clone https://github.com/Project-Helianthus/helianthus-ebusgateway.git
cd helianthus-ebusgateway
git checkout --detach 33d02f20b706440fbfe4a3ac6f0228507bf51212
git rev-parse HEAD
GOWORK=off go test -race ./cmd/gateway \
  -run '^TestPUBLIC05SunSpecSemRegSurvivesGatewayProvidersAndPortal$' \
  -count=1
```

The revision command must print
`33d02f20b706440fbfe4a3ac6f0228507bf51212`. The test should finish with an
`ok` result for `github.com/Project-Helianthus/helianthus-ebusgateway/cmd/gateway`.
It starts only loopback listeners and uses an in-process deterministic fixture.
It does not contact a device.

On the macOS proof host, the test command was prefixed with
`DEVELOPER_DIR=/Library/Developer/CommandLineTools` to select the installed
command-line toolchain instead of an unlicensed Xcode installation. This is a
host toolchain selection, not a repository or device prerequisite.

## What The Test Demonstrates

The test begins with valid native active power of **1234.5 W** and frequency of
**50 Hz**. It then advances the fixture with valid power of **4321.5 W** and a
malformed **2000 Hz** frequency. The healthy power advances and stays selected.
The invalid frequency creates no new candidate; the earlier 50 Hz evidence
becomes stale and degraded, is not selected, and is explicitly withheld with
`mapping.field_invalid`.

That is the small fail-closed negative case: one malformed field cannot invent
zero, become available, revive stale data, or discard the healthy field. The
same snapshot, evaluation, selections, and projection result then survives the
Gateway provider, MCP, M2M GraphQL, and Portal path.

The executable path is
[`cmd/gateway/public05_sunspec_path_test.go`](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/33d02f20b706440fbfe4a3ac6f0228507bf51212/cmd/gateway/public05_sunspec_path_test.go).
The detailed positive and negative assertions are linked from the
[SunSpec-to-SemReg example](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/33d02f20b706440fbfe4a3ac6f0228507bf51212/docs/examples/sunspec-semreg-pv.md).

## Follow Ownership At Each Layer

| When you encounter | Owner and contribution boundary |
| --- | --- |
| SunSpec identity, model decoding, qualification, capability selection, or retained native observation | [`helianthus-modbusreg`](https://github.com/Project-Helianthus/helianthus-modbusreg/tree/ed75fdfbed0d42eb2f159afc0174449b545b31af). A profile-owned change belongs there, with protocol evidence and native tests. Do not teach a consumer to decode registers. |
| A protocol-neutral fact, lifecycle, quality, selection, provenance, or projection contract | [`helianthus-semreg`](https://github.com/Project-Helianthus/helianthus-semreg/tree/089ed6ae9004cfba8aff27f1e54d579aeccc0b4c). Canonical domain types belong there and remain separate from native profiles. |
| The accepted native observation being published and composed at runtime | [`helianthus-ebusgateway/internal/modbusadapter`](https://github.com/Project-Helianthus/helianthus-ebusgateway/tree/33d02f20b706440fbfe4a3ac6f0228507bf51212/internal/modbusadapter). Gateway code wires owners together; it does not become the native profile or canonical semantic owner. |
| MCP, M2M GraphQL, or Portal output | [`mcp`](https://github.com/Project-Helianthus/helianthus-ebusgateway/tree/33d02f20b706440fbfe4a3ac6f0228507bf51212/mcp), [`m2mgraphql`](https://github.com/Project-Helianthus/helianthus-ebusgateway/tree/33d02f20b706440fbfe4a3ac6f0228507bf51212/m2mgraphql), and [`portal`](https://github.com/Project-Helianthus/helianthus-ebusgateway/tree/33d02f20b706440fbfe4a3ac6f0228507bf51212/portal). Consumers preserve the promoted contract and explicit loss; they do not requalify native evidence or select competing candidates. |

Before proposing a change, open the issue in the owning repository, branch from
its current `origin/main`, follow its repository-local `AGENTS.md`, and run its
declared validation. Link protocol facts to publishable evidence and keep
candidate, implemented, offline-tested, packaged, and physically verified
states separate.

This demonstration proves one offline software path at the pinned revision. It
does not prove SunSpec certification, an exact product model, packaging,
installation, or physical validation.

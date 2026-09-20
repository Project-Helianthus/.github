# Public Reproducibility Record

This record shows what a contributor can reproduce from the public Gateway
repository without organization credentials or sibling checkouts. It is a
bounded source-build and offline-test result, not evidence of installation,
certification, packaging parity, or physical device qualification.

## Anonymous environment

The proof used a fresh clone with an empty home directory, module cache, Go
workspace, and temporary directory. Git credential helpers, terminal prompts,
and askpass were disabled; no GitHub token, `.netrc`, `GOPRIVATE`,
`GONOSUMDB`, or private module cache was available. All Helianthus dependencies
resolved from public HTTPS sources.

The accepted run selected the installed Apple Command Line Tools explicitly and
recorded these tool versions:

- Git 2.54.0
- Go 1.26.2 (`darwin/arm64`)
- Python 3.14.7
- Node.js 26.7.0

The repository contract remains Git plus Go 1.22 or newer, Python 3.11 or
newer, and Node.js 20 or newer, matching hosted CI.

## Public module graph

The anonymous run resolved these Helianthus modules without credentials:

- `helianthus-ebusgo` at `872b442444f2`
- `helianthus-ebusreg` at `e24532a50caa`
- `helianthus-eebus-go` at `v0.7.1-helianthus.20`
- `helianthus-eebusreg` at `v0.1.35`
- `helianthus-modbus` at `f670287d0d86`
- `helianthus-modbusreg` at `ed75fdfbed0d`
- `helianthus-semreg` at `089ed6ae9004`
- `helianthus-ship-go` at `v0.6.1-helianthus.18`
- `helianthus-spine-go` at `v0.7.1-helianthus.9`

EEBUS and Matter software outputs and bindings are public 0.7 scope. Their
listed or planned presence does not claim complete integration, protocol
conformance, certification, or physical qualification, and neither depends on
private Helianthus hardware.

## Commands and result

The public path is:

```bash
git clone https://github.com/Project-Helianthus/helianthus-ebusgateway.git
cd helianthus-ebusgateway
git rev-parse HEAD
GOWORK=off go mod download
./scripts/ci_local.sh
go run ./cmd/gateway -h
```

The accepted anonymous run covered the Portal asset server, Go vet/build and
Linux 32-bit compilation, the complete race-enabled Go test suite, 224 Python
tests, lint with zero findings, Storage and EVSE mapping gates, and the Gateway
flag smoke check. The final accepted revision is recorded in the linked Gateway
pull request and this document's history.

T01..T88 was **DEFERRED / NOT RUN** under the Board's public-readiness scope
decision. A repository-owner override allowed this run to continue because the
only runtime change adds a final caller-cancellation check before an existing
B503 command emission; it does not change framing, endpoint topology, or
protocol semantics. T01..T88 remains mandatory against the final 0.7 release
bill of materials. No unexpected failure or xpass was accepted.

## Finding closed during the proof

The first anonymous run at Gateway revision `24aefc473b6183a017c6bbc1ee9318f8f26db22d`
found a deadline race: a caller could expire while waiting for the B503 emission
lock, while propagation to the derived internal context lagged long enough to
permit emission. Revision `79add8b5b3eddc1af452611647c3de3bf9dd7224`
adds a final check of the original caller context at the emission boundary and
adds a deterministic regression test. The focused regression and neighboring
B503 tests passed 25 consecutive race-enabled runs before the full anonymous
proof was repeated.


# Helianthus 0.7 Software Maturity Matrix

This is the public evidence boundary for the software planned for 0.7. Each
positive state links to an immutable commit. An issue link identifies remaining
work; it is not implementation evidence. No row inherits maturity from another
row.

Inspection baseline: **20 September 2026**. Later commits, packages, or physical
results require a new evidence link; they do not update this record implicitly.

## State vocabulary

- **IMPLEMENTED**: code exists at the linked revision.
- **QUALIFIED**: the linked evidence satisfies that profile's declared bounded
  qualification rule. This is not product certification.
- **CANDIDATE**: evidence is useful but does not satisfy qualification.
- **UNSUPPORTED**: the cited contract explicitly rejects the case.
- **UNKNOWN**: no publishable evidence establishes the value or state.
- **OFFLINE-TESTED**: deterministic tests or replay pass without a device.
- **HARDWARE-TEST-READY**: the exact integrated candidate, procedure, and
  prerequisites are complete. No row below currently claims this state.
- **PHYSICALLY VERIFIED**: a dated public record covers the exact model,
  firmware, function, and software revision. No row below currently claims
  this state.

`IMPLEMENTED`, `QUALIFIED`, and `OFFLINE-TESTED` are independent. None implies
packaging, installation, certification, conformance, or physical validation.

## Product and profile evidence

| Product or profile | Exact model | Firmware | Function | Source or specification revision | Decoder or native implementation | Semantic integration | Consumer exposure | Offline evidence | Physical-validation date |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Vaillant / eBUS | VR940f remains a qualification target; other exact models **UNKNOWN** ([ebusreg #148](https://github.com/Project-Helianthus/helianthus-ebusreg/issues/148)) | **UNKNOWN** | Native discovery, evidence and gateway composition are **IMPLEMENTED** at the [accepted Gateway baseline](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/8e6194e964da043e1806790ebe451fab61e6b588) | Exact applicable revision **UNKNOWN** | eBUS registry is **IMPLEMENTED** at [`e24532a`](https://github.com/Project-Helianthus/helianthus-ebusreg/commit/e24532a50caa00c113751b98b88239e045d731e8) | PV path is **IMPLEMENTED** at [`2ad927b`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/2ad927b6986c6ce01ed55ff1da25b38625188f44); complete Thermal/HVAC remains [in progress](https://github.com/Project-Helianthus/helianthus-ebusgateway/issues/952) | MCP, GraphQL, and Portal are selectively **IMPLEMENTED** at [`2ad927b`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/2ad927b6986c6ce01ed55ff1da25b38625188f44) and [`5eb5346`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/5eb53465e88d254455251203e2dc30f813541bba) | **OFFLINE-TESTED** only at the linked revisions | **UNKNOWN** |
| VRC Explorer | Exact device set **UNKNOWN** | **UNKNOWN** | Standalone exploration product | Product source is **IMPLEMENTED** at [`c46b8bb`](https://github.com/Project-Helianthus/helianthus-vrc-explorer/commit/c46b8bb277c45de91e78593e0ee7659fe870c9e3) | **IMPLEMENTED** at `c46b8bb` | Not a SemReg owner | Standalone product; add-on source pins `v0.5.1` at [`37910f1`](https://github.com/Project-Helianthus/helianthus-ha-addon/blob/37910f12956dcbfbc0382bb7f417c9a7bd23d8ce/helianthus/Dockerfile) | Reproducible product acceptance evidence: **UNKNOWN** | **UNKNOWN** |
| EEBUS / SHIP / SPINE | Exact device model **UNKNOWN** | **UNKNOWN** | Discovery and pending pairing are **IMPLEMENTED** at [`c68cb5e`](https://github.com/Project-Helianthus/helianthus-eebus-go/commit/c68cb5ee5d6bd9b2f8063bc4160325d3d183430a) | SHIP 1.0.1 / SPINE 1.3.0 are recorded by the [immutable library README](https://github.com/Project-Helianthus/helianthus-eebus-go/blob/c68cb5ee5d6bd9b2f8063bc4160325d3d183430a/README.md); the applicable Helianthus normative ledger remains [open](https://github.com/Project-Helianthus/helianthus-docs-eebus/issues/140) | Native runtime is **IMPLEMENTED** at `c68cb5e`; registry source is **IMPLEMENTED** at [`ede40b9`](https://github.com/Project-Helianthus/helianthus-eebusreg/commit/ede40b929e9c2d9cbf0de20c4844e737d5e6af68) | **UNKNOWN**, pending exact standard mapping; output binding is not complete | Gateway native runtime/read surfaces are **IMPLEMENTED** at [`143bf19`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/143bf1907e32a2acef3abde335e56a1494d9c557) | Native paths are **OFFLINE-TESTED**; no output-binding conformance claim | **UNKNOWN** |
| SunSpec / experimental Fronius flavor | Exact qualified product model **UNKNOWN** | **UNKNOWN** | Read-only qualification card is **IMPLEMENTED** at [`1e2cea3`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/1e2cea375f415847fb70cb8a181cdd1285543eca) | SunSpec phase-one coordinates are recorded at the same immutable revision | Standard-family decoder and bounded card are **IMPLEMENTED**; product qualification remains **CANDIDATE** | PV projection example is **IMPLEMENTED** at [`2ad927b`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/2ad927b6986c6ce01ed55ff1da25b38625188f44) | Exact positive/negative Gateway example remains [PUBLIC-05](https://github.com/Project-Helianthus/helianthus-ebusgateway/issues/985); packaged presence **UNKNOWN** | Qualification card is **OFFLINE-TESTED** | **UNKNOWN** |
| Huawei SmartLogger | SmartLogger | V300R024C10SPC191 / SPC210 | Read-only identity/inventory qualification card | Public evidence set pinned by [`4bba20c`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/4bba20ca8cc773bbabb152880ed459a02ee84cd3) | **IMPLEMENTED**, test-ready card; connected evidence still missing | **UNKNOWN** | **UNKNOWN** | **OFFLINE-TESTED** at `4bba20c` | **UNKNOWN** |
| Huawei EMMA | EMMA-A01 / EMMA-A02 | Bounded R024/R025 floors at [`4bba20c`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/4bba20ca8cc773bbabb152880ed459a02ee84cd3) | Read-only identity/inventory card | Public evidence set pinned by `4bba20c` | **CANDIDATE**, evidence-blocked card | **UNKNOWN** | **UNKNOWN** | Identity rules are **OFFLINE-TESTED** | **UNKNOWN** |
| Huawei S-Dongle | S-DongleA-05 / B-03 / B-06 | **UNKNOWN** | Non-response hard stop | Public evidence set pinned by [`4bba20c`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/4bba20ca8cc773bbabb152880ed459a02ee84cd3) | **UNSUPPORTED** for automatic admission at this baseline | **UNKNOWN** | **UNKNOWN** | Hard-stop behavior is **OFFLINE-TESTED** | **UNKNOWN** |
| GREE VRF CAN | Exact model **UNKNOWN** | **UNKNOWN** | Receive-only state replay and qualification | Evidence revision pinned by [`233fd48`](https://github.com/Project-Helianthus/helianthus-canbusreg/commit/233fd48136fa0e5024d87f3676c99990ef0d94b6) | **QUALIFIED** for bounded offline replay; no live acquisition claim | **UNKNOWN** | **UNKNOWN** | **OFFLINE-TESTED** at `233fd48` | **UNKNOWN** |
| Growatt LV BMS CAN | Exact product model **UNKNOWN** | Protocol V1.04 | Receive-only observation replay | V1.04 profile pinned by [`8c827ea`](https://github.com/Project-Helianthus/helianthus-canbusreg/commit/8c827ea26ffbad8b50aba2c6ae89028622ba4343) | **QUALIFIED** for bounded offline replay | **UNKNOWN** | **UNKNOWN** | **OFFLINE-TESTED** at `8c827ea` | **UNKNOWN** |
| Growatt Protocol II | TL3-X family | Exact firmware **UNKNOWN** | FC03 identity; FC04 monitoring foundation | Protocol II v1.24 pinned by [`7853d90`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/7853d903970a4fdded35abaef01fe30f7e93be6a) | **CANDIDATE**: identity and monitoring foundation implemented; exact profile work remains [open](https://github.com/Project-Helianthus/helianthus-modbusreg/issues/196) | **UNKNOWN** | **UNKNOWN** | Foundation is **OFFLINE-TESTED** | **UNKNOWN** |
| Growatt BMS RS-485 | 1xSxxP ESS | Header V2.0 / cumulative 2.02 | Read-only RTU observation and Storage projection | Revision tuple pinned by [`ff8cbea`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/ff8cbea47b05ded1436a0ed26d5f71f53d61ab17) | Native observer is **IMPLEMENTED** | Storage SemReg path is **IMPLEMENTED** at [`b2651d7`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/b2651d73639efb7ba690bc1464d9b8b04df51e4a) | HA consumer is **IMPLEMENTED** at [`b997372`](https://github.com/Project-Helianthus/helianthus-ha-integration/commit/b997372f64dc5f127bd2b6bf7eaa3e770d2f7765); package presence **UNKNOWN** | **OFFLINE-TESTED** | **UNKNOWN** |
| Tesla Gen3 Wall Connector | WC3 / HSC | 24.44.3 evidence lane | FC100 current-limit evidence and EVSE projection | Exact native bodies pinned by [`ed75fdf`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/ed75fdfbed0d42eb2f159afc0174449b545b31af) | Native bounded validation is **IMPLEMENTED** | EVSE SemReg path is **IMPLEMENTED** at [`1fbf5e1`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/1fbf5e1d95a1c07a2537e8fa4c4b78724bcf126a) | HA consumer is **IMPLEMENTED** at [`1e23a6b`](https://github.com/Project-Helianthus/helianthus-ha-integration/commit/1e23a6b0b3efb94730ec82e2c12d11ad1ef775c6); package presence **UNKNOWN** | **OFFLINE-TESTED**; no sender, route, or live authority follows | **UNKNOWN** |
| Tesla legacy Wall Connector | Legacy FBE0/FDE0 lane | **UNKNOWN** | RS-485 codec and bounded current evidence | Native baseline pinned by [`75e4e39`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/75e4e3988a7682068c02d8ac24f737b7f24a029f) | **IMPLEMENTED** native codec/evidence | **UNKNOWN** | **UNKNOWN** | **OFFLINE-TESTED** native path | **UNKNOWN** |
| OutBack AXS SunSpec | AXS Port family; exact model **UNKNOWN** | **UNKNOWN** | Read-only observed-state decoder | Baseline pinned by [`ca30533`](https://github.com/Project-Helianthus/helianthus-modbusreg/commit/ca30533ac0bb9d7cf438630c93dbf0f139a94843) | **IMPLEMENTED** native decoder seam | **UNKNOWN** | **UNKNOWN** | **OFFLINE-TESTED** native path | **UNKNOWN** |
| Matter output binding | Exact target model **UNKNOWN** | **UNKNOWN** | Protocol-neutral output binding | Planned anchor is Matter draft 1.7 ballot 0.9; accepted Gateway inventory at [`5eb5346`](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/5eb53465e88d254455251203e2dc30f813541bba/docs/architecture/runtime-driver-provider-contract-v1.md) has no composed output | Not implemented in the accepted baseline | SemReg records input-only; output mapping **UNKNOWN** | **UNKNOWN** | **UNKNOWN** | **UNKNOWN** |

EEBUS and Matter software outputs are public 0.7 scope and do not depend on
private hardware. Their incomplete cells remain unknown until linked public
evidence exists; public scope does not turn planned work into implementation.

## Platform and consumer baselines

| Layer | Development baseline | What the baseline proves | Package or installed baseline |
| --- | --- | --- | --- |
| Semantic Registry | [`089ed6ae9004cfba8aff27f1e54d579aeccc0b4c`](https://github.com/Project-Helianthus/helianthus-semreg/commit/089ed6ae9004cfba8aff27f1e54d579aeccc0b4c) | Canonical kernel and PV, Storage, EVSE, Thermal/HVAC, and Infrastructure pack contracts are **IMPLEMENTED** and **OFFLINE-TESTED**. It does not prove native acquisition, consumer integration, or device support. | No separately published package digest is established here: **UNKNOWN** |
| Gateway | [`8e6194e964da043e1806790ebe451fab61e6b588`](https://github.com/Project-Helianthus/helianthus-ebusgateway/commit/8e6194e964da043e1806790ebe451fab61e6b588) | Current public development `main`; selective SemReg composition and public surfaces only. | HA add-on source pins Gateway [`a759efd7f72a099288f1fc2b7cf20236d37cfa0b`](https://github.com/Project-Helianthus/helianthus-ha-addon/blob/37910f12956dcbfbc0382bb7f417c9a7bd23d8ce/helianthus/Dockerfile): **PACKAGING LAG PRESENT** |
| Home Assistant integration | [`1e23a6b0b3efb94730ec82e2c12d11ad1ef775c6`](https://github.com/Project-Helianthus/helianthus-ha-integration/commit/1e23a6b0b3efb94730ec82e2c12d11ad1ef775c6) | PV, Storage, and EVSE consumers are implemented at their linked row revisions. This does not prove an installed copy. | Packaged revision and installed revision: **UNKNOWN**; consumer lag cannot be measured without them |
| Home Assistant add-on source | [`37910f12956dcbfbc0382bb7f417c9a7bd23d8ce`](https://github.com/Project-Helianthus/helianthus-ha-addon/commit/37910f12956dcbfbc0382bb7f417c9a7bd23d8ce) | Source declares add-on version `0.6.56`, Gateway pin `a759efd…`, and VRC Explorer `v0.5.1`. | Public image digest, release asset digest, installed add-on revision, and installed Gateway build ID: **UNKNOWN** |

The add-on image name in configuration is not an image digest. A version string,
merged library change, or successful development build does not establish that
an installed add-on contains the same source. The exact 0.7 package BOM,
Daybreak Blue review, T01..T88, and exhaustive dated physical validation remain
release gates.

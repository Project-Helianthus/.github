# Third-Party And Dependency License Inventory

Inspection baseline: **20 September 2026**. This is a source-linked inventory,
not a legal conclusion or a substitute for the named license files. Preserve
license text, notices, attribution, and source obligations that apply to the
exact artifact being redistributed.

The software snapshot is the Gateway [`go.mod` at `8e6194e`](https://github.com/Project-Helianthus/helianthus-ebusgateway/blob/8e6194e964da043e1806790ebe451fab61e6b588/go.mod).
That tree has no checked-in `vendor/` directory. Dependencies are resolved as Go
modules; this inventory includes every module named by that manifest, plus the
public Matter source anchor. A release BOM must regenerate this inventory if any
pin changes.

## Helianthus modules and temporary upstream forks

| Module and pinned source | License file at that source | Relationship |
| --- | --- | --- |
| `helianthus-ebusgo` `872b442444f2` | [AGPL-3.0](https://github.com/Project-Helianthus/helianthus-ebusgo/blob/872b442444f286cd075831db68304bd46f09fd87/LICENSE) | Helianthus public module |
| `helianthus-ebusreg` `e24532a50caa` | [AGPL-3.0](https://github.com/Project-Helianthus/helianthus-ebusreg/blob/e24532a50caa00c113751b98b88239e045d731e8/LICENSE) | Helianthus public module |
| `helianthus-eebusreg` `v0.1.35` / `c0cd3a9` | [MIT](https://github.com/Project-Helianthus/helianthus-eebusreg/blob/c0cd3a9625093f07b6d950f7563666d6b98c0b8c/LICENSE) | Helianthus public module |
| `helianthus-modbus` `f670287d0d86` | [AGPL-3.0](https://github.com/Project-Helianthus/helianthus-modbus/blob/f670287d0d864e9d669ddba0d21a217beadc45f9/LICENSE) | Helianthus public module |
| `helianthus-modbusreg` `ed75fdfbed0d` | [AGPL-3.0](https://github.com/Project-Helianthus/helianthus-modbusreg/blob/ed75fdfbed0d42eb2f159afc0174449b545b31af/LICENSE) | Helianthus public module |
| `helianthus-semreg` `089ed6ae9004` | [AGPL-3.0](https://github.com/Project-Helianthus/helianthus-semreg/blob/089ed6ae9004cfba8aff27f1e54d579aeccc0b4c/LICENSE) | Helianthus public module |
| `helianthus-eebus-go` `v0.7.1-helianthus.20` / `8ae8f91` | [MIT](https://github.com/Project-Helianthus/helianthus-eebus-go/blob/8ae8f91dad595b2b2b5c4ed782befdb47220404f/LICENSE) | Temporary fork of upstream EEBUS software |
| `helianthus-ship-go` `v0.6.1-helianthus.18` / `84eb654` | [MIT](https://github.com/Project-Helianthus/helianthus-ship-go/blob/84eb65407f694f0a2eaee323d7afceae5cb4d115/LICENSE) | Temporary fork of upstream SHIP software |
| `helianthus-spine-go` `v0.7.1-helianthus.9` / `b0cdd86` | [MIT](https://github.com/Project-Helianthus/helianthus-spine-go/blob/b0cdd8653ccc0c0d0133706172541e80179de818/LICENSE) | Temporary fork of upstream SPINE software |

The temporary forks retain upstream license and notice obligations. Their
presence does not transfer third-party trademarks, standards, patents, or
certification rights to Helianthus.

## Other modules in the Gateway manifest

| Module pin | Actual license file |
| --- | --- |
| `grandcat/zeroconf v1.0.0` | [MIT](https://github.com/grandcat/zeroconf/blob/86b31ec94a48fec7292089a7a71a4fa185be3f1f/LICENSE) |
| `graphql-go/graphql v0.8.1` | [MIT](https://github.com/graphql-go/graphql/blob/a9741863816e423e4287fd8947731d637451cf6c/LICENSE) |
| `graphql-go/handler v0.2.4` | [MIT](https://github.com/graphql-go/handler/blob/62f4eb5dc6b7e8e1f4c7d7dca1a2af3399a486a1/LICENSE) |
| `machinebox/graphql v0.2.2` | [Apache-2.0](https://github.com/machinebox/graphql/blob/05b17f3157491bbfa5d6fc2006443a272d960d15/LICENSE) |
| `golang.org/x/mod v0.21.0` | [BSD-3-Clause](https://github.com/golang/mod/blob/46a3137daeac7bd5e64dc5971191e4a7207e6d89/LICENSE) |
| `golang.org/x/sys v0.25.0` | [BSD-3-Clause](https://github.com/golang/sys/blob/a43b625d3c32b5cd2726d132c8478884ae6cb0dc/LICENSE) |
| `golang.org/x/text v0.22.0` | [BSD-3-Clause](https://github.com/golang/text/blob/3b64043c9e8fa8cd61a019df17dc729630915fa9/LICENSE) |
| `golang.org/x/net v0.29.0` | [BSD-3-Clause](https://github.com/golang/net/blob/35b4abaed97f1df7ee83c075f500e84d8d75d184/LICENSE) |
| `golang.org/x/sync v0.11.0` | [BSD-3-Clause](https://github.com/golang/sync/blob/fe3591bd8a96873abc98bb9d2d5c62f27efca3e9/LICENSE) |
| `golang.org/x/tools v0.25.0` | [BSD-3-Clause](https://github.com/golang/tools/blob/7398f36f576504906456476c2f6251b76feb664e/LICENSE) |
| `gorilla/websocket v1.5.3` | [BSD-2-Clause](https://github.com/gorilla/websocket/blob/ce903f6d1d961af3a8602f2842c8b1c3fca58c4d/LICENSE) |
| `gopkg.in/yaml.v3 v3.0.1` | [MIT and Apache-2.0 components](https://github.com/go-yaml/yaml/blob/f6f7691b1fdeb513f56608cd2c32c51f8194bf51/LICENSE) |
| `github.com/ahmetb/go-linq/v3 v3.2.0` | [Apache-2.0](https://github.com/ahmetb/go-linq/blob/9b75bfdcd4c49fdfd69601f69c8faec3c8ceff0f/LICENSE) |
| `cenkalti/backoff v2.2.1` | [MIT](https://github.com/cenkalti/backoff/blob/5267b6dd4d2666b980a911bf235efa276222cbe2/LICENSE) |
| `enbility/go-avahi d5de6b280d7a` | [MIT](https://github.com/enbility/go-avahi/blob/d5de6b280d7a/LICENSE) |
| `github.com/enbility/zeroconf/v2 be1cae74fda6` | [MIT](https://github.com/enbility/zeroconf/blob/be1cae74fda6/LICENSE) |
| `github.com/godbus/dbus/v5 v5.1.0` | [BSD-2-Clause](https://github.com/godbus/dbus/blob/e523abc905595cf17fb0001a7d77eaaddfaa216d/LICENSE) |
| `golanguzb70/lrucache v1.2.0` | [MIT](https://github.com/golanguzb70/lrucache/blob/ede7dc5cf7fc905315ea1e9a969437687b09318a/LICENSE) |
| `miekg/dns v1.1.62` | [BSD-3-Clause](https://github.com/miekg/dns/blob/07a2352e44fe1aaa3bae7b0b4cbcb3a0f6d1a4a6/LICENSE) |
| `rickb777/date v1.21.1` | [BSD-3-Clause](https://github.com/rickb777/date/blob/b7388c8d966e8186fc37862639c11d761b546e95/LICENSE) |
| `rickb777/plural v1.4.2` | [BSD-3-Clause](https://github.com/rickb777/plural/blob/5b1ad1d92990444d45cd3352389ba2b49f8e97be/LICENSE) |
| `gitlab.com/c0b/go-ordered-json febf46534d5a` | [MIT](https://gitlab.com/c0b/go-ordered-json/-/blob/febf46534d5a/LICENSE) |
| `matryer/is v1.4.1` | [MIT](https://github.com/matryer/is/blob/02e4121244e0f9e27b5ebdade62f5da7b7a42f23/LICENSE) |
| `pkg/errors v0.9.1` | [BSD-2-Clause](https://github.com/pkg/errors/blob/614d223910a179a466c1767a985424175c39b465/LICENSE) |

## Add-on build dependencies

The add-on source at
[`37910f1`](https://github.com/Project-Helianthus/helianthus-ha-addon/commit/37910f12956dcbfbc0382bb7f417c9a7bd23d8ce)
also installs VRC Explorer `v0.5.1` from source. That exact release carries
[GPL-3.0-or-later](https://github.com/Project-Helianthus/helianthus-vrc-explorer/blob/615418cbfcf974d6b8d0b3140abe9e9d627dc3bf/LICENSE).
Its immutable [`pyproject.toml`](https://github.com/Project-Helianthus/helianthus-vrc-explorer/blob/615418cbfcf974d6b8d0b3140abe9e9d627dc3bf/pyproject.toml)
declares `httpx>=0.24`, `rich>=13`, `textual>=0.82`, and `typer==0.27.1`.
Typer `0.27.1` carries [MIT](https://github.com/fastapi/typer/blob/fe2aa0e2f9c853de378e60ca24ec3b256144decf/LICENSE).
The actual resolved versions and exact license files for the three range-based
requirements are **unknown** because the package source and inspected add-on
source contain no Python lock file or built-image SBOM.

The add-on Dockerfile also names Home Assistant base `3.20`, Go
`1.26.2-alpine`, and Python `3.12-alpine` images without immutable digests. Their
exact image layers and bundled license artifacts are therefore **unknown** at
this source baseline. The final package BOM must record the resolved image
digests, Python dependency versions, license files, and notices before release.

## Public Matter source anchor

The planned Matter output mapping references
[`AryaHassanli/connectedhomeip` at `29b4768`](https://github.com/AryaHassanli/connectedhomeip/commit/29b4768a513cf566011ab8cd60df1bc495204953),
whose source carries [Apache-2.0](https://github.com/AryaHassanli/connectedhomeip/blob/29b4768a513cf566011ab8cd60df1bc495204953/LICENSE)
and a separate [NOTICE](https://github.com/AryaHassanli/connectedhomeip/blob/29b4768a513cf566011ab8cd60df1bc495204953/NOTICE).
If Matter SDK source is redistributed, preserve both files and the notices they
require. No Matter SDK source is vendored in the inspected Gateway or temporary
EEBUS-fork trees.
That source license does not establish Matter certification, trademark-program
participation, patent rights, or permission to redistribute restricted Matter
specification material. Those statuses remain **unknown** unless separately
verified for the exact artifact and use.

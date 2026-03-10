# Helianthus Licensing Model

This document explains the intended licensing model and contribution boundary for
Project Helianthus.

It is a project policy document. It does not replace the license files in each
repository and it does not, by itself, act as a standalone CLA or copyright-
assignment instrument.

## 1. Reverse-Engineered Protocol Knowledge

Reverse-engineered protocol knowledge is intended to remain permanently public.

This includes material such as:

- wire layouts
- frame formats
- register maps
- value semantics
- timing quirks
- protocol notes derived from reverse engineering

For robustness across jurisdictions, the recommended publication form is
`CC0-1.0` public-domain dedication for that class of material.

Project intent:

- once Helianthus publishes reverse-engineered protocol knowledge as public
  protocol documentation, it should remain publicly reusable
- Helianthus should not later try to close that protocol knowledge back up
- the community should be free to copy, mirror, extend, validate, and republish
  that knowledge

## 2. Helianthus Implementation Documentation

Implementation-specific Helianthus documentation follows the OSS licensing model
of the Helianthus implementation.

This includes material such as:

- architecture documentation
- API contracts
- rollout and state-machine behavior
- deployment guidance
- implementation-specific semantic and runtime notes

Default project intent:

- protocol knowledge in the abstract remains public-domain style material
- Helianthus-specific implementation work remains OSS under the repository
  license, currently `AGPL-3.0` unless a repository states otherwise

## 3. OSS Core And Proprietary Surrounding Components

Helianthus is intended to support an OSS core plus separate surrounding
proprietary components where the boundary is kept clean.

Project intent:

- the Helianthus OSS component remains OSS
- changes to the Helianthus OSS component that are merged into Helianthus remain
  under the applicable public license
- separate components built around Helianthus may be proprietary at the
  discretion of the Helianthus owner

Examples of potentially separate proprietary components:

- a certified Matter implementation or endpoint
- commercial managed services around Helianthus
- proprietary operational tooling or compliance layers

Boundary rule:

- if a capability requires changes to Helianthus itself and those changes are
  merged back into Helianthus, those Helianthus-side changes remain public under
  the applicable repository license
- if a component stays separate from Helianthus itself, it does not
  automatically become part of the Helianthus OSS codebase merely because it
  integrates with or surrounds Helianthus

Acknowledgement rule:

- when Helianthus OSS is reused inside a broader private or commercial effort,
  applicable license notices, attribution, and source acknowledgement for the
  Helianthus-originating OSS component should be preserved

## 4. Community Freedom

The community remains free and encouraged to build:

- independent OSS implementations
- complementary integrations
- alternative Matter-related implementations
- tooling that overlaps with or competes with owner-built proprietary layers

The goal is not to close the ecosystem. The goal is to let Helianthus remain an
open engineering base while also allowing a revenue stream around engineering,
certification, packaging, operations, and proprietary surrounding components.

## 5. Contributor Inbound Rule

By submitting material for inclusion in Helianthus, a contributor confirms that
the submitted material can be published under the appropriate Helianthus public
licensing lane:

- reverse-engineered protocol knowledge in the public-domain lane
- implementation-specific Helianthus material in the repository OSS lane

This means, at minimum:

- merged public contributions remain public on the Helianthus side
- contributors should not submit material that they cannot legally publish under
  the applicable public license
- reusable knowledge that belongs in Helianthus should not be submitted as
  “temporary private follow-up material” if it is intended for merge

## 6. Copyright Note

This document is intentionally careful about copyright ownership.

- it explains how material may be accepted and published in Helianthus
- it explains the intended OSS/proprietary boundary
- it does not by itself transfer third-party copyright to the Helianthus owner

If the project later wants explicit contributor copyright assignment or a
specific owner-favoring commercial rights instrument, that should be done
through a separate CLA or contributor terms document.

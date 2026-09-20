# Helianthus Licensing Model

This document explains the public software, protocol-knowledge, third-party, and
contribution boundaries for Project Helianthus.

It is a project policy document. It does not replace the license files in each
repository and it does not, by itself, act as a standalone CLA or copyright-
assignment instrument.

This update changes no repository or third-party license.

## 1. Reverse-Engineered Protocol Knowledge

Reverse-engineered protocol knowledge is intended to remain permanently public.

This includes material such as:

- wire layouts
- frame formats
- register maps
- value semantics
- timing quirks
- protocol notes derived from reverse engineering

Helianthus uses the `CC0-1.0` lane only for independently recorded facts or
derived knowledge that the contributing repository is entitled to publish.

Project intent:

- once Helianthus publishes reverse-engineered protocol knowledge as public
  protocol documentation, it should remain publicly reusable
- Helianthus should not later try to close that protocol knowledge back up
- the community should be free to copy, mirror, extend, validate, and republish
  that knowledge

CC0 applies only to the Helianthus-authored artifact carrying it. It does not
grant or imply rights in a vendor specification, trademark, patent, firmware,
private capture, confidential material, certification program, or other
third-party content. Do not copy restricted source text or private evidence into
a CC0 artifact. When the right to publish or redistribute a source is unknown,
record that state as unknown and route it for qualified review before publishing.

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

## 3. Public Software And Separate Components

Helianthus public repositories are independent open-source software components.
The repository license file controls each component.

The following software is part of the public 0.7 scope:

- EEBUS native support and its public output binding;
- the public Matter output binding;
- SemReg contracts, Gateway composition, and their declared public consumers.

EEBUS and Matter software work does not depend on the private Helianthus hardware
repository. Its public scope does not mean every binding is already implemented,
packaged, conformant, certified, or physically verified; use the
[software maturity matrix](./profile/maturity-matrix.md) for current evidence.

Separate components may exist around the public software, for example:

- private hardware design;
- commercial managed services around Helianthus
- proprietary operational tooling or compliance layers

Those examples do not move public EEBUS or Matter software into a proprietary
lane. A component remains separate only when its code and rights are actually
separate. Changes merged into a public Helianthus repository remain governed by
that repository's public license.

## 4. Certification, Trademarks, And Vendor Rights

Software implementation is separate from product certification, trademark
programs, protocol conformance programs, patent rights, and vendor approval.
Helianthus does not claim any of those statuses merely because code, a decoder,
an offline replay, or a public mapping exists.

- Matter and EEBUS names remain subject to their respective owners' rights and
  program rules.
- A public protocol mapping is not a certification or conformance result.
- A public device profile is not vendor approval or a patent license.
- Certification, redistribution limits, and other third-party rights are
  **unknown** unless an applicable public record states them for the exact
  artifact and version.

Unknown rights or status require qualified review before publication or an
external claim. This document makes no legal conclusion about a third party's
material.

## 5. Third-Party Dependencies And Notices

Third-party code remains under its own license. Preserve the corresponding
license, notice, attribution, and source-offer obligations when redistributing a
Helianthus build. The source-linked inventory for the current public Gateway and
package anchors is in [THIRD_PARTY.md](./THIRD_PARTY.md). Repository and
dependency license files remain authoritative over that summary.

## 6. Community Freedom

The community remains free to build independent software, integrations, and
competing or complementary public Matter and EEBUS implementations subject to
the applicable licenses and third-party rights.

## 7. Contributor Inbound Policy

By submitting material for inclusion in Helianthus, a contributor confirms that
the submitted material can be published under the license already declared by
the destination repository or documentation lane:

- independently recorded protocol facts in the repository's CC0 lane;
- implementation code and implementation-specific documentation in the
  repository's open-source lane.

This is an inbound contribution policy. As of 20 September 2026, no separate
Helianthus contributor license agreement, copyright-assignment document, or CLA
acceptance mechanism was verified in the public organization repository. Do not
call this policy a CLA, and do not infer a copyright transfer or separate
commercial grant from a pull request.

The issue-template checkbox acknowledging this policy is an intake-policy
acknowledgement. It is not a standalone CLA or a verified CLA acceptance
mechanism.

Contributors must not submit material they are not entitled to publish under the
destination license. Restricted specifications, third-party code, firmware,
captures, trademarks, patents, and confidential material retain their own rights
and require a verified publication basis.

## 8. Copyright Note

This document explains how public material may be accepted and published. It
does not itself transfer copyright, relicense a repository, grant third-party
rights, or certify a product. Any future CLA, copyright assignment, relicensing,
or certification claim requires separate explicit scope, an actual acceptance
mechanism where applicable, and qualified review.

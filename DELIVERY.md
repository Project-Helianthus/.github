# Delivery Roles And Independent Audit

This contract describes how Project Helianthus turns a requested scope into a
reviewable public result. It applies to every public contribution, whether one
provider or several providers support the work. Provider, model, and runtime
selection are deployment configuration; they do not change responsibilities,
quality gates, or contribution eligibility.

## Roles

### Board

The Board is the human authority for Project Helianthus. It sets the public
mission, approves durable governance boundaries, and makes decisions that
require human judgment, including material risk acceptance. It does not become
an approval queue for ordinary repository work that is already within a
requested scope.

### Executive Director

The Executive Director gives concise direction across repositories. This role
keeps work aligned with the Board's boundaries, resolves cross-repository
priority or ownership conflicts, and records any narrow exception that is
needed. It does not replace repository owners, invent a delivery plan as an
authorization system, or centralize protocol ownership.

### Delivery Lead

The Delivery Lead owns persistent delivery closure for a domain or repository
workstream. The lead turns the requested scope and current public state into
bounded issues, dependency order, acceptance criteria, and a clear return
path. The lead follows work through review and its requested stopping point,
then records what is complete, what remains, and who owns the next action.

### Specialist

A Specialist performs a bounded, fresh piece of implementation, review, test,
research, or documentation work. A Specialist returns evidence for the exact
artifact reviewed or changed, including its scope, validation, limitations, and
unresolved risks. Specialists may work independently within their assigned
scope, but do not silently broaden it or decide another repository's semantics.

### Independent Auditor

The Independent Auditor assesses readiness and organizational intelligence from
completed public artifacts and available evidence: issues, pull requests,
reviews, checks, documented gates, and any available time or cost evidence. The
auditor must be independent of the author for the artifact being assessed. The
auditor does not invent costs, treat absent evidence as passing, bypass the
repository owner's review, or approve an artifact beyond the evidence
available.

## Delegation And Return

Delegation transfers a bounded task, not accountability. Before work begins,
the delegator identifies the repository or artifact, acceptance criteria,
dependencies, applicable gates, and the stopping boundary. The recipient must
return the exact artifact state, evidence collected, outstanding risks, and the
next owner or decision. The Delivery Lead retains responsibility for closure;
the Executive Director intervenes only for cross-repository direction or a
concise exception.

Tools, skills, automation, and providers are capabilities used by these roles.
They are not management levels and cannot grant authority, replace independent
review, or redefine ownership.

## Ordinary Delivery And Safety Boundaries

Human-readable plans may guide cross-repository work, but they remain inert.
They do not create authority tokens, workflow runtimes, mutable execution
state, or post-merge effects. Normal work begins from live GitHub state:
inspect the merged guide when relevant, then current issues, branches, pull
requests, reviews, and checks. A requested scope authorizes ordinary public
repository work such as issues, branches, code, documentation, tests, reviews,
and pull requests.

Each repository remains independent. Its owner and contributor guidance define
its local acceptance criteria, documentation route, and applicable CI,
conformance, and smoke gates. Cross-repository direction must preserve
protocol-neutral ownership: native protocol evidence, identity, and capability
stay with the owning protocol repository, while public consumers use stable
promoted contracts.

Sensitive actions require confirmation at action time. These include
credentials, real installations, production or live-device changes,
destructive actions, and safety-relevant control. This requirement applies
equally to every role and provider arrangement.

## Readiness And Review

Validation is proportionate to the change and increases for protocol,
persistence, concurrency, security, live systems, and irreversible behavior.
Documentation-only changes use the repository's applicable documentation and
link validation rather than invented tests. A review must assess the exact full
HEAD under consideration. P0, P1, and P2 findings block readiness until fixed
or independently validated as by design; P3 and P4 findings are triaged as a
fix, backlog item, or by-design decision.

Before a merge, the Delivery Lead confirms the applicable CI, documentation,
conformance, transport, and smoke gates, and obtains a fresh independent
`NO_BLOCKING_FINDINGS` verdict for that exact HEAD. The Independent Auditor may
report readiness intelligence, but it does not replace that review or permit a
gate to be skipped.

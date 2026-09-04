# Contributing To Project Helianthus

These rules are the default contributor contract for Helianthus repositories.
Repository-specific instructions may tighten them.

The [delivery-role and independent-audit contract](./DELIVERY.md) explains how
human authority, cross-repository direction, delivery closure, bounded work,
and independent readiness assessment fit together. It applies equally whether
one provider or several providers support the work.

## Start With The Right Workstream

Cross-repository, milestone, architecture, protocol, and API work may use a
merged human-readable guide from
[`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans).
The guide records scope, dependencies, milestones, acceptance criteria, and
applicable gates. It is not a lock, authorization token, workflow runtime, or
substitute for current GitHub state.

Before starting or resuming guided work:

1. read the guide from `main`
2. inspect current issues, branches, PRs, reviews, and checks
3. reconcile actual state
4. proceed one repository at a time in dependency order

Small one-repository changes may start directly in the target repository.

## Issue Standard

Use this structure for implementation issues:

```markdown
## What
One sentence describing what this issue implements.

## Why
How it connects to architecture, rollout, or user value.

## Acceptance Criteria
- [ ] Specific, testable condition 1
- [ ] Specific, testable condition 2
- [ ] Tests or validators cover the change
- [ ] CI green
- [ ] Smoke test required: YES / NO

## Dependencies
- Depends on issue #X (if any)
```

Use one issue, one `issue/<id>-<slug>` branch from current `origin/main`, and
one PR per repository for the active workstream.

## Pull Request Requirements

Each PR should include:

- the linked issue
- the merged guide link when the workstream is guide-backed
- commands run and relevant evidence or artifacts
- explicit test/validation and smoke status
- explicit doc-gate and knowledge-capture status
- an explicit `PASS` or `FAIL` verdict

Review is blocker-driven against the exact current HEAD. P0-P2 findings must be
resolved or independently validated as by-design before merge. P3/P4 findings
are triaged and do not become blockers merely because they exist.

## Licensing Boundary

The authoritative explanation of the Helianthus licensing boundary lives in
[`LICENSING.md`](./LICENSING.md).

Contributor-facing summary:

- material merged into Helianthus must be publishable under the applicable
  public licensing lane
- reverse-engineered protocol knowledge belongs in the public-domain lane
- implementation-specific Helianthus work belongs in the repository OSS lane
- separate proprietary components may exist, but Helianthus-side merged changes
  remain public under the applicable repository license

## Doc-Gate And Knowledge Routing

Doc-gate is mandatory when a change affects architecture, public or semi-public
APIs, protocol behavior, semantic behavior, state machines, or reverse-
engineered knowledge.

Route knowledge to its owner:

- eBUS material -> [`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus)
- EEBUS/SHIP/SPINE material -> [`helianthus-docs-eebus`](https://github.com/Project-Helianthus/helianthus-docs-eebus)
- MODBUS/SunSpec material -> [`helianthus-docs-modbus`](https://github.com/Project-Helianthus/helianthus-docs-modbus)
- generic CAN/SocketCAN material -> [`helianthus-docs-canbus`](https://github.com/Project-Helianthus/helianthus-docs-canbus)
- GREE VRF CAN/UART material -> [`helianthus-docs-gree-vrf`](https://github.com/Project-Helianthus/helianthus-docs-gree-vrf)
- another protocol -> its corresponding public docs repository or documented
  public source until a dedicated docs repository exists
- cross-protocol semantics -> the owning semantic/platform documentation, with
  links to each native evidence source

Do not use `helianthus-docs-ebus` as a universal protocol knowledge store.

Every PR must state one of:

- `Docs updated`: this PR or a linked docs PR captures the new knowledge
- `No new knowledge captured`: with a short rationale

## Statement Quality And Safety

Use `Proven` for current evidence, `Hypothesis` for claims awaiting proof,
and `Unknown` when not established. Preserve raw/native evidence and explicit
projection loss.

Ask for action-time confirmation before credentials, real installations,
production or live-device mutations, destructive actions, or similarly
high-risk changes. Ordinary issue, branch, code, docs, test, and PR work needs
no additional authorization artifact.

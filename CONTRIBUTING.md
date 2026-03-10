# Contributing To Project Helianthus

These rules are the default contributor contract for Helianthus repositories.
Repository-specific instructions may tighten them, but should not weaken them.

## Start With The Right Workstream

Use the
[`helianthus-execution-plans`](https://github.com/Project-Helianthus/helianthus-execution-plans)
repository first when the work is:

- cross-repo
- milestone-driven
- architecture-changing
- protocol-changing
- API-changing

Those workstreams should not enter code repos without a locked canonical plan.

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
- [ ] Unit tests cover the implemented code
- [ ] CI green
- [ ] Smoke test required: YES / NO

## Dependencies
- Depends on issue #X (if any)
```

## Pull Request Requirements

Each PR should include:

- the linked issue
- the canonical plan link when the workstream requires a locked plan
- commands run
- relevant evidence or artifacts
- explicit doc-gate status
- explicit knowledge-capture status
- an explicit `PASS` or `FAIL` verdict

## Licensing Boundary

The authoritative explanation of the Helianthus licensing boundary lives in
[`LICENSING.md`](./LICENSING.md).

Contributor-facing summary:

- material merged into Helianthus must be publishable under the applicable
  public licensing lane
- reverse-engineered protocol knowledge belongs in the public-domain lane
- implementation-specific Helianthus work belongs in the repository OSS lane
- separate proprietary components around Helianthus may exist, but Helianthus-
  side merged changes remain public under the applicable repository license

If the project later adopts repository-specific CLA or copyright-assignment
terms, they should be added explicitly alongside `LICENSING.md`.

## Doc-Gate

Doc-gate is mandatory when a change affects:

- architecture
- public or semi-public APIs
- protocol behavior
- semantic behavior
- state machines
- reverse-engineered knowledge

Reusable knowledge belongs in
[`helianthus-docs-ebus`](https://github.com/Project-Helianthus/helianthus-docs-ebus).

## Knowledge-Capture Gate

Every PR must answer one of these two statements explicitly:

- `Docs updated`: the PR or a linked merged docs PR captures the new knowledge
- `No new knowledge captured`: with a short rationale

Reviewers should not accept this implicitly.

## Statement Quality

Prefer precise, falsifiable statements over vague confidence language.

Use:

- `Proven` when backed by evidence in the current change cycle
- `Hypothesis` when still awaiting proof
- `Unknown` when not established

When verification is idempotent, prefer idempotent verification. When a step is
non-idempotent or mutating, declare that before execution.

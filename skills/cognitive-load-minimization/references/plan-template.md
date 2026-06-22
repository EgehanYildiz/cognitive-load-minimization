# Implementation Plan Template

Phase 6, only if the user accepts the offer. Turns the **audited** report (surviving + revised findings, plus branch-A preferences) into a phased, executable plan. Write it in the detected language. Self-contained — no external planning skill required.

## Principles

- Plan only the fixes that survived the audit (and the directions the user chose in branch A). Dropped findings do not appear.
- Order by **severity × ease**: ship the Critical-and-easy fixes first (quick wins build momentum and let you measure early), defer Critical-but-deep work into its own phase.
- Every task names the exact surface/file/component, the concrete change, and how it will be verified.
- Where a fix moves complexity onto the system (Tesler-correct), say what the system now absorbs (e.g. "derive company name from email domain" → a backend enrichment step).

## Structure

```
# Implementation Plan: [surface]

## Goal
[One line: the load reduction this plan delivers, tied to the metric it should move.]

## Phase 1 — Quick wins (shippable now)
- [ ] [Surface/component]: [concrete change] — verify: [how]
- [ ] ...

## Phase 2 — Structural changes (design/eng investment)
- [ ] [Surface/component]: [concrete change] — verify: [how]
- [ ] [Note any complexity the system now absorbs]

## Phase 3 — Validation
- [ ] [The measurement from the report's "How to validate": A/B, drop-off, first-click, field-level abandonment]
- [ ] [Success threshold]

## Out of scope / deferred
[Findings intentionally not addressed now, with why.]
```

After the plan is accepted, proceed to normal development (Phase 7). Do not start coding before the plan is accepted.

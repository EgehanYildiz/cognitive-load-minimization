# Report Template

The single `.md` the orchestrator writes in Phase 3 and rewrites in Phase 5. Write it in the detected language. Lead with the highest-severity item. Make every recommendation specific and shippable — "reduce the primary nav from 9 items to 5 by grouping X, Y, Z under 'Resources'" beats "simplify navigation."

```
# Cognitive Load Audit: [surface]

## Frame
[Phase 1 summary: surface, primary goal, primary action, user context, assumptions.]

## Findings by lens (by severity)
### Lens 1 — IA & Navigation
For each finding: **[Severity] Title**
- What: [the issue]
- Costs the user: [the extraneous load] (principle: [named law])
- Load type: [intrinsic | extraneous | germane]
- Fix: [concrete change]

### Lens 2 — Visual Hierarchy & Attention
[same structure]

### Lens 3 — Content & Language
[same structure]

### Lens 4 — Interaction & Flow
[same structure]

## Copy rewrites
| Where | Before | After | Why |
(Only for surfaces with copy. Concrete, shippable.)

## IA / flow changes
[Reorganized menus, reduced steps, regrouped choices — show before → after structure.]

## Quick wins vs. deeper work
[2–4 shippable today; 1–3 needing design/eng investment.]

## Eliminated (false positives)        ← added/updated in Phase 5 only
| Finding | Lens | Why dropped |
(Every finding the audit dropped, with its reason. Never delete silently.)

## How to validate
[Per the "measure where possible" guardrail: task-completion time, drop-off rate, first-click test, field-level abandonment, etc.]
```

## Severity normalization (Phase 3)

Each lens proposed its own severity seeing only its own area. Re-rank across all findings using:
- **Load impact** — how much extraneous effort it adds (a confusing primary CTA ≫ a long footer).
- **Reach** — share of users who hit it (a homepage issue ≫ a settings-subpage issue).
- **Funnel position** — friction early or at the moment of commitment costs more than friction afterward.

Buckets: **Critical / High / Medium / Low.** Be honest about Low items — listing trivia as if it mattered is itself cognitive load on the reader.

# Interview — branch A

Runs only if the user chose branch A in Phase 4. Purpose: walk the recommended fixes together, one at a time, and capture for each whether the user wants that fix, a different direction, or to drop it. The captured preferences are fed into the Phase 5 auditors.

## How to run it

Interview the user relentlessly about the recommended fixes until you reach shared understanding. Walk down each finding's fix one-by-one, resolving dependencies between decisions. For each fix, provide your recommended answer.

Ask one question at a time.

If a question can be answered by looking at the artifacts instead of asking, look at the artifacts.

## What to capture per fix

For each recommended fix, record:
- **decision** — accept this fix / take a different direction / drop it
- **direction** — if different: what the user wants instead
- **notes** — any constraint the user surfaced (tech limit, brand rule, business reason)

## Handing off to the audit

Pass the captured decisions into every adversarial auditor's prompt (see `audit-loop.md`). An auditor that knows "the user accepted fix X but wants it done via Y" can verify severity and fix against what the user actually intends, so the interview is never wasted. Findings the user chose to drop are still audited (the user may have dropped a real one) — but record the user's intent alongside the verdict.

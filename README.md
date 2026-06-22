# cognitive-load-minimization

[![skills.sh](https://skills.sh/b/EgehanYildiz/cognitive-load-minimization)](https://skills.sh/EgehanYildiz/cognitive-load-minimization)

A self-contained [Agent Skill](https://agentskills.io) that audits and reduces the **cognitive load** of any product surface — a landing page, a SaaS dashboard, an onboarding flow, a signup form, a navigation menu, a pricing page, marketing copy, or a whole multi-step funnel.

It removes **extraneous** load (effort caused by *how* something is presented) so a user's limited working memory is spent on the actual task — not on decoding the interface.

## Install

```bash
npx skills add EgehanYildiz/cognitive-load-minimization
```

## What makes it different

Most "UX review" prompts have one model eyeball everything at once — and the lenses interfere (the layout judgment colors the copy judgment, fatigue sets in, coverage gets amortized). This skill is an **orchestration**: it fans out one fresh subagent per lens, in parallel, then adversarially verifies the findings before you ever see them.

### The eight phases

0. **Detect language** — every output (report, questions, plan, *and* the subagent prompts) matches the user's language automatically.
1. **Context investigation** — establish the frame: surfaces, primary goal + single primary action, user context, artifacts.
2. **Parallel lens fan-out** — four fresh subagents run at once, one per lens (MECE by surface concern):
   - **IA & Navigation** (Hick, serial position, scent, recognition>recall)
   - **Visual Hierarchy & Attention** (von Restorff, Gestalt, F/Z, whitespace)
   - **Content & Language** (skim test, scent, microcopy)
   - **Interaction & Flow** (Fitts, progressive disclosure, Postel, peak–end, Zeigarnik, goal-gradient)
3. **Assemble report** — one `.md`, findings grouped by lens, severity normalized across lenses.
4. **A/B choice** — interview the fixes together, or review on your own then go straight to audit.
5. **Adversarial audit** — one fresh skeptic per lens tries to *refute* each finding (default false-positive when unsure). Findings come back confirmed / revised / dropped; dropped ones are **logged with reasons, never silently deleted**. Repeats until convergence.
6. **Implementation plan** — offered, not forced.
7. **Development** — only after the plan is accepted.

The adversarial audit is the point: it breaks the producing agent's bias, so plausible-but-wrong findings and inflated severities don't survive.

## Grounding

Every recommendation cites a named law/heuristic (Sweller's Cognitive Load Theory, Hick, Miller, von Restorff, Gestalt, Fitts, Tesler, Postel, Jakob, peak–end, Zeigarnik, goal-gradient, information foraging, satisficing…). Taste-only suggestions are labeled as taste, not research. The full substance lives in `skills/cognitive-load-minimization/references/`.

## Self-contained

No dependency on any other skill. Works on any runtime that can dispatch subagents (Claude Code, Codex, Copilot CLI, Gemini CLI). Clone it anywhere and it runs.

## Structure

```
SKILL.md              # 8-phase orchestration
references/
  principles.md       # the theory (named laws & heuristics)
  audit-checklist.md  # operational checks (Pass A–D)
  lenses.md           # the four parallel subagent briefs + output schema
  audit-loop.md       # adversarial false-positive elimination
  interview.md        # branch-A interview
  report-template.md  # single-report template + severity normalization
  plan-template.md    # implementation plan template
LICENSE · README.md
```

The skill lives at the repo root (the directory name matches the skill `name`), so `npx skills add EgehanYildiz/cognitive-load-minimization` resolves it directly.

## License

MIT — see [LICENSE](LICENSE).

---
name: cognitive-load-minimization
description: Audit and reduce the cognitive load of any product surface — a landing page, a SaaS dashboard, an onboarding flow, a signup form, a navigation menu, a pricing page, marketing copy, or a whole multi-step funnel. Use this skill whenever the user wants something "simpler," "clearer," "easier to scan," "less overwhelming," "more intuitive," or "higher converting"; whenever they ask for a UX review, a copy review, an IA/navigation review, or a friction audit; or whenever they share screenshots, component code, sitemaps, menu structures, or marketing copy and want it optimized for how real users actually perceive and decide. Trigger it even when the user doesn't say the words "cognitive load" — phrasings like "why is this confusing," "people drop off here," "make the flow smoother," or "tighten this copy" all qualify.
---

# Cognitive Load Minimization

Reduce the mental effort a user must spend to perceive, understand, and act on a product surface. The goal is never "minimal" for its own sake — it is to remove **extraneous** load (effort caused by *how* something is presented) so the user's limited working memory is spent on the actual task, not on decoding the interface.

This skill is **self-contained**: everything it needs lives in `references/`. It works on any runtime that can dispatch subagents — no other skill needs to be installed.

## Core mental model

Users do not read; they **forage**. They arrive with a goal, skim for "information scent," commit attention only when something signals relevance (the isolation / von Restorff "catch"), then engagement escalates. Every decision serves this loop: strong scent, obvious next step, exactly one thing that should catch the eye actually does, everything else quiet.

Three kinds of load (Sweller):
- **Intrinsic** — inherent task difficulty. *Managed* (chunking, sequencing), not removed.
- **Extraneous** — load created by presentation. **This is the target. Cut it aggressively.**
- **Germane** — productive effort that builds understanding. Preserve it; flag it; never silently cut it.

The substance — every named law, theory, and heuristic — lives in `references/principles.md`. The operational lens definitions live in `references/lenses.md`. Read them; citing principles by name makes recommendations defensible rather than opinion.

## How this skill runs

This is an **orchestration** skill. You (the agent reading this) are the **orchestrator**. You do NOT personally audit all four lenses in one pass — that is the exact failure this skill exists to fix (lenses interfere when one mind holds them all at once). Instead you fan out one fresh subagent per lens, in parallel, then assemble and adversarially verify their findings.

Run the eight phases below **in order**. Create a todo per phase so none is silently skipped.

### Phase 0 — Detect the language

Detect the language of the user's request from the conversation so far. **Every output** — the frame, the report, interview questions, the plan, AND the instructions you put inside each subagent's prompt — must be in that language. Do not ask the user which language; infer it. (Turkish request → everything Turkish; English → everything English.) Inject a `Respond in <language>.` line into every subagent prompt you dispatch.

### Phase 1 — Context Investigation (you, alone)

Establish the frame before judging anything. This phase is NOT delegated — every lens subagent receives this frame as input, so it must exist first. Gather and state explicitly:

1. **What surface(s)** are in scope — single screen, a flow, copy, a menu/IA, the whole product.
2. **The primary user goal** on each surface, and the **single primary action** you want them to take. No clear primary action = already a finding.
3. **The user's context** — device (mobile changes everything), expertise, emotional state (anxious checkout vs. relaxed browse), new vs. returning.
4. **Available artifacts** — screenshots/mockups (view images directly, rasterize PDFs), component/markup code, copy, sitemap/menu tree, any analytics or drop-off data. Ask for what's missing only if it materially changes the audit; otherwise proceed and note assumptions.

Summarize the frame back in 3–5 lines before continuing. This prevents optimizing the wrong thing.

### Phase 2 — Parallel lens fan-out (four subagents, at once)

Dispatch **four subagents in parallel** — one per lens — using your platform's parallel-agent mechanism (send them in a single batch so they run concurrently). Each subagent gets: the Phase 1 frame, the artifacts, the `Respond in <language>` line, and its lens brief from `references/lenses.md`. Each returns **structured findings only** (the schema is in `references/lenses.md`) — it does NOT write any file. You are the only writer.

The four lenses (MECE by surface concern; each carries its own laws):
- **Lens 1 — IA & Navigation** (Hick, serial position, scent, recognition>recall)
- **Lens 2 — Visual Hierarchy & Attention** (von Restorff, Gestalt, F/Z, whitespace, aesthetic-usability)
- **Lens 3 — Content & Language** (skim test, scent, microcopy)
- **Lens 4 — Interaction & Flow** (Fitts, progressive disclosure, Postel, peak–end, Zeigarnik, goal-gradient)

**Every lens runs. No exceptions.** After the batch returns, confirm all four came back. If any subagent failed or returned nothing, re-dispatch it. Do not proceed to Phase 3 with fewer than four lenses' findings, and do not substitute your own pass for a missing lens — the whole point is the fresh, isolated context per lens.

### Phase 3 — Assemble the first report (you, alone)

Collect the four structured result sets and write ONE markdown file: `cognitive-load-audit-<surface>.md` in the working directory. Each finding goes under its lens heading, carrying its principle, cost-to-user, load_type, severity, and fix. Then **normalize severity across lenses** — a lens only sees its own area, so re-rank using global reach and funnel position so a "High" means the same thing everywhere. Use the report template in `references/report-template.md`.

### Phase 4 — Offer the A/B choice (always)

Present the assembled report path to the user and offer exactly this choice (in the detected language):

> "I've researched from each cognitive-load lens and compiled my findings into `<file>`. We can (A) go through the recommended fixes together — I'll interview you on which fixes you want vs. other directions — or (B) you review on your own and, once you approve, I move straight to the audit step where we make sure none of the findings are false positives and tighten everything. Which would you like?"

**Always offer this.** Do not skip to fixes, and do not pick for the user. Wait for their answer.

### Phase 5 — Audit (runs in BOTH branches — never skipped)

The audit is a quality gate, not optional. It runs whether the user chose A or B.

- If the user chose **A**, first run the interview (`references/interview.md`): walk the fixes one at a time, capture which fixes they want vs. alternative directions. Feed those preferences into the auditors.
- Then run the audit loop (`references/audit-loop.md`): dispatch **one fresh adversarial auditor subagent per lens, in parallel**, each tasked to *refute* its lens's findings (default-skeptical: if unsure, mark false-positive). Each finding comes back `confirmed` / `revised` / `dropped` with a reason. Rewrite the report keeping survivors and revisions; list dropped findings under "Eliminated (false positives)" with reasons — **never silently delete a finding.** Repeat rounds until a full round produces no new drops/revisions (convergence).

### Phase 6 — Offer the implementation plan

Once the audited report is final, offer: "Next is the implementation plan — want me to write it?" If yes, write it using `references/plan-template.md` (audited findings + approved fixes → phased plan). Do not auto-start coding.

### Phase 7 — Development

Only after the plan is accepted, begin normal development.

## Guardrails

- **Don't confuse minimal with usable.** Stripping necessary information *raises* load by forcing recall or guesswork. Target extraneous load only.
- **Respect Jakob's Law.** Users expect your product to work like the others they know. "Innovative" navigation is often just unfamiliar — i.e. high-load. Justify any departure.
- **Beauty is not the metric.** Aesthetic-usability effect means polish can *mask* load in testing. Fix structure first, then make it pretty.
- **Ground claims.** Tie every finding to a named principle from `references/principles.md`. Taste-only recommendations must be labeled as taste, not research.
- **Measure where possible.** Recommend a validation (task-completion time, drop-off rate, first-click test) rather than asserting the fix works.

## Red flags — you are drifting from this skill if:

- You audited all four lenses yourself in one pass instead of dispatching four parallel subagents → **stop, fan out.**
- You produced fewer than four lenses' findings → **re-dispatch the missing lens; never fill it in yourself.**
- You wrote findings straight into your chat answer instead of into the `.md` file → **stop, write the file.**
- You skipped the A/B offer and went straight to fixing → **stop, offer the choice.**
- You skipped the audit because findings "look solid" → **stop, run the adversarial audit; that judgment is exactly what the audit exists to check.**
- You deleted a weak finding silently → **stop, move it to "Eliminated" with a reason.**
- You answered in English for a Turkish request (or vice versa) → **stop, match the user's language everywhere, including subagent prompts.**

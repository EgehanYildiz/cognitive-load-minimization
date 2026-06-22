# Lenses — the four parallel subagent briefs

This is the SSOT for Phase 2. Four lenses, mutually exclusive by surface concern, collectively covering the whole theory. Each lens = one subagent, dispatched in parallel. Each subagent reads `principles.md` (the theory) and the matching pass in `audit-checklist.md` (the operational checks), then returns structured findings — **nothing else, and no files**.

## What every lens subagent prompt must contain

When you (orchestrator) build a lens subagent's prompt, include all of:

1. `Respond in <detected language>.`
2. The **Phase 1 frame** (surface, primary goal + primary action, user context, assumptions).
3. The **artifacts** (paste copy/markup; attach or reference screenshots; give the sitemap/menu tree).
4. The lens's **focus + which checklist pass + which principles sections** (table below).
5. The **output contract** (below) — emphasize: findings only, no prose preamble, no file writes.
6. This instruction: *"Only report what your lens covers. If a problem belongs to another lens, skip it — a parallel agent owns it."* (keeps lenses MECE, prevents duplicate findings.)

## The four lenses

| Lens | Focus | Checklist pass | Principles sections | Laws it carries |
|---|---|---|---|---|
| **1 — IA & Navigation** | choice count & grouping, menu breadth/depth, label clarity, scent, findability, recognition vs recall | Pass A | §2, §4 (Hick, Miller), §5 (recognition>recall), §6 (serial position) | Hick, Miller, serial position, information scent, recognition>recall |
| **2 — Visual Hierarchy & Attention** | scan path (F/Z), single focal point, contrast/size/color, whitespace, Gestalt, alignment | Pass B | §3, §5 | von Restorff, Gestalt (incl. continuity + closure), visual hierarchy, whitespace, aesthetic-usability |
| **3 — Content & Language** | front-loaded value, scannable structure, reading level, jargon, microcopy, CTA verbs | Pass C | §2, §3 | skim/F-pattern, scent, satisficing, "don't make me think" |
| **4 — Interaction & Flow** | steps & fields, smart defaults, progressive disclosure, error prevention, perceived progress, forgiving input, mobile reach | Pass D | §4 (Fitts, Tesler, Postel), §5 (progressive disclosure), §6 (Zeigarnik, peak–end, goal-gradient) | Fitts, Tesler, Postel, progressive disclosure, Zeigarnik, peak–end, goal-gradient |

Load classification (intrinsic/extraneous/germane, the old "Pass E") is **not** a fifth lens — every finding carries a `load_type` field, so each lens classifies its own findings inline.

## Output contract (every finding)

Each lens subagent returns a list of findings. Each finding is an object:

```
lens          — which lens (e.g. "IA & Navigation")
title          — short label
what           — the issue, concretely
principle      — the named law/heuristic it violates (e.g. "Hick's Law", "von Restorff")
cost_to_user   — the extraneous effort it imposes
load_type      — intrinsic | extraneous | germane
severity       — the lens's proposed Critical | High | Medium | Low (orchestrator re-normalizes later)
fix            — a concrete, shippable change
```

A finding with no named `principle` is not shippable — either name the principle or label it explicitly as taste, not research. If a lens finds nothing real in its area, it returns an empty list and says so — padding the list with trivia is itself cognitive load on the reader.

## Why parallel + isolated

One mind auditing all four lenses in sequence lets the lenses interfere — the IA judgment colors the visual judgment, fatigue sets in by the fourth pass, and coverage gets amortized ("I basically covered that"). Four fresh contexts, each seeing only its own lens, removes that interference and guarantees every lens gets full attention. That isolation is the entire reason this skill fans out instead of looping.

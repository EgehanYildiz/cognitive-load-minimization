# Principles: The Research Behind Cognitive Load

The substance the audit rests on. Cite these by name — it turns recommendations from taste into defensible design rationale.

## Contents
1. Cognitive Load Theory (the foundation)
2. How people actually behave: foraging, skimming, satisficing
3. The "skim then it catches your eye" arc, explained
4. The UX laws (decision, memory, motion, expectation)
5. Attention & perception (hierarchy, salience, grouping)
6. Memory effects worth exploiting
7. Canonical sources

---

## 1. Cognitive Load Theory (the foundation)

John Sweller, 1988 (educational psychology, later adopted wholesale by UX). Working memory is small and easily overloaded; long-term memory is effectively unlimited. Performance collapses when total load exceeds working-memory capacity. Three components:

- **Intrinsic load** — the inherent difficulty of the material/task. A tax return is intrinsically harder than a newsletter signup. You can *manage* it (chunk it, sequence it, scaffold it) but not eliminate it.
- **Extraneous load** — load imposed by *how* information is presented: clutter, poor hierarchy, jargon, inconsistent patterns, unnecessary choices. **This is the entire target of UX work.** Every point of extraneous load you remove frees capacity for the task.
- **Germane load** — effort the user spends building durable understanding (schemas). This is *good* load. Stripping it to make something "easier" can leave users unable to use the product independently. Preserve it; flag it; never silently cut it.

Operational rule: classify every issue you find. Cut extraneous, manage intrinsic, protect germane.

## 2. How people actually behave

**Information Foraging Theory** (Pirolli & Card, Xerox PARC, 1990s). People seek information the way animals forage for food: they follow **information scent** — cues (link text, headings, labels, imagery) that suggest a path leads to their goal — and abandon a "patch" when the scent weakens or a better patch appears. Strong scent = low load = users find things. Weak/misleading scent = users thrash, backtrack, and leave.

**Satisficing** (Krug, from Herbert Simon's term). Users do **not** weigh all options to pick the best. They pick the **first reasonable option** that seems good enough, because evaluating everything is expensive and "muddling through" usually works. Design consequence: the obvious path must be the good path. Don't rely on users reading everything before choosing — they won't.

**Banner blindness / "Don't make me think."** Users skim, ignore anything that looks like an ad or like decoration, and resent being made to stop and figure things out. Self-evident beats clever.

## 3. The "skim then it catches your eye" arc, explained

This is the exact behavior described as: hold the decision lightly → skim → *something catches the eye* → read more carefully → interest escalates. It is not one phenomenon but three stacked:

1. **The skim is foraging + the F-shaped pattern.** Eye-tracking (Nielsen/NN/g) shows users scan text-heavy pages in an F or E shape: a couple of horizontal sweeps near the top, then a vertical scan down the left edge. They are sniffing for scent, not reading. → Front-load meaning into the first two words of headings and the first sentence of blocks.

2. **The "BOOM, it catches the eye" is the von Restorff (isolation) effect plus visual salience.** An item that differs from its surroundings — in color, size, weight, motion, whitespace — is disproportionately noticed and remembered. This is *why* a single high-contrast primary button works and five competing buttons don't. The catch only happens if one thing stands out; if everything shouts, nothing does. → Give each view exactly one focal point, and spend your salience budget on it.

3. **The escalation is engagement compounding once scent is confirmed.** When the eye-catch turns out to be relevant (scent confirmed), the user shifts from skimming to reading and invests more attention — each confirmation lowers the perceived cost of the next step. → Reward the click immediately; confirm the user is on the right track at every step or the escalation reverses into a bounce.

Design takeaway: you are engineering a scent trail with one deliberate salience spike per decision point, and confirming relevance fast enough that engagement compounds instead of decaying.

## 4. The UX laws

**Hick's Law** — decision time increases (logarithmically) with the number and complexity of choices. More options = slower, harder decisions and more abandonment. Mitigate by reducing options, grouping/categorizing them, hiding advanced ones (progressive disclosure), and highlighting a recommended default. Caveat: don't over-aggregate to where users must drill through many shallow steps — that trades one load for another.

**Miller's Law** — working memory holds ~7±2 "chunks." Widely *misquoted* as a hard limit on menu items or list length; Miller's actual point was about chunking. The usable lesson is **chunk information into meaningful groups** (a phone number as 3-3-4, not 10 digits), not "never show more than 7 things."

**Jakob's Law** — users spend most of their time on *other* products, so they expect yours to work the same way. Familiar patterns carry near-zero learning load; novel ones impose it. Innovate on substance, conform on convention, and justify any deliberate departure.

**Fitts's Law** — time to hit a target is a function of its distance and size. Make primary actions large and close to where the cursor/thumb already is; mobile thumb-zones matter. Tiny or far-apart targets add motor + cognitive load.

**Tesler's Law (conservation of complexity)** — every system has irreducible complexity; the only question is who absorbs it, the user or the system. Good design moves complexity off the user and into the product (smart defaults, inference, automation). When you can't remove a tradeoff, name who pays.

**Postel's / forgiveness** — be liberal in what you accept from users (parse messy phone/date/card input rather than rejecting it). Rejection on a technicality is pure extraneous load.

## 5. Attention & perception

**Visual hierarchy** — size, weight, color, contrast, position, and whitespace tell the eye what matters and in what order. A flat hierarchy (everything equally emphasized) forces the user to do the prioritizing the designer should have done.

**Gestalt principles** — the mind groups by **proximity** (near things feel related), **similarity** (alike things feel related), **common region** (shared container/background), **closure**, and **continuity**. Use them to make structure *perceptible without reading* — e.g., spacing alone can replace dividers and labels, cutting load.

**Whitespace / signal-to-noise** — empty space is not wasted; it isolates the signal and is part of how the von Restorff catch works. Dense layouts raise extraneous load even when every element is individually justified.

**Aesthetic-usability effect** — users perceive attractive interfaces as more usable and are more forgiving of minor issues. Useful, but a trap during evaluation: polish can hide structural load. Fix structure first; let beauty be the finish, not the patch.

**Progressive disclosure** — show only what's needed now; reveal advanced/rare options on demand. Keeps the default view low-load while preserving power for those who need it.

**Recognition over recall** — recognizing is far cheaper than recalling. Show options, recently used items, and contextual hints instead of making users remember commands, codes, or where things live. (NN/g heuristic #6.)

**Error prevention over correction** — preventing an error costs the user less than the stop-read-fix loop a good error message triggers. Constrain inputs, validate inline, parse forgivingly (Postel). For confirmations specifically: use them *sparingly* — confirming routine, reversible actions trains a "click yes" reflex (wolf-alarm / confirmation fatigue) that gets the one genuinely dangerous confirm dismissed too. Prefer **undo over confirmation** whenever the action can be reversed ("Deleted. Undo →" beats "Are you sure?"). (NN/g heuristic #5.)

## 6. Memory effects worth exploiting

- **Serial position effect** — first and last items in a series are best remembered. Put the most important nav/menu/list items at the ends, weakest in the middle.
- **Zeigarnik effect** — unfinished tasks stay mentally "open" and nag for completion. Progress indicators and checklists harness this to pull users through multi-step flows.
- **Peak–end rule** — people judge an experience by its most intense moment and its end, not its average. Invest disproportionately in the hardest step and the finish (e.g., a genuinely satisfying success/confirmation state).
- **Goal-gradient effect** — motivation increases near a goal. Show progress as already partly complete (the "endowed progress" trick) and momentum builds.

## 7. Canonical sources

For deeper reading and for naming sources in reports:

- Steve Krug, *Don't Make Me Think* — the practitioner bible on self-evidence and satisficing.
- Nielsen Norman Group (nngroup.com) — eye-tracking/F-pattern research, the 10 Usability Heuristics, and a large body of cognitive-load articles.
- John Sweller — Cognitive Load Theory (original papers).
- Pirolli & Card — Information Foraging Theory.
- *Laws of UX* by Jon Yablonski (lawsofux.com) — concise reference for Hick's, Jakob's, Fitts's, Miller's, Tesler's, von Restorff, etc.
- Edward Tufte — visual signal-to-noise and data-ink (for dense/data UIs).

> Note for the user: these are well-established, slow-moving foundations. If you want the *latest* NN/g articles or fresh benchmarks/figures on a specific point (e.g. current drop-off norms for checkout flows), that calls for a web search at audit time rather than relying on this file.

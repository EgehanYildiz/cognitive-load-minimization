# Audit Checklist

Operational checklist for Phase 2. Walk each pass deliberately. For every "no," capture: *what → which principle → cost to user → fix.* Not every item applies to every surface — skip what's irrelevant and say so rather than padding the report.

## Pass A — Information architecture & navigation

- [ ] Is there a clear primary action on this surface, and is everything else visibly subordinate to it?
- [ ] Top-level navigation: is the item count low enough to scan at a glance? If high, can items be grouped into meaningful categories (Hick's Law)?
- [ ] Are labels written in the **user's** words, not internal/brand jargon? Would a first-time visitor predict what's behind each one (information scent)?
- [ ] Breadth vs. depth: are users forced through many shallow clicks, or faced with one overwhelming menu? Find the balance.
- [ ] Can users tell where they are (current location), where they've been (visited), and where they can go? (Recognition over recall.)
- [ ] Are the most important items at the **start or end** of menus/lists (serial position effect), not buried mid-list?
- [ ] Is the structure consistent across the product, or do similar things live in different places on different screens?
- [ ] Search: present when the IA is large? Does it tolerate typos and synonyms?

## Pass B — Visual hierarchy & attention

- [ ] Does the natural scan path (F or Z) actually pass through the primary action and the key message — or does it miss them?
- [ ] Is there exactly **one** dominant focal point per view, or do multiple elements compete with equal weight (the "everything shouts, nothing stands out" failure)?
- [ ] Does the primary CTA win on contrast/size/color against everything around it (von Restorff)? Are secondary actions visibly de-emphasized?
- [ ] Is whitespace used to isolate the signal and group related items, or is the layout dense edge-to-edge?
- [ ] Do Gestalt cues (proximity, common region, similarity) make structure perceptible **without reading** labels or dividers?
- [ ] Continuity: does the eye flow along a natural line/alignment from one element to the next, or does the layout force jumps?
- [ ] Closure: are implied/partial shapes (an open card edge, a suggested grouping) enough — i.e. is anything fully drawn that an outline would carry, adding ink without information?
- [ ] Is type hierarchy real (clear steps between heading/subhead/body) or flat (everything roughly the same size/weight)?
- [ ] Is alignment consistent? Ragged alignment forces micro-effort on every scan.
- [ ] Color: does it carry meaning consistently, and is meaning ever conveyed by color *alone* (accessibility + load)?
- [ ] Motion/animation: does it guide attention, or distract and delay?

## Pass C — Content & language

- [ ] **Skim test:** read only the headings and the first sentence of each block. Does the gist survive? If not, front-load meaning.
- [ ] Do headings and link text start with the **most meaningful word** (users scan left edges)?
- [ ] Is the value proposition stated plainly and early, or buried under throat-clearing / "We are a leading provider of…"?
- [ ] Paragraphs short, sentences short, lists used where appropriate? Walls of text = abandoned text.
- [ ] Jargon, acronyms, internal terms — defined or removed? Reading level appropriate to the audience?
- [ ] **Microcopy:** are button labels specific verbs describing the outcome ("Create my account") rather than generic ("Submit", "OK", "Click here")?
- [ ] Are form labels, helper text, and empty states doing work — telling the user what to do and why — rather than restating the obvious?
- [ ] Error messages: do they say what went wrong **and** how to fix it, in plain language, near the field?
- [ ] Is anything written for the company's convenience (legalese, feature-speak) rather than the user's task?

## Pass D — Interaction & flow

- [ ] **Step count:** what is the minimum number of steps/screens to complete the primary task? Can any be merged or removed?
- [ ] **Field count:** is every form field necessary *now*? Each field is a tax; defer or drop optional ones. (Ask: would removing this lose a real decision the user needs to make?)
- [ ] Smart defaults pre-filled wherever a sensible default exists (Tesler — let the system absorb the choice)?
- [ ] Advanced/rare options hidden behind progressive disclosure, keeping the default path clean?
- [ ] **Error prevention over correction:** inline validation, constrained inputs, format-forgiving parsing (Postel) instead of post-submit rejection?
- [ ] Multi-step flows: is progress shown, and does it exploit the goal-gradient (e.g., step 1 already feels partly done)?
- [ ] Recognition aids: dropdowns, autocomplete, recently-used, and contextual suggestions instead of free recall?
- [ ] Are destructive/irreversible actions confirmed, undoable, and visually distinct from safe ones?
- [ ] Is confirmation used **sparingly**? Confirming routine/reversible actions trains "click yes" reflex (wolf-alarm / confirmation fatigue), so the one dangerous confirm gets dismissed too. Prefer **undo over confirmation** wherever the action can be reversed ("Deleted. Undo →" beats "Are you sure?").
- [ ] Does each action give immediate, legible feedback (the relevance confirmation that keeps engagement escalating)?
- [ ] Does the **end** of the flow land well (peak–end)? Is success obvious and the next step offered?
- [ ] Mobile: are touch targets large enough and within thumb reach (Fitts)? Does the layout reflow rather than just shrink?

## Pass E — Load classification

For each issue found across A–D, tag it:

- **Extraneous** → cut or fix. This is the bulk of the value.
- **Intrinsic** → manage (chunk, sequence, scaffold, explain) — don't pretend it away.
- **Germane** → keep; flag explicitly if a "simplification" would remove it, and warn the user.

## Sanity questions to close the audit

- If a brand-new user had 5 seconds on this surface, would they know what it's for and what to do next?
- Is the easy/obvious path also the correct path (because users satisfice — they take it regardless)?
- Did any recommendation just *move* complexity onto someone else (Tesler)? If so, is that someone the system, not the user?
- Is anything here recommended on taste alone? If yes, label it as taste, not research.

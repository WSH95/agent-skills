# Claim Calibration (standalone)

Match every claim's strength to the evidence that licenses it — no stronger,
no weaker. This is a grounding tool, not a style tool: it protects the paper
from the two symmetric failures reviewers punish, **overclaiming** (asserting
more than the evidence supports) and **underclaiming** (hedging away a result
the evidence actually earns).

In a standalone pass, the evidence anchor is what the manuscript itself
reports — its tables, figures, and stated results — plus the contribution
list the author confirmed during setup. A claim with no anchor there is not a
weak claim — it is an unverifiable one: mark it `unverifiable from the
manuscript`, ask the author, move it to future work, or drop it — never
soften it into a vague version of itself.

## The claim-strength ladder

Every assertion about the world sits on a rung. Name the rung the evidence
supports, then phrase the sentence at exactly that rung.

1. **Observation** — what was measured. Licensed by a reported measurement
   (a table row, a figure, a stated number).
   "Method A reached 0.82 success rate over 10 seeds (Table 2)."
2. **Interpretation** — what the observation means in context. Licensed by
   the observation plus a stated frame. "A clears the gap where the blind
   baseline stalls."
3. **Causal explanation** — *why* it happened. Licensed only by an isolating
   ablation or controlled comparison, not by a correlation. Without one, it
   is a hypothesis — say so.
4. **Generalization** — the claim holds beyond what was tested. Licensed
   only by the span actually covered (tasks, robots, terrains, seeds). Do
   not generalize past the evaluated set.
5. **Implication** — consequence for practice or the field. State the
   condition it depends on.
6. **Speculation** — plausible but unshown. Allowed only when labeled as
   such (future work, conjecture) and never in the abstract or
   contributions.

Rungs 1–2 are usually safe; 3–6 are where overreach happens. When in doubt,
drop one rung.

## Causal-verb precision

The verb encodes the causal claim. Pick the weakest verb consistent with the
evidence:

- **Direct/strong** (needs an isolating comparison): `causes`, `produces`,
  `X results in Y`, `drives`, `yields`.
- **Partial**: `contributes to`, `is a factor in`, `is one driver of`.
- **Association only** (no causal claim at all): `is associated with`,
  `is linked to`, `correlates with`, `coincides with`.

`a cause of` implies other factors too; `the cause of` claims sole cause —
only use `the` when alternatives are ruled out. `X results from Y` and
`X results in Y` reverse cause and effect; check the direction.

## Strength and tense (two different axes)

Grammatical tense policy comes from the author's stated preference (setup
questions) or the manuscript's dominant convention — typically present tense
for the method and standing claims, past for actions performed; keep it.
Calibration governs a different axis: how strongly a claim about the world
is scoped. "A improves sample efficiency" asserts a general property;
"A improved sample efficiency in our experiments" scopes the same finding to
what was shown. Do not state a scoped finding as a standing law. When the
two guidances meet, keep the tense policy and adjust the *scope* words
(`in our experiments`, `on these tasks`, `under these conditions`) instead.

## Hedging to the evidence level

Modals (`may`, `might`, `could`) and qualifiers (`in our experiments`,
`for N seeds`, `on flat terrain`) exist to scope a claim **down to what was
shown** — not to sound cautious. A hedge vaguer than the evidence is as
wrong as an overclaim stronger than it: "the policy may sometimes improve
tracking" buries a real, measured result. Calibrate to the rung; then stop.

## Statistical claim words (hard gates)

These carry a specific evidentiary burden in ML/robotics writing:

- **"significant" / "significantly"** — needs a test or non-overlapping CIs.
  Never as a synonym for "large."
- **"outperforms" / "beats"** — needs a CI-backed comparison under an
  identical protocol; otherwise `improves upon`, or state the metric delta
  plainly.
- **"robust"** — name the perturbation set it is robust *to*.
- **"state-of-the-art"** — name the comparison set and the date.
- **"consistent" / "stable"** — report the spread, not just the mean.

These mirror the standards statistical reviewers apply; a review panel will
flag them if editing does not.

## What calibration is NOT

- Not concision, not the style sweep, not blanket hedging. It changes claim
  *strength*, nothing else.
- It **tightens or scopes** overreach and **restores** earned strength to
  underclaims. It must never rewrite strong, well-supported prose into
  vaguer, weaker, or hedge-laden language — that trades a real claim for a
  timid one.
- **Divergence note (deliberate):** broad-STEMM writing guides advise
  "evaluative" framing — attaching value words to fix a number's meaning.
  Keep only the grounded half of that idea (a bare number needs an explicit
  "what should the reader conclude") and reject the marketing half
  ("striking", "excellent", "novel"): an evidence-calibrated style bans it
  because ML/robotics reviewers read it as hype. Calibration lowers unearned
  strength; it does not add rhetorical color.

## Procedure

For each claim sentence:
1. Find its anchor in the manuscript's reported results or the
   author-confirmed contributions.
2. Place it on the ladder; pick the verb and scope words at exactly that
   rung.
3. If nothing anchors it, it is `unverifiable from the manuscript` — ask
   the author, label it as speculation, move it to future work, or cut it.
   Do not downgrade it into a vague claim that reads as supported.
4. Every edit that could change meaning goes into the revision report's
   meaning-changing section as a before → after pair for the author's
   confirmation.

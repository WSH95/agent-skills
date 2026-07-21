---
name: paper-review-standalone
description: >-
  Run a mock peer review of a finished academic paper draft with no project
  setup — works directly on an uploaded PDF, LaTeX or Markdown files, or
  pasted text. Optionally interviews the author (venue, paper type,
  contributions, worries), then five reviewer lenses each write a
  structured review and an area-chair adjudication rules on every major
  weakness with cited evidence — one report with scores, verdicts, a ranked
  must-fix list, and an overall call. Use whenever an author shares a draft
  and wants critical assessment before submitting — "review this paper",
  "mock review", "what would reviewers say", "red-team it", "will this get
  into CoRL / T-RO" — even if they don't name this skill.
disable-model-invocation: true
---

# Standalone Mock Review

Simulate a program-committee review of a single manuscript: five reviewer
lenses, then an area-chair adjudication that rules on every major weakness
and prioritizes. Everything needed ships in this skill's `references/` —
no repository, project files, or other skills. (See "Relation to the
Paperforge kit" at the end for the workspace-grounded original.)

## Workspace check (first)

If this session is inside a Paperforge paper workspace — the project
carries the Paperforge constitution and the plugin's `paper-review-panel`
skill is available — invoke that skill and stop: it runs the same panel
with native reviewer isolation and an evidence base the area chair can rule
against. This standalone variant exists for manuscripts without a
workspace.

## Input and setup

- Accept the manuscript in whatever form this environment can read: an
  uploaded PDF, LaTeX or Markdown files, or pasted text. If a PDF cannot be
  read here, ask the author to paste the text — never fail. Note extraction
  limits (figures, table alignment, math fidelity) in the report header
  rather than guessing.
- **Optional mini-interview** — ask one question at a time; every question
  is skippable, and skipping all of them means a blind, venue-agnostic
  review (say so in the report header):
  1. Target venue? (Plus page limit or deadline if relevant.)
  2. Paper type — empirical evaluation, systems, methods-heavy, or theory —
     and what does this venue's audience value most (hardware demos,
     statistical rigor, theoretical framing)?
  3. The contributions as you would defend them to a hostile reviewer
     (2–4)?
  4. Which existing paper worries you most as an overlap threat, and what
     are the paper's real limitations in your own words?
  Answers calibrate the lenses (the overlap threat feeds the novelty lens;
  the confirmed contributions anchor the area chair). Author answers are
  context, never manuscript content — the paper is judged *as submitted*.
- **Panel composition**: all five lenses for journal or high-impact targets;
  the significance/impact lens is optional for page-limited conferences.
  Offer to skip or adapt lenses if the paper's field is far from
  robotics/ML — keep each lens's *kind* of scrutiny, adjust its domain
  examples.

## Run the panel

1. Read the manuscript **in full, first**, and form your own impression —
   strengths, likely objections — before generating any review. (This also
   satisfies the area chair's anti-anchoring rule.)
2. **Isolation is required whenever available**: if this environment can
   delegate a task to an isolated, fresh-context agent (for example a
   general-purpose subagent), run each lens as one delegated task. Give the
   delegated agent ONLY: the manuscript, that lens's section from
   `references/reviewer-lenses.md`, the shared rules and output format from
   the same file, and the venue/paper-type answers. Never share another
   lens's review or the author's other interview answers. Collect the
   completed reviews.
3. **Sequential fallback** (no delegation available — plain chat or a
   restricted environment): run the lenses one at a time in this context,
   producing one complete review per lens in the exact output format, and
   never revising an earlier review after writing a later one. The report
   header must then carry the label `non-independent (single context)`.
4. Every review follows the shared output format in
   `references/reviewer-lenses.md` exactly: Summary (≤150 words),
   Strengths (S#), Weaknesses — major (W#, each with a Sec./Fig. pointer),
   Weaknesses — minor (w#), Questions (Q#), Scores (1–5), Recommendation.

## Area-chair adjudication

Follow `references/area-chair-protocol.md`: rule on every major weakness
with an evidence-cited verdict, resolve disagreements between lenses,
escalate contested calls to the author, and produce the meta-review.

## Coverage self-check (before delivering)

Verify, and fix the meta-review if any check fails:

- every major W# from every review has exactly one row in the Adjudication
  table, and no row cites an id that does not exist in its review;
- every verdict is one of `confirmed | partly-confirmed | refuted |
  judgment-call | out-of-scope` (a trailing `(contested)` marker is
  allowed);
- every `confirmed` / `partly-confirmed` / `refuted` row has a non-empty
  Evidence cell;
- all meta-review sections from the protocol's template are present.

## Deliverable

One review report, as a document where this environment supports writing
files, otherwise inline: **header** (venue and paper type, or "blind
review"; the isolation label; input-fidelity caveats) → **the five
reviews** → **the meta-review**. If the author wants to act on it next,
suggest working through the "Top must-fix" list and rebutting `refuted`
points with the cited evidence.

## Relation to the Paperforge kit

Derived from the Paperforge plugin's `paper-review-panel` skill and its
reviewer and area-chair personas — install the full plugin from the public
marketplace (https://github.com/WSH95/agent-plugins/tree/main/paperforge)
to run the same panel inside a per-paper workspace with stronger
guarantees: filesystem-enforced reviewer isolation, native Codex reviewer
agents, a durable evidence base the area chair can rule against,
deterministic review-round checks, and the revision/rebuttal workflow that
consumes the verdicts.

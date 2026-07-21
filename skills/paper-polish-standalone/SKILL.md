---
name: paper-polish-standalone
description: >-
  Polish, tighten, proofread, shorten, or line-edit a finished academic
  paper draft with no project setup — works directly on an uploaded PDF,
  LaTeX or Markdown files, or pasted text. Runs structured editing passes
  (structure, clarity and flow, claim calibration, concision, mechanical
  sweep, style consistency, title check) and returns a revision report of
  numbered before/after comparisons with reasons. Use whenever an author
  shares a paper draft and wants the writing improved — "polish this",
  "make it read better", "proofread", "tighten", "we're over the page
  limit", "are my claims overstated" — even if they don't name this skill.
  Not for adding content or new claims.
disable-model-invocation: true
---

# Standalone Polish Pass

Improve prose quality without changing scientific content. Polishing never
adds claims, numbers, or citations; if a passage *needs* new content, tell
the author what is missing instead of inventing it.

This skill is self-contained: it works on any manuscript this environment
can read, with no repository or project files. (See "Relation to the
Paperforge kit" at the end for the workspace-grounded original it derives
from.)

## Workspace check (first)

If this session is inside a Paperforge paper workspace — the project
carries the Paperforge constitution and the plugin's `paper-polish` skill
is available — invoke that skill and stop: it runs the same method grounded
in the project's durable records (evidence, style sheet, deterministic
checker). This standalone variant exists for manuscripts without a
workspace.

## Input and setup

- Accept the manuscript in whatever form this environment can read: an
  uploaded PDF, LaTeX or Markdown files, or pasted text. If a PDF cannot be
  read here, ask the author to paste the text — never fail. Text extracted
  from a PDF loses source details (comments, macros, exact table layout);
  note affected checks in the report rather than guessing.
- Confirm scope before editing: whole paper or named sections, and which
  passes (below). Default: everything, passes 1–6. Ask the concision target
  (default −10–15%, more under page pressure).
- Ask up to three quick style preferences — tense policy, person
  (we/I/impersonal), and any terminology to protect — or, if the author
  prefers, infer the manuscript's dominant conventions and state in the
  report which conventions you inferred.
- Record a word count before and after.

## The passes (run in this order)

1. **Structure & argument.** Within each section: does paragraph order
   follow the paper's own argumentative logic and section headings? Does
   each paragraph open with its topic sentence and contain one idea? Fix by
   moving/splitting paragraphs; do not rewrite sentences yet.
2. **Clarity & flow.** Sentence level: active voice by default,
   subject–verb close together, one idea per sentence, resolve dangling
   "this/it", replace vague intensifiers with specifics. Then information
   flow: open each sentence with what the reader already knows and put the
   new information last, where the next sentence picks it up (given→new /
   end-focus); the join between two sentences is where readers lose the
   thread, so close it with an overlapping repeat, a `This`/`These`+noun
   pro-form, a semicolon, or a signal word. Guardrails, because these edits
   regress easily: do NOT add a connector to every sentence and do NOT
   mechanically insert "This shows / This suggests / Therefore"; always
   attach a noun to a leading `This`/`These`; near math, defined symbols,
   and method/dataset/system names, terminology consistency and technical
   precision win over flow — never reword a symbol or defined term for
   rhythm. Flow is reader navigation, not a licence to add words.
3. **Claim calibration.** Match every claim's strength to its evidence,
   using `references/claim-calibration.md` (the claim-strength ladder,
   causal-verb precision, and the statistical claim-word gates). The
   evidence anchor here is what the manuscript itself reports plus the
   contributions the author confirmed during setup; a claim with no anchor
   is flagged `unverifiable from the manuscript` — asked about, moved to
   future work, or cut, never silently weakened. This pass changes claim
   *strength* only — never rewrite strong, supported prose into vaguer or
   hedge-laden language, and add no evaluative/marketing words. Every
   calibration edit is a meaning-changing edit: it appears as a
   before → after pair in the report's approval section.
4. **Concision.** Apply the author's target. Cut throat-clearing ("It is
   worth noting that"), redundant hedges, and repeated information;
   compress via nominalization removal. Never cut assumptions, caveats, or
   reproducibility details to save space without asking.
5. **Mechanical sweep (in-context).** Check the text directly for: doubled
   words ("the the"), sentences starting with a bare digit, terminology
   variants used inconsistently (e.g. "sim-to-real" vs "sim2real" — pick
   the dominant form), and acronyms used before or without a "Full Name
   (ACRO)" expansion. Then list, without attempting them, the checks that
   only the author's LaTeX source or build can verify: citation keys
   resolving to the bibliography, cross-references and labels, leftover
   TODO markers, and any evidence-tagging conventions their project uses.
6. **Style consistency sweep.** Enforce the stated preferences (or the
   inferred conventions) item by item: terminology, banned phrases,
   tense/person rules, number formatting. When a rule is missing for a case
   you hit, ask once, then apply the ruling consistently.

When this is a pre-submission polish (not a mid-draft pass), also verify the
paper **title** against `references/title-check.md`: flag overpromising,
vague topic-only breadth, opaque acronyms, compound-noun pileups, ambiguous
prepositions, buried keywords, or mismatch with target-venue title norms.
Suggest fixes; the title is the author's call.

## Editing discipline

- Edit surgically; keep the author's voice — polish removes friction, it
  does not homogenize. If a sentence is unusual but clear and deliberate,
  leave it.
- Substantive rewordings (meaning could shift) always appear as
  before → after pairs for approval; mechanical fixes are batched and
  summarized.
- Anything ambiguous about *meaning* is a question for the author, not an
  editorial guess.

## Deliverable: the revision report

Produce the report as a document — a written file where this environment
supports writing files, otherwise inline in the reply. Structure:

1. **Header** — scope, passes run, word-count delta, style conventions
   applied (stated vs. inferred), and input-fidelity caveats (e.g. "PDF
   text extraction; table alignment approximate").
2. **Per pass, numbered edits** — `P<pass>.<n>` with: Location (section /
   paragraph), BEFORE (verbatim quote), AFTER (revised text), WHY (one
   line naming the rule applied).
3. **Meaning-changing edits** — all calibration and scope changes grouped
   for explicit author approval, each with its before → after pair.
4. **Verify-in-source list** — the deferred source-only checks from pass 5.
5. **Full revised text** — as an appendix, on request.

## Relation to the Paperforge kit

Derived from the Paperforge plugin's `paper-polish` skill — install the
full plugin from the public marketplace
(https://github.com/WSH95/agent-plugins/tree/main/paperforge) to run the
same method inside a per-paper workspace with stronger grounding: a durable
record of experimental results that claims are calibrated against, a
deterministic consistency checker, a persistent style sheet, isolated
multi-reviewer mock panels, and revision/rebuttal workflows.

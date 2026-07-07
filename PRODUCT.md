# Product context

> **Confidence note:** pre-implementation (scaffold only — no parser, no
> receipt schema, no renderer written). Drawn from the founding proposal
> and the 2026-07-07 problem-space research
> (`docs/research/2026-07-07-problem-space.md`), not from code. Treat as
> **medium confidence**; `docs/specs/` work may change it. Re-run
> `/extract-product-context` once the MVP exists.

## Why this product exists

AI-text detection is collapsing — false-accusation lawsuits are being won,
universities are disabling Turnitin's AI detection, and Stanford HAI found
61% of non-native-speaker essays falsely flagged — while institutions,
journals, and platforms shift to disclosure and process evidence (journal
AI-use disclosure rules, Amazon KDP's generated-vs-assisted checkbox, EU AI
Act Article 50 marking). Grammarly Authorship proved the category (3M+
reports) but is editor-locked, cloud, institution-facing — and demonstrably
launderable by its own Humanize feature.

Developers have the same need in a friendlier register: `Co-Authored-By:
Claude` / `Assisted-by:` trailers are a de facto disclosure convention, but
they are binary and commit-scoped — nobody accounts for *how much* of a PR
description, README, design doc, or post a human actually wrote. byline
derives that accounting from the place it already exists: session
transcripts record who typed what. Ground truth, no capture surveillance.

## Who uses it

### Primary persona

A developer who writes with AI daily — PR descriptions, design docs,
READMEs, blog posts drafted in Claude Code or claude.ai — and wants their
disclosure to be honest and proportional rather than a binary trailer.
They run byline over the session(s) behind a piece, get a receipt, and
attach it (a footer line, a trailer block, or a linked receipt file) by
choice. Their audience — maintainers, teammates, readers — extends
good-faith trust; the receipt upgrades that trust with specifics.

### Secondary persona (later, riskier)

A student or academic documenting writing process in the direction
institutions are moving (drafts + process evidence). Explicitly deferred:
byline serves the honest majority documenting process; it is never
positioned as exoneration evidence for the accused — gameability makes
adversarial claims untenable, and overclaiming is the category's fatal
mistake (Grammarly's laundering demo is the cautionary tale).

## Product principles

1. **Ground truth over instrumentation.** Parse transcripts that already
   record authorship (Claude Code JSONL first); never require writing
   inside a surveilled editor.
2. **Bounded claims, stated in the artifact.** Every receipt carries its
   own epistemics: what was measured, what window, what it cannot prove.
   The trust model is Signed-off-by / KDP-checkbox — good-faith
   self-disclosure with low honesty cost and nonzero forgery cost.
3. **Proportional and paragraph-level.** Written / AI-drafted-human-revised
   / accepted-verbatim, per paragraph — not a binary badge, not a single
   opaque percentage without the map behind it.
4. **Disclosure, never blocking.** No gate, no verdict about acceptability,
   no policy engine. byline states; humans and institutions decide.
5. **Local and keyless.** The user's transcripts stay on the user's
   machine; receipts are emitted by choice. No hosted verification service.
6. **Cross-tool plumbing, not a walled editor.** The receipt format and
   parsers are the product; more transcript sources over time — the one
   shape editor-locked incumbents structurally resist.

## Feature tracker

No issue tracker configured yet. Founding scope:

| Capability | What users can do | Status |
|---|---|---|
| Transcript parsing | Attribute text spans from Claude Code session JSONL: human-typed, AI-drafted + human-edited, accepted verbatim | Not started |
| Edit-distance attribution | Classify revision depth of AI-drafted text (revised vs verbatim) with stated thresholds | Not started |
| Receipt schema | Per-paragraph proportions + provenance metadata + epistemics block, as data | Not started |
| Renderers | Footer line, git trailer block, markdown receipt section, standalone receipt file | Not started |
| Doc mapping | Map a final document back to the sessions that produced it (fuzzy match across drafts) | Not started |
| Multi-source (later) | claude.ai export, other agent transcripts | Not started |

## Critical user journeys

1. **PR description:** dev finishes a feature; the PR body was drafted in
   session > `byline receipt` maps the body to the transcript > emits a
   trailer block ("Authorship: 55% written, 35% revised-from-draft, 10%
   verbatim — byline v0") > dev pastes it, by choice.
2. **Blog post:** post drafted across three sessions > receipt renders as a
   one-line footer with a link to the paragraph map > readers who care can
   look; readers who don't see one honest line.
3. **The dogfood test:** byline's own README and design docs carry
   receipts from the sessions that wrote them — including unflattering
   proportions. Honest receipts or no receipts.

## What we're NOT building

- An AI detector, or anything that scores text without a transcript.
- Adversarial/forensic proof — no claim survives a determined forger who
  retypes AI output; the product says so on every receipt.
- Keystroke/biometric capture, editor plugins that watch typing, or any
  surveillance surface (Grammarly's lane, and a 2026 paper shows timing
  forgery defeats it anyway).
- A gate, a policy engine, or an institutional dashboard of other people's
  receipts.
- Watermarking (model-vendor territory; says nothing about human share).

## Current known problems

None yet — no code. Founding risks from the research: (1) **incumbent
extension** — Grammarly moving Authorship beyond its editor, or Anthropic
shipping a first-party session-authorship summary, closes the window; the
defense is cross-tool plumbing and dev-native surfaces neither prioritizes;
(2) **attribution is genuinely hard at the edges** — text pasted between
sessions, heavy interleaved editing, multi-draft assembly; v0 scopes to
what the transcript supports and marks the rest "unattributed," honestly;
(3) **norm risk** — proportional disclosure only matters if audiences read
it; the `Assisted-by` debate (~500k views) says devs care, but adoption is
a bet, not a fact.

## Business model

None yet. Plausible shape: free CLI/skill (the receipt spreads with a
pointer back, same distribution logic as winnow's receipt format); paid
conveniences later only if adoption warrants. Decided by written amendment,
not drift.

# Design system

> Pre-implementation: founding intent for the surfaces. Re-run
> `/extract-design-system` once real output exists.

## Surfaces

- **CLI / Claude Code skill** (`byline`) — parse sessions, map a document,
  emit receipts.
- **The receipt** — the real product surface: footer line, git trailer
  block, markdown section, or standalone file. Read by strangers; every
  formatting decision optimizes for a skeptical first-time reader.

## Semantic palette

### States (attribution classes)

- **written** — human-typed in session; the strongest class.
- **revised** — AI-drafted, human-edited past the stated edit-distance
  threshold.
- **verbatim** — AI-drafted, accepted with no meaningful edit.
- **unattributed** — outside transcript coverage (pasted in, unknown
  origin). Never silently folded into another class.

### Per-surface rendering

Receipts render proportions in a fixed order (written / revised / verbatim
/ unattributed) with the same class names everywhere. The paragraph map
uses the same four words — no synonyms, no euphemisms ("verbatim" never
becomes "AI-assisted").

## Vocabulary

receipt, attribution class, paragraph map, epistemics block, coverage
(the share of the document the transcript can speak to). One name per
concept across CLI, schema, and rendered output.

## Formatting

- The one-line footer form: `Authorship: 62% written · 30% revised · 8%
  verbatim (byline v0, 94% coverage)`. Numbers always sum with
  unattributed included or coverage stated — never a flattering subset.
- Every rendered receipt includes or links the epistemics block: what was
  measured, from which sessions, what it cannot prove (retyping defeats
  it). Non-negotiable — the bounded claim is the brand.
- Trailer block form follows git conventions (RFC-822-style keys).

## Per-surface conventions

### CLI

- Non-interactive by default; `byline receipt <file>` does the whole flow
  when sessions are discoverable, and says exactly which sessions it read.
- Exit codes: 0 receipt emitted, 1 coverage below floor (receipt still
  emitted, flagged), 2 error.

### Report / export

- Standalone receipt file is plain markdown + a data block (schema-versioned)
  — readable without byline, parseable with it.

## Anti-patterns (do NOT do these)

- A percentage without coverage stated — the Grammarly-laundering lesson:
  the summary number must never be more confident than the map behind it.
- Green/red moralizing of classes — verbatim is a fact, not a shame color.
- Claiming or implying forgery resistance anywhere, including marketing.
- Hiding unattributed text by renormalizing the other three classes.

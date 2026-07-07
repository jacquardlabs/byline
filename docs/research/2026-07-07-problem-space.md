# Problem-space research — 2026-07-07

Condensed from the founding research pass (web research agent, 2025–2026
sources). Grounds PRODUCT.md; cite rather than re-derive.

## Problem validation

- **Detection is failing legally and institutionally:** a wave of 2025–26
  false-accusation lawsuits (an Adelphi student won expungement in NY State
  Supreme Court; Yale, Michigan, Palo Alto, Minnesota cases pending);
  Curtin University disabled Turnitin AI detection Jan 2026; Stanford HAI
  found 61% of non-native-speaker essays falsely flagged; GPTZero ~11%
  false positives on real student text vs its 1% claim.
- **The institutional response is process evidence** — drafts, version
  history, disclosure: journal AI-use disclosure rules (Science treats
  undisclosed AI text as misconduct), Amazon KDP's generated-vs-assisted
  checkbox, EU AI Act Article 50 marking (enforcement Aug 2026),
  universities moving to "grade the thinking."
- **The category is validated:** Grammarly Authorship — 3M+ reports, ~41k/
  day, Canvas LMS integration where instructors can require reports.
- **Dev-side vacuum:** `Co-Authored-By:`/`Assisted-by:` trailers are de
  facto convention (a ~500k-view debate; OpenTelemetry standardized
  `Assisted-by` in its contribution policy) but binary and commit-scoped —
  nobody does proportional, per-paragraph accounting for PR/doc prose.

## Gameability (the bound, stated once)

Retyping AI output defeats any process log; a 2026 paper (arXiv 2601.17280)
shows timing-forgery defeats keystroke biometrics — motor signals "cannot
establish content provenance." Therefore: a receipt is **good-faith
self-disclosure with low honesty cost and nonzero forgery cost** — the
Signed-off-by / KDP-checkbox trust model, which is adopted and useful.
Grammarly's failure mode (its own Humanize feature yields "75% typed by
human" in reassuring green — the laundering demo) shows *overclaiming* is
the category's fatal mistake. Bounded claims are the brand.

## Landscape

| Player | Covers | Gap |
|---|---|---|
| Grammarly Authorship | typed/pasted/AI events in its editors; reports + replay; LMS distribution | Editor-locked, cloud, surveillance-framed; launderable; no CLI/dev surface |
| Cursor AI Code Tracking / GitClear | AI-line attribution for code, manager-facing | Analytics, not an author's voluntary artifact; code only |
| git trailers convention | Binary AI disclosure | No proportions, no prose coverage — the vacuum byline fills |
| Indie typing-biometrics (Purely Human, OKhuman…) | Composition capture + sealing | Biometrics ≠ provenance (forgeable); own-editor lock-in; no distribution |
| SynthID-Text / C2PA | Vendor watermark / media provenance | Detects one vendor's output; text C2PA unimplemented — adjacent standard to emit into later |
| Authors Guild "Human Authored" | Honor-system warranty | No process evidence at all |

## What the research changed

1. **Market order inverted: dev first, academic later.** The accused need
   adversarial proof (ruled out); institutions already have Grammarly-in-
   Canvas; the buyer there is the institution. Devs extend good-faith
   trust, have the convention vacuum, and are reachable.
2. **The transcript scope is the structural advantage:** Claude Code
   sessions already record who typed what — byline parses ground truth it
   never had to capture, where every competitor must instrument an editor.
3. **Position as cross-tool, local-first plumbing** (receipt format +
   parsers) — the shape an editor-locked incumbent's business model
   resists.
4. Constitutional rules derived: never market forgery resistance; every
   receipt carries its epistemics; unattributed text is never hidden.

## Threats

- Grammarly extending Authorship beyond its editors; Anthropic shipping a
  first-party session-authorship summary. Defense: cross-tool plumbing +
  dev-native surfaces neither prioritizes.
- Norm risk: proportional disclosure matters only if audiences read it —
  adoption is a bet.

## Verdict recorded

PROCEED — dev-first scope, permanently bounded claims.

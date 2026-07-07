# byline

Authorship receipts for prose — proportional human/AI disclosure derived from session transcripts — from [Jacquard Labs](https://github.com/jacquardlabs).

AI detectors are failing publicly (false-accusation lawsuits, universities disabling Turnitin's AI detection), and the world is shifting from detection to *process evidence*. byline is the affirmative side of that shift: a local tool that reads the transcripts where writing actually happened — starting with Claude Code sessions, where the record of who typed what already exists — and emits an authorship receipt: "written by me: 62%; AI-drafted, human-revised: 30%; accepted verbatim: 8%," at paragraph granularity, attached to a PR description, blog post, or README as voluntary disclosure.

Dev-first by design: developer audiences already extend good-faith trust to `Assisted-by:`/`Co-Authored-By:` trailers — byline upgrades that binary convention to honest proportions, from ground truth it never had to capture.

## What byline must never become

Not a detector. Not forgery-proof — a receipt is signed self-disclosure whose honesty cost is low and whose forgery cost is nonzero (the Signed-off-by trust model), and it must never be marketed as more. Not a gate: disclosure, never blocking. Not adversarial evidence — byline is for the honest majority documenting process, never positioned as exoneration proof for the accused.

## Status

Pre-implementation — founding design. See `PRODUCT.md`, `docs/research/2026-07-07-problem-space.md` for the evidence base, and `docs/specs/` / `docs/plans/` as they land.

## License

TBD (decided before first release).

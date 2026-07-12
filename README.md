# byline

Authorship receipts for prose: proportional human/AI disclosure derived from session transcripts, from [Jacquard Labs](https://github.com/jacquardlabs).

AI detectors are failing publicly: false-accusation lawsuits, universities disabling Turnitin's AI detection, Stanford HAI finding 61% of non-native-speaker essays falsely flagged. The world is shifting from detection to *process evidence*. byline is the affirmative side of that shift — a local tool that reads the transcripts where writing actually happened, starting with Claude Code sessions, and emits an authorship receipt: "written by me: 62%; AI-drafted, human-revised: 30%; accepted verbatim: 8%," at paragraph granularity, attached to a PR description, blog post, or README as voluntary disclosure.

Dev-first by design: developer audiences already extend good-faith trust to `Assisted-by:` / `Co-Authored-By:` trailers. byline upgrades that binary convention to honest proportions, from ground truth it never had to capture.

## What byline must never become

- **Not a detector.** It reads transcripts; it never scores text without one.
- **Not forgery-proof.** A receipt is signed self-disclosure: low honesty cost, nonzero forgery cost (the Signed-off-by trust model). It is never marketed as more.
- **Not a gate.** Disclosure, never blocking.
- **Not adversarial evidence.** byline is for the honest majority documenting process, never positioned as exoneration proof for the accused.

## Status

Pre-implementation — founding design only. No parser, no receipt schema, no renderer, no CLI exists yet.

- Product context and rationale: [`PRODUCT.md`](PRODUCT.md)
- Design intent for the receipt surfaces: [`DESIGN.md`](DESIGN.md)
- Evidence base: [`docs/research/2026-07-07-problem-space.md`](docs/research/2026-07-07-problem-space.md)
- `docs/specs/` and `docs/plans/` are scaffolded and currently empty — specs and plans land here as they're written.

## Install

> TODO: no package, manifest, or entrypoint exists yet. This section will document the real install command once one exists.

## Usage

> TODO: nothing is runnable yet — no CLI, no demo. `DESIGN.md` describes the planned interface: `byline receipt <file>` would parse discoverable Claude Code sessions and emit a receipt (exit 0 = receipt emitted, 1 = coverage below floor, 2 = error). Treat this as design intent, not a working command.

## Contributing

Working process is spec → plan → build: design specs in `docs/specs/`, implementation plans in `docs/plans/`, both dated. Code conventions (Python 3.11+, `uv`, Ruff, Pydantic models, tests) and the full quality-gate flow are documented in [`CLAUDE.md`](CLAUDE.md).

## License

> TODO: no LICENSE file in this repo yet. License to be decided before first release — add the file and name the license here once chosen.

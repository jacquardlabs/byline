# byline — agent instructions

Authorship receipts for prose, derived from session transcripts.
Pre-implementation: founding design docs only. Read PRODUCT.md before
proposing scope. Two rules are constitutional and appear throughout the
docs: **never claim or imply forgery resistance**, and **never render a
proportion without coverage stated**. Treat both as invariants, not style.

## Working process

Spec → plan → build. Design specs in `docs/specs/`, implementation plans in
`docs/plans/`, both dated. Founding research lives in
`docs/research/2026-07-07-problem-space.md` — cite it rather than
re-deriving the landscape (detector collapse, Grammarly Authorship,
gameability bounds, dev-first rationale).

## Review workflow

### Context documents

- **PRODUCT.md** — product context, personas, principles, NOT-building list. Read before any product decision.
- **DESIGN.md** — receipt formats, the four attribution classes, epistemics-block rules. Read before changing anything users see. (CLAUDE.md owns *how the code is written*; DESIGN.md owns *the user-facing surface*.)

### Code conventions

- **Python** — 3.11+, `uv` for all tooling. Type hints required. Pydantic models for the receipt schema and all parser output — never raw dicts. Comprehensions and stdlib (functools, itertools, collections) over explicit loops.
- **Linter** — Ruff with C4,SIM,PERF,B,RUF,PIE; run `ruff check` before pushing.
- **Tests** — new features require tests; bug fixes require regression tests. Attribution classification gets golden transcript fixtures from day one (known session → known receipt); edit-distance thresholds are tested at their boundaries.
- **Transcript parsing** — fix data at the boundary: normalize session JSONL into typed events at ingestion; downstream code never touches raw JSONL shapes.

### Quality gates

| Gate | When | Command |
|------|------|---------|
| Should we build? | Before any engineering | `/gate-should-we-build [idea]` |
| Design review | After design doc, before implementation | `/gate-design-review` |
| Audit | After implementation, before acceptance | `/gate-audit` |
| Acceptance | After audit passes, before merge | `/gate-acceptance` |

### Periodic reviews

| Review | Cadence | Command |
|--------|---------|---------|
| Codebase health | Weekly or pre-milestone | `/deep-review codebase` |
| Interface health | Monthly or post-receipt-format-changes | `/deep-review interface` |
| Architecture | Quarterly or pre-major-feature | `/deep-review architecture` |
| Product health | Monthly | `/deep-review product` |
| README drift | After a release or feature batch | `/deep-review readme` |
| All reviews + summary | As needed | `/deep-review` |

### After each review

1. Fix any **Critical** findings before the next feature
2. File **Important** findings as tasks to address this cycle
3. Log **Track** findings (lowest tier — revisit next cycle); they compound if ignored
4. Update context docs if the review surfaced changes:
   - `/deep-review product` updates PRODUCT.md
   - `/deep-review interface` updates DESIGN.md
   - `/deep-review architecture` updates CLAUDE.md
   - `/deep-review readme` proposes a README.md diff

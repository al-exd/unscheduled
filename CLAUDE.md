# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

cve-lens is a portfolio project for exploring, filtering and computing statistics on known CVEs imported from a single public source: the NVD (NIST National Vulnerability Database). No other source is in scope. It demonstrates software system engineering. The repository is at **Phase 0 (foundations)**: there is no source code, build, or test setup yet, and no technology has been chosen. When the skeleton exists, add the build, test, and single-test commands to this file.

## Key documents

- `README.md`: project pitch, written in **French**.
- `docs/PLAN.md`: phased MVP plan (Phase 0 to 8) with "Done when" criteria. Read it before starting work to know which phase is active.
- `docs/GLOSSARY.md`: domain glossary.
- `docs/adr/`: architecture decision records (none yet).
- Everything under `docs/` is written in **English**. The README is in French.

## Intended architecture

The plan uses domain-driven design with these areas of responsibility:

1. **Ingestion**: incremental, idempotent sync from the NVD. Raw records are kept alongside cleaned domain objects.
2. **Querying**: search and filters over imported CVEs, for interactive exploration.
3. **Statistics**: documented, reproducible measures over any filtered set of CVEs (volumes, severity, weaknesses, products, analysis coverage and delay, data completeness).

End-to-end flow: import → query → compute statistics → display.

AI suggestions for incomplete CVEs are an optional final phase (Phase 8), only after the core is shipped.

## Domain invariants (from the plan, Phase 1)

- Every piece of data records who supplied it (the NVD itself or a CNA).
- Data from one provider never silently overwrites data from another.
- Rejected CVEs stay visible as rejected; they are never deleted.
- Key domain events: CVE imported, CVE updated.

## Working rules

- Documentation describes the system, not the tools. Don't name specific technologies (languages, frameworks, databases, hosting) in the README, plan, or glossary; record technology choices only in ADRs.
- Work test-first (TDD). Build small value objects (CVE ID, severity, version range, weakness type, NVD status) before the main CVE aggregate.
- Finish each phase before starting the next. Ship something working at the end of each phase. Cut scope rather than extend the timeline.
- Write the ADR when the decision is made, not afterwards.
- `data/` holds small sample datasets only. Never commit bulk source dumps or database files.
- Keep secrets (NVD API key) out of code. `.env` is gitignored.
- The owner makes the design, domain-model, technology, and security decisions. Propose options; don't settle them unilaterally.

## Known inconsistencies

- The `.gitignore` is a .NET template left from the initial commit; it does not reflect a technology decision.

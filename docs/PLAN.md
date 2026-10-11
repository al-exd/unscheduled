# Plan

- Build a Minimal Viable Product (MVP) for the project using DDD and TDD.

## Phase 0 - Foundations

1. Write a one-page problem statement: the gap, the goal, the MVP scope.
2. Write a glossary of domain terms (CVE, source, consolidated record, severity, filter, statistic).
3. Map the end-to-end flow: import → consolidate → query → compute statistics → display.
4. Identify the areas of responsibility: ingestion, consolidation, querying, statistics.
5. Record the first architecture decisions.
6. Set up the repository, project skeleton and automated build/test pipeline.

**Done when:** the empty project builds and tests run automatically on every change.

## Phase 1 - Domain model

1. List the core concepts and their rules (what must always be true).
2. Build the small descriptive values first (CVE ID, severity, version range, weakness type, source), test-first.
3. Build the main CVE object and its rules, test-first:
   - Every piece of data records which source it came from.
   - Data from one source never silently overwrites data from another.
   - A rejected CVE stays visible as rejected; it is never deleted.
4. Define the key events (CVE imported, CVE updated, sources disagree).

**Done when:** all domain rules are enforced by code and proven by tests.

## Phase 2 - Ingestion from a first source

1. Explore the first public CVE source and its data format manually.
2. Fetch a single page of CVEs and convert it into domain objects.
3. Store CVEs, keeping both the raw records and the cleaned data.
4. Make the import incremental (only new or changed CVEs).
5. Make it safe to re-run (no duplicates) and resilient (rate limits, failures, retries).
6. Schedule the sync to run automatically.

**Done when:** the last 90 days of CVEs from one source are imported and stay up to date on their own.

## Phase 3 - Additional sources and consolidation

1. Add a second and third source behind the same import contract.
2. Merge records about the same CVE into one consolidated view.
3. Keep the provenance of every field and record where sources disagree.
4. Track per-source coverage: which CVEs each source knows, and how complete its data is.

**Done when:** a CVE shows data from every source that knows it, with the origin of each field.

## Phase 4 - Querying and filtering

1. Define the filters (publication date, severity, product, vendor, weakness type, source, status, known exploitation).
2. Search by CVE ID, keyword, vendor and product.
3. Sort and paginate results.
4. Expose the queries through a public interface usable by other tools.

**Done when:** any combination of filters returns correct results, proven by tests.

## Phase 5 - Statistics

1. Choose the first questions to answer (volume over time, severity distribution, top weakness types, top vendors, share of known exploited CVEs).
2. Measure source coverage and analysis delay (time between publication and analysis, per source).
3. Measure disagreement between sources (severity, weakness type, affected products).
4. Compute statistics on any filtered subset of CVEs.
5. Keep statistics up to date as new data arrives.

**Done when:** each statistic is reproducible and documented with its exact definition.

## Phase 6 - User interface

1. CVE list with search and filters.
2. CVE detail page: data from each source side by side, with provenance and disagreements.
3. Statistics dashboard with charts.

**Done when:** a visitor understands the project and its results within a minute.

## Phase 7 - Security and delivery

1. Keep all secrets out of the code.
2. Add automated security checks on the code and its dependencies.
3. Package the application and deploy it publicly.
4. Add monitoring: sync health per source, data volume, errors.
5. Write a threat model.

**Done when:** the application runs live, is monitored, and the pipeline blocks insecure changes.

## Phase 8 - Presentation

1. Write a README a recruiter understands in 30 seconds (problem, solution, results, live link).
2. Add screenshots and a short demo video.
3. Finalize the architecture decision records.
4. Write a short article about what the statistics revealed.
5. Prepare answers to the key interview questions about the design.

**Done when:** the project can be shared on a CV, LinkedIn and in interviews.

## Phase 9 (optional) - AI suggestions

Only after Phase 8 is done.

1. Let an AI model propose missing data (affected products, version ranges, weakness type) for incomplete CVEs.
2. Check its facts in code and validate every response; descriptions and references are untrusted input.
3. Label every result as a suggestion, never as official data, with its model, prompt version, confidence and sources.
4. Measure accuracy against CVEs that have official data, field by field, without giving the model the answer.

**Done when:** incomplete CVEs show labeled suggestions and their measured accuracy is published.

## Guiding rules

- Finish each phase before starting the next.
- Ship something working at the end of every phase.
- Write the decision record when you make the decision, not afterwards.
- Cut scope before extending the timeline.
- Describe the system in documentation; record technology choices only in decision records.

# Implementation Plan

## Development Rule

Build this project sequentially.

Never implement all phases at once.

After completing a phase:

- test it
- document it
- show changes
- report limitations
- stop for approval

---

# Phase 0 — Discovery & Research

## Goal

Determine what the marketplace should actually detect before writing the production implementation.

## Tasks

1. Read the Adobe Round 3 brief completely.
2. Extract all hard requirements.
3. Extract evaluation criteria.
4. Analyze Round 2 failure modes.
5. Research real websites and observable patterns.
6. Identify repeatable root causes.
7. Identify potential false positives.
8. Identify evidence required for each finding.
9. Determine which checks are deterministic.
10. Determine where semantic reasoning is useful.
11. Propose skill boundaries.

## Deliverables

    docs/requirements.md
    docs/research-notes.md
    docs/audit-taxonomy.md

## Required taxonomy table

For every candidate check:

| Field | Description |
|---|---|
| Check | What is being checked |
| Problem | What failure it detects |
| Evidence | What proves the problem |
| Impact | Why it matters |
| Severity | Severity logic |
| Confidence | Confidence logic |
| Detection | How it is detected |
| False Positives | Potential mistakes |
| Fix | Recommended remediation |

## Stop Condition

Do not begin architecture implementation until the user approves Phase 0.

---

# Phase 1 — Architecture

## Goal

Design the complete technical architecture.

Determine:

- final skills
- orchestrator
- crawler
- evidence model
- finding model
- recommendation model
- configuration
- shared utilities
- testing architecture

Create:

    docs/architecture.md

## Important

Challenge the proposed architecture.

Do not create skills just for quantity.

---

# Phase 2 — Marketplace Skeleton

Create:

- marketplace.json
- skill directories
- SKILL.md files
- references/
- scripts/
- README.md

Validate the Agent Skills structure.

Exactly one entrypoint.

---

# Phase 3 — Crawl & Evidence Foundation

Implement:

- URL validation
- robots.txt
- bounded crawler
- sitemap discovery
- URL normalization
- redirects
- HTTP metadata
- content-type handling
- timeouts
- crawl logs
- evidence representation

Add unit tests.

---

# Phase 4 — Crawl / Render Audit

Implement:

- raw HTML extraction
- rendered DOM extraction
- browser rendering where needed
- raw-vs-rendered comparison
- important content detection
- meaningful JS-only content detection

Do not report irrelevant DOM differences.

Add fixtures.

---

# Phase 5 — Structured Data & Fact Extraction

Implement:

- JSON-LD extraction
- schema analysis
- schema validation
- relevant schema selection
- visible content comparison
- important fact extraction
- fact consistency checks

Support context-sensitive page types.

---

# Phase 6 — Entity, Freshness & Corroboration

Implement:

- entity clarity
- brand/product relationships
- organization identity
- freshness signals
- cross-source comparison where feasible
- conflict detection
- confidence calculation

Gracefully handle external failures.

Never fabricate sources.

---

# Phase 7 — Engagement Audit

Implement:

- page purpose
- heading hierarchy
- important-answer discoverability
- above-the-fold information
- navigation
- internal links
- related content
- next-step guidance
- contextual continuity

Avoid unsupported assumptions about traffic source.

---

# Phase 8 — Orchestrator

Implement:

- audit planning
- skill invocation
- shared evidence
- finding normalization
- deduplication
- severity
- confidence
- priority
- recommendation composition
- final report generation

The orchestrator should compose skills rather than duplicate their logic.

---

# Phase 9 — Evaluation Harness

Create controlled test websites/fixtures representing:

1. Excellent static website
2. JS-heavy website
3. Missing structured data
4. Invalid structured data
5. Product site
6. Service site
7. Stale information
8. Conflicting information
9. Image-only important facts
10. Weak engagement
11. Strong engagement
12. Mixed-quality site

Measure:

- precision
- recall
- false positives
- missed findings
- evidence completeness
- severity quality
- recommendation quality
- runtime

---

# Phase 10 — CLI & Reports

Create CLI:

    python -m audit https://example.com

Potential options:

    --max-pages
    --max-depth
    --timeout
    --output
    --format json
    --format markdown
    --verbose

Output:

- JSON
- Markdown
- optional HTML

---

# Phase 11 — UI

Only begin after the audit engine is stable.

Build an investigation-oriented interface.

The UI must NOT look like a generic AI SaaS dashboard.

Refer to:

    UI_PRINCIPLES.md

---

# Phase 12 — Hardening

Test:

- invalid URLs
- redirects
- robots restrictions
- timeouts
- broken pages
- malformed HTML
- invalid JSON-LD
- missing metadata
- huge sites
- JS-heavy pages
- unavailable external sources
- duplicate pages
- rendering failures

Ensure graceful degradation.

---

# Phase 13 — Final Submission

Verify:

- marketplace.json
- exactly one entrypoint
- valid SKILL.md files
- README.md
- no secrets
- no pretrained weights
- ZIP <= 50 MB
- runtime < 5 minutes
- read-only behavior
- reproducible installation

Create:

    docs/final-validation.md

Also perform a final rubric review against:

- detection accuracy
- suggested-action quality
- output design
- engineering hygiene
- marketplace composition
- generalization
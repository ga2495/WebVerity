# CLAUDE.md

## Project

This is an Adobe University Hackathon 2026 — Round 3 submission.

Project goal:

Build a reusable Agent Skill Marketplace that can receive an arbitrary website URL, audit the website for:

1. AI discoverability problems
2. On-site engagement problems

and produce an evidence-backed, severity-ranked audit report with specific, prioritized recommendations.

---

## Authoritative Sources

Before making architectural or implementation decisions, read:

1. `round-3-brief.pdf`
2. `PRD.md`
3. `IMPLEMENTATION_PLAN.md`
4. `UI_PRINCIPLES.md` when working on the UI

The Adobe Round 3 PDF is the ultimate authority if there is any conflict.

Do not silently override competition requirements.

---

## Development Method

Work strictly phase by phase.

Do NOT build the entire project in one pass.

At the beginning of each phase:

1. State the objective.
2. State the files/components that will be created or changed.
3. Explain important design decisions.
4. Implement only that phase.

At the end of each phase:

1. Run validation/tests.
2. Report what works.
3. Report what does not work.
4. Report known limitations.
5. Show the resulting architecture/file structure.
6. STOP.

Do not start the next major phase until the user explicitly approves it.

---

## Core Principles

### 1. Evidence before conclusions

Every finding must be supported by observable evidence.

Never fabricate:

- URLs
- crawl results
- source counts
- timestamps
- structured data
- page content
- external corroboration
- measurements
- test results

If something cannot be verified, say so.

---

### 2. Root causes, not generic best practices

Do not turn the project into a generic SEO checker.

Bad:

"No SSR."

Good:

"Important product information is absent from the initial HTML and only becomes available after client-side rendering."

Bad:

"No JSON-LD."

Good:

"The product page exposes price and availability, but these important commercial attributes are not represented in machine-readable structured data."

Only report an issue when there is a meaningful reason it can affect AI discoverability, trust, understanding, or engagement.

---

### 3. Minimize false positives

Before reporting a defect, ask:

- What evidence proves it?
- Is the evidence sufficient?
- Does it actually create a meaningful problem?
- Is this context-dependent?
- Could this be an intentional implementation?
- Are we confusing a recommendation with a defect?

When evidence is insufficient, downgrade confidence or report an observation rather than a defect.

---

### 4. Generalization

The evaluator will use unseen websites.

Never hardcode:

- domains
- brand names
- products
- expected page structures
- known demo websites
- known content
- specific HTML patterns that only work for one site

Design for patterns.

---

### 5. Genuine skill decomposition

Do not create skills merely to increase the number of skills.

Every skill must represent a genuine separation of concern.

If two skills overlap heavily, merge them.

If one skill becomes too broad, consider splitting it.

A smaller number of strong skills is preferable to padded decomposition.

---

### 6. Deterministic first

Use deterministic code wherever possible.

Prefer code for:

- HTTP status
- redirects
- robots.txt
- sitemap discovery
- HTML extraction
- metadata extraction
- JSON-LD parsing
- structured data validation
- URL normalization
- raw-vs-rendered comparison
- counts
- timestamps
- page statistics

Use LLM reasoning only where semantic interpretation is genuinely necessary.

---

### 7. Read-only operation

The system must never modify a live website.

Never:

- submit destructive forms
- authenticate into admin areas
- modify content
- deploy changes
- edit files on the target website
- perform destructive actions

Respect `robots.txt`.

---

### 8. Performance

Typical audits should target:

< 5 minutes

Use:

- bounded crawling
- timeouts
- concurrency
- caching
- selective browser rendering
- limited external research
- early stopping

Do not perform uncontrolled crawling.

---

### 9. No pretrained weights

Do not include pretrained model weights in the final submission.

Keep the ZIP:

<= 50 MB

---

## Priority Order

When making tradeoffs, prioritize:

1. Detection accuracy
2. Evidence quality
3. Generalization
4. Recommendation correctness
5. False-positive control
6. Skill architecture
7. Runtime
8. CLI/reporting
9. UI polish

Do not sacrifice audit correctness for visual polish.

---

## Current Phase

The project begins at:

Phase 0 — Discovery and Research

Do not move beyond Phase 0 until explicitly approved.
# Adobe University Hackathon 2026
# Round 3 — Agent Skill Marketplace
# Product Requirements Document

## 1. Product Overview

We need to build a reusable Agent Skill Marketplace that allows a general AI agent to audit an arbitrary website.

Input:

    Website URL / domain

Output:

    Structured audit report containing:

    - problems found
    - evidence
    - severity
    - root cause
    - suggested action
    - priority

The system must cover two dimensions:

1. AI discoverability
2. On-site engagement

The system must generalize to websites it has never seen before.

---

# 2. Problem Being Solved

The Round 3 challenge builds on the reasoning from Round 2.

Round 2 focused on understanding why a brand can become:

- invisible
- stale
- misrepresented

inside AI applications.

Round 3 asks us to encode that reasoning into reusable Agent Skills so that a general AI agent can automatically audit arbitrary websites.

The system should identify the underlying mechanisms that make a website difficult for machines to discover, read, understand, trust, or accurately represent.

It should also identify issues that prevent visitors from continuing to engage once they reach the website.

---

# 3. Core User Story

A user provides:

    Audit https://example.com

The marketplace should:

1. Validate the URL.
2. Crawl the website safely.
3. Identify representative pages.
4. Inspect machine-readable and rendered content.
5. Analyze AI discoverability.
6. Analyze facts and structured information.
7. Analyze freshness and consistency where feasible.
8. Analyze entity clarity.
9. Analyze on-site engagement.
10. Collect evidence.
11. Determine severity/confidence.
12. Generate prioritized recommendations.
13. Compose everything into one final audit report.

---

# 4. AI Discoverability

The system must investigate why a brand may fail to be:

- discovered
- retrieved
- understood
- trusted
- cited
- represented accurately

Potential areas include:

## 4.1 Crawlability

Investigate:

- robots.txt
- HTTP accessibility
- redirects
- canonical URLs
- sitemap availability
- crawl boundaries
- inaccessible important pages

---

## 4.2 Machine Readability

Investigate whether important information is available to automated readers.

Potential checks:

- raw HTML
- rendered DOM
- client-side rendering
- JS-dependent content
- important content only appearing after rendering
- content hidden in non-text formats

Do not report every rendering difference.

Determine whether the missing content is actually meaningful.

---

## 4.3 Structured Data

Inspect relevant structured information including:

- JSON-LD
- schema.org
- Product
- Offer
- Organization
- Brand
- WebSite
- WebPage
- BreadcrumbList
- Article where appropriate

Check:

- syntax
- validity
- relevance
- important properties
- consistency with visible content
- relationships between entities

Do not require irrelevant schema types.

---

## 4.4 Important Facts

Identify important facts such as:

- organization name
- brand
- product/service names
- prices
- currency
- availability
- categories
- locations
- specifications
- dates
- important claims

Determine whether important facts are:

- clearly stated
- machine-readable
- extractable
- internally consistent

---

## 4.5 Entity Clarity

Investigate whether the website clearly communicates:

- what the organization is
- what the brand represents
- what products/services belong to it
- relationships between entities
- identity information
- ambiguous naming

Use observable evidence.

Do not speculate about hidden knowledge graphs.

---

## 4.6 Freshness and Corroboration

Where practical, identify important facts and compare them against relevant external information.

Potential signals:

- stale information
- conflicting information
- outdated product descriptions
- inconsistent brand descriptions
- inconsistent locations
- outdated product availability
- conflicting attributes

Consider:

- recency
- authority
- relevance
- directness
- consistency

Do not assume that a fact is true simply because many websites repeat it.

Never fabricate external corroboration.

---

# 5. On-Site Engagement

The system must investigate why visitors who arrive on a website may fail to engage.

Potential areas:

## 5.1 Orientation

Can the visitor quickly understand:

- where they are
- what the page is about
- what the product/service is
- why the page is relevant

---

## 5.2 Intent Continuity

Determine whether the landing experience supports likely visitor intent.

Look for:

- relevant answers
- important facts
- context continuity
- relevant navigation
- supporting information

Do not assume the exact query that brought a user to the page is available.

Use observable page evidence.

---

## 5.3 Information Hierarchy

Investigate:

- heading structure
- placement of important information
- above-the-fold clarity
- content hierarchy
- discoverability of key facts

---

## 5.4 Next Steps

Determine whether the page provides clear paths to:

- purchase
- contact
- explore
- compare
- learn more
- find related products/services
- access supporting information

The relevant action depends on page type.

---

# 6. Round 2 Knowledge

The Round 2 work provides starting hypotheses.

## Visibility

Important product information may be rendered only through JavaScript.

Potential Round 3 translation:

    Detect meaningful differences between raw HTML and rendered content.

---

## Structured Information

Important facts may lack machine-readable representation.

Potential translation:

    Detect important facts that are difficult to extract reliably.

---

## Staleness

Official information may conflict with outdated external information.

Potential translation:

    Detect important factual inconsistencies and freshness issues.

---

## Engagement

Visitors may arrive with specific intent but encounter a generic experience.

Potential translation:

    Detect weak orientation, poor information hierarchy,
    buried answers, and weak next-step guidance.

---

## Hallucination Risk

Do not attempt to directly prove that an AI will hallucinate.

Instead identify conditions that increase the risk of inaccurate machine interpretation.

Example:

    Authoritative sizing information is only available
    inside an image and is not present as crawlable text.

---

# 7. Audit Philosophy

Every finding should follow:

    Observation
        ↓
    Evidence
        ↓
    Root Cause
        ↓
    Impact
        ↓
    Severity
        ↓
    Recommended Action
        ↓
    Priority

A recommendation is not automatically a finding.

A best practice is not automatically a defect.

---

# 8. Findings

Each finding must minimally contain:

- id
- title
- severity
- evidence
- suggested_action

Recommended additional fields:

- category
- confidence
- affected_urls
- root_cause
- impact
- detection_method
- priority
- supporting_signals

---

# 9. Severity

Use:

### Critical

Severe problem that substantially prevents important content from being discovered/read/understood or creates a major correctness risk.

### High

Strong impact on discoverability, trust, or engagement.

### Medium

Meaningful issue but not fundamentally blocking.

### Low

Minor issue or optimization opportunity.

### Info

Useful observation or proactive recommendation without a confirmed defect.

Severity must be evidence-based.

---

# 10. Confidence

Use confidence separately from severity.

Suggested:

- High
- Medium
- Low

A finding with strong impact but weak evidence should not automatically receive high confidence.

---

# 11. Recommendation Requirements

Recommendations must answer:

1. What should change?
2. How should it change?
3. Why does it matter?
4. What problem does it resolve?

Bad:

    Improve SEO.

Good:

    Expose the current product price as crawlable HTML and
    represent the same value through Product/Offer structured
    data so machine readers can reliably extract the commercial
    attribute.

---

# 12. Proactive Recommendations

The system may recommend improvements even when no explicit defect exists.

Examples:

- stronger fact pages
- better machine-readable product information
- clearer entity relationships
- better contextual navigation
- clearer above-the-fold orientation

These recommendations must still be relevant and non-obvious.

---

# 13. Generalization

The system must support multiple website types.

Potential categories:

- e-commerce
- SaaS
- services
- local businesses
- publishers
- education
- corporate
- marketplaces
- portfolios

Do not assume every site is e-commerce.

Use adaptive page classification where useful.

---

# 14. Safety

The marketplace is recommend-only.

It must never:

- modify a target website
- access authenticated areas
- perform destructive actions
- abuse servers
- bypass access controls
- submit forms unnecessarily

Respect robots.txt.

---

# 15. Runtime

Typical audit:

    < 5 minutes

The crawler must be bounded.

Potential controls:

- max pages
- max depth
- request timeout
- overall timeout
- concurrency limit
- render limit
- retry limit

---

# 16. Submission

Final marketplace ZIP:

    <= 50 MB

No pretrained model weights.

Required root-level artifacts include:

- marketplace.json
- skill folders
- README.md

---

# 17. Success Criteria

The system should:

1. Accept arbitrary website URLs.
2. Audit both discoverability and engagement.
3. Produce evidence-backed findings.
4. Avoid false positives.
5. Generate specific recommendations.
6. Prioritize findings.
7. Generalize to unseen sites.
8. Use genuine skill decomposition.
9. Have exactly one entrypoint.
10. Produce the required report structure.
11. Run within the runtime constraint.
12. Remain read-only.
13. Be easy to run and understand.
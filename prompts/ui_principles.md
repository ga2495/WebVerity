# UI Principles

## Product Identity

The UI should feel like a:

    Website Forensics / AI Readiness Workbench

It should NOT feel like:

    Generic AI SaaS Dashboard

The product should communicate:

- investigation
- evidence
- technical analysis
- credibility
- precision
- transparency

---

# 1. Avoid Generic AI Design

Do NOT use:

- huge gradient hero sections
- purple/blue AI glow
- excessive glassmorphism
- floating chatbot widgets
- meaningless KPI cards
- generic "AI-powered" slogans
- stock illustrations
- excessive rounded containers
- excessive shadows
- random animated particles
- generic three-column SaaS layouts
- giant centered headings with a single CTA
- decorative AI brain graphics

Avoid designs that could belong to any random AI startup.

---

# 2. Design Inspiration

The interface should feel closer to:

- browser developer tools
- observability platforms
- security investigation tools
- forensic analysis software
- technical IDEs
- data inspection tools
- professional research software

The goal is:

    dense but understandable

not:

    decorative but empty

---

# 3. Primary Workflow

The core UI workflow:

    Enter URL
       ↓
    Start Audit
       ↓
    Crawl Progress
       ↓
    Audit Results
       ↓
    Investigate Finding
       ↓
    Inspect Evidence
       ↓
    Understand Root Cause
       ↓
    Read Recommended Fix

---

# 4. Suggested Main Layout

Possible structure:

    ┌────────────────────────────────────────────────────────┐
    │ AI READINESS LAB                    New Audit          │
    ├────────────────────────────────────────────────────────┤
    │                                                        │
    │ Audit target                                           │
    │ https://example.com                     [Run Audit]    │
    │                                                        │
    ├────────────────┬───────────────────────────────────────┤
    │ SITE            │ FINDINGS                             │
    │                │                                       │
    │ /              │ F-001   HIGH                         │
    │ /products      │ JS-only product information          │
    │ /about         │                                       │
    │ /contact       │ Evidence                              │
    │                │ ─────────────────────                 │
    │                │ Initial HTML:                         │
    │                │ price not found                       │
    │                │                                       │
    │                │ Rendered DOM:                         │
    │                │ ₹5,999                                │
    │                │                                       │
    │                │ Root Cause                            │
    │                │ ...                                   │
    │                │                                       │
    │                │ Recommended Fix                       │
    │                │ ...                                   │
    └────────────────┴───────────────────────────────────────┘

This is only a conceptual direction.

Improve it if a better information architecture emerges.

---

# 5. Evidence Should Be First-Class

Do not hide evidence behind vague summaries.

A user should be able to understand:

    Why did the system make this finding?

Possible evidence views:

- URL
- extracted text
- raw HTML
- rendered content
- JSON-LD
- source comparison
- page counts
- timestamps
- selectors
- crawl metadata

---

# 6. Finding Presentation

Example:

    HIGH
    F-004

    Product price unavailable in initial HTML

    IMPACT
    Important commercial information may be harder
    for machine readers to extract.

    EVIDENCE
    /products/example

    Initial HTML
    price not detected

    Rendered DOM
    ₹5,999

    ROOT CAUSE
    Price is injected after client-side rendering.

    RECOMMENDED FIX
    Expose price in crawlable HTML and corresponding
    Product/Offer structured data.

    PRIORITY
    HIGH

The interface should make the evidence → conclusion connection obvious.

---

# 7. Avoid Dashboard Clutter

Do not create:

    12 cards
    8 charts
    4 gauges
    3 progress bars

just because dashboards commonly contain them.

Every visual element must help answer:

    What is wrong?
    Why is it wrong?
    How do we know?
    What should I do?

---

# 8. Useful Visual Concepts

Potential components:

### Signal Map

A two-dimensional view:

    AI Discoverability
              ↑
              │
              │
              │
              └──────────────────→ Engagement

Findings can be positioned by impact.

---

### Evidence Drawer

Click a finding and inspect the evidence without losing context.

---

### Crawl Map

Show:

- pages discovered
- pages audited
- page types
- failed pages

---

### Raw vs Rendered Inspector

Show meaningful differences between:

    initial HTML

and:

    rendered page

---

### Recommendation Queue

A prioritized list:

    HIGH IMPACT
    ─────────────────
    Fix product facts

    HIGH
    ─────────────────
    Fix structured data

    MEDIUM
    ─────────────────
    Improve entity clarity

---

# 9. Visual Language

Use a restrained professional visual system.

Prefer:

- strong typography
- clear hierarchy
- compact spacing
- subtle borders
- limited accent usage
- consistent severity indicators
- readable evidence blocks
- monospace typography for technical evidence where appropriate

Avoid visual noise.

---

# 10. Responsive Behavior

The core audit experience must remain usable on:

- desktop
- laptop
- tablet

The desktop layout should be optimized for investigation because this is primarily a technical tool.

---

# 11. UX Principle

The UI should make the system's intelligence visible.

Do not merely show:

    "AI Readiness Score: 72"

Instead show:

    "6 findings"

    "2 high-impact discoverability issues"

    "Evidence available"

    "Here is what should be fixed first"

The evidence is the product.

---

# 12. Final Principle

The UI should feel like a tool built by engineers for people investigating websites.

It should not feel like a template generated from:

    "Create a modern AI SaaS dashboard."
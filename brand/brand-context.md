# Brand Context Guide

<!--
  client:        [Client Name]
  version:       1.0
  last_updated:  YYYY-MM-DD
  review_cadence: per-sync   # refreshed by the sync loop; event-driven, not date-checked
  maintained_by: [Your Name / Team]
  # Version history lives in brand/CHANGELOG.md. Never accumulate change narratives in
  # this block — this file is loaded into every project chat, and history bloats it.
  sync:                          # Consumed by the brand-sync skill. Fill in per client.
    stakeholders:  [Full Name One, Full Name Two, Full Name Three]   # people whose call input drives the sync
    fathom_query:  [Client Name]                                     # Fathom meeting search term; defaults to client if omitted
    fathom_team:   [Fathom Team Name]                                # optional; delete this line if the client has no Fathom team
    teams_chat:    [Exact Microsoft Teams Chat Name]                 # destination chat for proposed brand-kit updates
    samples:                       # Consumed by the brand-kit-samples-refresh skill. Optional — every value has a fallback.
      planable_workspace: [Client Name]     # Planable workspace name; defaults to the client name when absent
      blog_path: [www.client.com/blog/]     # URL prefix identifying articles among GA4 landing pages; without it the article half of a samples refresh skips cleanly
      published_floor: [YYYY-MM-DD]         # optional; never sample content published before this date
-->

## 1. Company Overview

**Company Name:** [Full legal / trading name]
**Industry:** [Primary industry and sub-sector]
**Headquarters:** [City, Country]
**Founded:** [Year]
**Company Size:** [Employees / revenue band if relevant]
**Company Website URL:** [URL]
**Company LinkedIn Page URL:** [URL]

**One-line description:**
> [A single sentence explaining what the company does and for whom.]

**Boilerplate (approved):**
> [The standard "About [Company]" paragraph used in press releases and bios. 2–3 sentences maximum.]

---

## 2. Brand Positioning

**Positioning Statement:**
> For [target audience], [Company] is the [category] that [key benefit] because [reason to believe].

**Brand Promise:**
> [One sentence: what the brand commits to delivering every time.]

**Brand Purpose / Mission:**
> [Why the company exists beyond making money.]

**Brand Vision:**
> [Where the company is heading — aspirational future state.]

---

## 3. Key Differentiators

List 3–5 things that genuinely set this brand apart. Be specific — avoid generic claims like "great customer service."

1. **[Differentiator Name]** — [One-sentence explanation with proof point if available]
2. **[Differentiator Name]** — [One-sentence explanation]
3. **[Differentiator Name]** — [One-sentence explanation]

---

## 4. Target Audiences

### Primary Audience

| Attribute         | Detail                                      |
|-------------------|----------------------------------------------|
| **Segment Name**  | [e.g. "Mid-market CFOs"]                     |
| **Demographics**  | [Age range, seniority, industry, geography]  |
| **Pain Points**   | [Top 2–3 problems they need solved]          |
| **Motivations**   | [What drives their decisions]                |
| **Objections**    | [Common reasons they hesitate or say no]     |
| **Channels**      | [Where they consume content / make decisions] |

### Secondary Audience

| Attribute         | Detail                                      |
|-------------------|----------------------------------------------|
| **Segment Name**  | [e.g. "Technical evaluators"]                |
| **Demographics**  | [Age range, seniority, industry, geography]  |
| **Pain Points**   | [Top 2–3 problems they need solved]          |
| **Motivations**   | [What drives their decisions]                |
| **Objections**    | [Common reasons they hesitate or say no]     |
| **Channels**      | [Where they consume content / make decisions] |

<!-- Copy the table block above for additional audience segments as needed. -->

---

## 5. Competitive Landscape

### Direct Competitors

| Competitor        | Website URL                  | LinkedIn Company Page URL                  | Positioning / Claim                    | Our Advantage Against Them              |
|-------------------|------------------------------|--------------------------------------------|----------------------------------------|-----------------------------------------|
| [Competitor 1]    | [https://competitor1.com]    | [https://linkedin.com/company/competitor1] | [How they position themselves]         | [Why we win]                            |
| [Competitor 2]    | [https://competitor2.com]    | [https://linkedin.com/company/competitor2] | [How they position themselves]         | [Why we win]                            |
| [Competitor 3]    | [https://competitor3.com]    | [https://linkedin.com/company/competitor3] | [How they position themselves]         | [Why we win]                            |

### Indirect Competitors / Alternatives

- **[Alternative 1]** — [e.g. "Doing nothing / manual process"]
- **[Alternative 2]** — [e.g. "In-house build"]

---

## 6. Products & Services Summary

Provide a brief reference so Claude can accurately describe offerings without hallucinating details.

### [Product / Service 1]

- **What it is:** [One sentence]
- **Who it's for:** [Primary audience segment]
- **Key features:** [3–5 bullet points]
- **Pricing model:** [e.g. subscription, project-based, freemium — or "Do not reference pricing"]

### [Product / Service 2]

- **What it is:** [One sentence]
- **Who it's for:** [Primary audience segment]
- **Key features:** [3–5 bullet points]
- **Pricing model:** [e.g. subscription, project-based, freemium — or "Do not reference pricing"]

<!-- Repeat for additional products/services. -->

---

## 7. Key Messages

The core messages the brand wants to land, ranked by priority.

1. **[Message 1]** — [Supporting proof point or stat]
2. **[Message 2]** — [Supporting proof point or stat]
3. **[Message 3]** — [Supporting proof point or stat]

---

## 8. Sensitive Topics & Guardrails

Things Claude should avoid or handle carefully when representing this brand.

> **Durable rules only.** This section is for standing guardrails that always apply.
> Time-bound rules — embargoes, hold-until-announced wins, dates awaiting verification,
> proof points that cannot be used *yet* — belong in `brand/live-holds.md`, where each
> carries a scope, a lift condition and a review-by date. If a rule has an expiry, it is
> a hold, not a guardrail.

- **Never claim:** [e.g. "Never claim regulatory approval that hasn't been granted"]
- **Avoid topics:** [e.g. "Do not comment on competitor pricing"]
- **Legal requirements:** [e.g. "All financial content must include the disclaimer: '...'"]
- **Cultural sensitivities:** [e.g. "Avoid idioms that don't translate well — audience is pan-Asian"]

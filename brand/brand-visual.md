# Brand Visual Guide

<!--
  client:        [Client Name]
  version:       2.0
  last_updated:  YYYY-MM-DD
  review_cadence: per-rebrand   # rebuilt when the design system changes; event-driven, not date-checked
  maintained_by: [Your Name / Team]
-->

> **Purpose:** This file gives our tools the visual values they actually read when
> generating branded documents, decks, reports and HTML — plus a home for visual
> rulings that otherwise die in delivery threads. It is deliberately small. It is
> **not** a copy of the client's brand guidelines: those live wherever the client
> keeps them, and § "Visual source" points there. Duplicating a design system into
> markdown rots at the next rebrand; pointing at it does not.

---

## Visual source

Required, even when nothing else in this file is filled. A kit that cannot name
its visual source has a real finding; a kit that names one and declines to
duplicate it does not.

| Field | Value |
|---|---|
| Canonical source | [e.g. "Corporate brand guidelines v3 (PDF, client's DAM)" / "Design-token set in the client's design system repo" / "Parent-group guidelines — this brand realigns to them"] |
| Where it lives | [e.g. "Shared drive link / DAM URL / repo path — wherever the team actually fetches it"] |
| State | [e.g. "current" / "rebrand in progress, new system expected [Month Year] — values below will be re-cut then" / "awaiting guidelines from the client — nothing below is real yet"] |
| Owner / contact | [e.g. "Client marketing lead / our design lead"] |

> If the client publishes **design tokens** (the W3C DTCG format is the common
> shape), point at the token set here and treat § "Production palette & type"
> as a derived excerpt, never a competing source.

---

## Production palette & type

The values our document, report and HTML generators read. Keep it to what
production uses — the full palette stays in the canonical source.

### Palette

| Name | Hex | Usage |
|------|-----|-------|
| [e.g. "Primary"] | `#1A2B4A` | [e.g. "H1 text, accents, chart series 1"] |
| [e.g. "Secondary"] | `#00B4A6` | [e.g. "Highlights, links, chart series 2"] |
| [e.g. "Neutral"] | `#F2F4F6` | [e.g. "Panel and callout backgrounds"] |
| [e.g. "Text"] | `#1A1A1A` | [e.g. "Body text"] |

### Type

| Role | Font | Fallback stack | Notes |
|------|------|----------------|-------|
| Headings | [e.g. "Inter"] | [e.g. "'Inter', 'Helvetica Neue', sans-serif"] | [e.g. "600/700; embed or install for Word outputs"] |
| Body | [e.g. "Inter"] | [e.g. "'Inter', 'Helvetica Neue', sans-serif"] | [e.g. "400"] |

- **Heading case:** [e.g. "H1 AP Title Case; H2 and below sentence case" — this rule is read by every document generator, so state it exactly]

---

## Document & deck conventions

The rules that are native to *our* deliverables and exist in no guidelines PDF.
This section, not the palette, is usually where the real value is.

- **Word documents:** [e.g. "Cover: title + client logo; footer: page number right; DRAFT watermark until sign-off"]
- **Charts and data visuals:** [e.g. "Flat bars/lines in palette order above; no 3D; minimal gridlines"]
- **Slides:** [e.g. "16:9; logo top-left; max ~40 words per content slide"]
- **Report covers:** [e.g. "Match the reports index page; no descriptive copy on the cover"]

---

## Visual decisions

Rulings made in delivery — client feedback on lockups, motion, layout density,
photo treatment — recorded here with the same provenance discipline as a hold,
so they stop being rediscovered by collision. Newest first. This table is
expected to grow continuously; it needs no rebrand to change.

| Date | Decision | Source |
|------|----------|--------|
| [YYYY-MM-DD] | [e.g. "Co-branding: never place our logo and a partner's side by side; stack with divider"] | [e.g. "Client design feedback, task link"] |
| [YYYY-MM-DD] | [e.g. "Motion: GIF over MP4, under 15s, loops, assume muted autoplay, no background music"] | [e.g. "Client comment, date"] |

---

## Asset locations

Where the real files live — a pointer, not an inventory.

- **Logos:** [e.g. "DAM folder / shared drive path; use primary on light, reversed on dark"]
- **Fonts:** [e.g. "Licensed via X; webfont kit at Y"]
- **Photography / template library:** [e.g. "Where approved imagery and deck templates live"]

---

## Extended specification (optional)

Grid systems, UI component patterns, email and digital-ad specs were part of
this template's v1 and were removed: no kit filled them in five months, and our
kits do not generate those channels. If a client engagement genuinely needs
them, restore the relevant v1 sections from this template's history rather than
re-inventing the tables — and prefer pointing at the client's design system.

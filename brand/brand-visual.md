# Brand Visual Guide

<!--
  client:        [Client Name]
  version:       1.0
  last_updated:  YYYY-MM-DD
  maintained_by: [Your Name / Team]
-->

> **Purpose:** This document gives our tools the specifications needed to generate branded HTML, presentations, artifacts, and design briefs. It is not a replacement for the full brand guidelines PDF — it is a machine-readable reference optimised for AI-assisted content production.

---

## 1. Colour Palette

### Primary Colours

| Name             | Hex       | RGB              | Usage Rules                                          |
|------------------|-----------|------------------|------------------------------------------------------|
| [e.g. "Navy"]    | `#1A2B4A` | `rgb(26,43,74)`  | [e.g. "Primary brand colour. Headings, CTAs, nav."]  |
| [e.g. "White"]   | `#FFFFFF` | `rgb(255,255,255)`| [e.g. "Default background. Body text on dark."]       |

### Secondary Colours

| Name               | Hex       | RGB                | Usage Rules                                          |
|--------------------|-----------|--------------------|------------------------------------------------------|
| [e.g. "Teal"]      | `#00B4A6` | `rgb(0,180,166)`   | [e.g. "Accent colour. Links, highlights, icons."]    |
| [e.g. "Light Grey"] | `#F2F4F6` | `rgb(242,244,246)` | [e.g. "Section backgrounds, card fills."]            |

### Functional / UI Colours

| Purpose    | Hex       | Usage                               |
|------------|-----------|--------------------------------------|
| Success    | `#2E7D32` | [e.g. "Confirmations, positive KPIs"] |
| Warning    | `#F9A825` | [e.g. "Alerts, caution states"]       |
| Error      | `#D32F2F` | [e.g. "Error messages, destructive actions"] |
| Info       | `#1565C0` | [e.g. "Informational callouts"]       |

### Colour Usage Rules

- **Maximum colours per layout:** [e.g. "3 brand colours + 1 neutral + 1 accent"]
- **Background/foreground contrast:** [e.g. "Minimum WCAG AA (4.5:1 for body text, 3:1 for large text)"]
- **Gradient usage:** [e.g. "Permitted: Navy → Teal, left to right. No radial gradients."]
- **Dark mode:** [e.g. "Not currently defined" or provide dark palette hex codes]

### CSS Custom Properties (for HTML outputs)

```css
:root {
  --brand-primary:    #1A2B4A;
  --brand-secondary:  #00B4A6;
  --brand-white:      #FFFFFF;
  --brand-light-grey: #F2F4F6;
  --brand-dark-text:  #1A1A1A;
  --brand-body-text:  #4A4A4A;
  --brand-success:    #2E7D32;
  --brand-warning:    #F9A825;
  --brand-error:      #D32F2F;
}
```

---

## 2. Typography

### Font Families

| Role           | Font Family                  | Fallback Stack                                | Weight(s)       |
|----------------|------------------------------|-----------------------------------------------|-----------------|
| **Headings**   | [e.g. "Inter"]               | [e.g. "'Inter', 'Helvetica Neue', sans-serif"] | [e.g. "600, 700"] |
| **Body**       | [e.g. "Inter"]               | [e.g. "'Inter', 'Helvetica Neue', sans-serif"] | [e.g. "400, 500"] |
| **Monospace**  | [e.g. "JetBrains Mono"]      | [e.g. "'JetBrains Mono', 'Fira Code', monospace"] | [e.g. "400"]  |
| **Display**    | [e.g. "Playfair Display"]    | [e.g. "'Playfair Display', Georgia, serif"]    | [e.g. "700"]    |

**Google Fonts import (if applicable):**
```
https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap
```

### Type Scale

| Element        | Size   | Weight | Line Height | Letter Spacing | Colour             |
|----------------|--------|--------|-------------|----------------|---------------------|
| H1             | 40px   | 700    | 1.2         | -0.02em        | `--brand-primary`   |
| H2             | 32px   | 600    | 1.25        | -0.01em        | `--brand-primary`   |
| H3             | 24px   | 600    | 1.3         | 0              | `--brand-dark-text` |
| H4             | 20px   | 600    | 1.35        | 0              | `--brand-dark-text` |
| Body           | 16px   | 400    | 1.6         | 0              | `--brand-body-text` |
| Body (small)   | 14px   | 400    | 1.5         | 0.01em         | `--brand-body-text` |
| Caption        | 12px   | 500    | 1.4         | 0.02em         | `--brand-body-text` |
| Button / CTA   | 14px   | 600    | 1           | 0.03em         | `--brand-white`     |

### Typography Rules

- **Heading case:** [e.g. "Sentence case for all headings. Never ALL CAPS except acronyms."]
- **Maximum line width:** [e.g. "680px / ~75 characters for body text"]
- **Paragraph spacing:** [e.g. "1em between paragraphs; no first-line indent"]
- **Emphasis:** [e.g. "Use bold for emphasis, not italics or underline. Never use colour alone for emphasis."]

---

## 3. Logo Usage

### Available Logo Variants

| Variant              | Filename              | Use When                                       |
|----------------------|-----------------------|-------------------------------------------------|
| Primary (full colour) | `logo-primary.svg`   | [e.g. "Default. Use on white or light backgrounds."] |
| Reversed (white)     | `logo-reversed.svg`   | [e.g. "On dark or photographic backgrounds."]   |
| Monochrome (black)   | `logo-mono.svg`       | [e.g. "Single-colour print, fax, engraving."]   |
| Icon / mark only     | `logo-icon.svg`       | [e.g. "Favicons, social avatars, small spaces."] |

### Logo Rules

- **Minimum clear space:** [e.g. "Equal to the height of the logomark on all sides"]
- **Minimum display size:** [e.g. "24px height for digital; 10mm for print"]
- **Placement:** [e.g. "Top-left for web headers; centred for presentations and documents"]
- **Never:** [e.g. "Stretch, rotate, recolour, add drop shadows, place on busy backgrounds without overlay"]

---

## 4. Imagery & Photography

### Photography Style

- **Subjects:** [e.g. "Real people in real work environments. No stock photo clichés (handshakes, pointing at screens)."]
- **Lighting:** [e.g. "Natural or soft studio lighting. Avoid harsh flash or heavy filters."]
- **Colour treatment:** [e.g. "Slightly desaturated, warm whites. No heavy colour grading."]
- **Composition:** [e.g. "Generous negative space on one side for text overlay."]
- **Diversity:** [e.g. "Reflect our audience: pan-Asian, mixed age, gender-balanced."]

### Illustration Style

- **Style:** [e.g. "Flat vector, geometric. No 3D renders or skeuomorphism."]
- **Colour palette:** [e.g. "Use brand palette only. Primary + one accent per illustration."]
- **Line weight:** [e.g. "2px uniform stroke if using outlines."]
- **Icons:** [e.g. "Line icons, 24×24 base grid, 1.5px stroke, rounded caps."]

### Stock Image Guidelines

- **Approved sources:** [e.g. "Unsplash, Pexels, or licensed via Shutterstock account"]
- **Avoid:** [e.g. "Overly staged scenes, obvious stock photo smiles, clip art, AI-generated faces"]
- **AI-generated imagery policy:** [e.g. "Permitted for internal concepts only. Never in client-facing materials without approval."]

---

## 5. Layout & Spacing

### Grid System

- **Columns:** [e.g. "12-column grid for web; 2–3 columns for print"]
- **Gutter width:** [e.g. "24px (desktop), 16px (mobile)"]
- **Max content width:** [e.g. "1200px with 80px horizontal padding"]
- **Mobile breakpoint:** [e.g. "768px"]

### Spacing Scale

Use a consistent spacing scale (base unit = 8px):

| Token  | Value | Use For                                |
|--------|-------|----------------------------------------|
| `xs`   | 4px   | Tight spacing within components        |
| `sm`   | 8px   | Icon-to-label gaps, inline spacing     |
| `md`   | 16px  | Component internal padding             |
| `lg`   | 24px  | Between related sections               |
| `xl`   | 40px  | Between distinct content sections      |
| `2xl`  | 64px  | Major section breaks, hero padding     |
| `3xl`  | 96px  | Page-level vertical rhythm             |

### Component Patterns

| Component       | Corner Radius | Shadow                        | Border                      |
|-----------------|---------------|-------------------------------|-----------------------------|
| Cards           | [e.g. "8px"]  | [e.g. "0 2px 8px rgba(0,0,0,0.08)"] | [e.g. "1px solid #E5E7EB"] |
| Buttons         | [e.g. "6px"]  | [e.g. "None"]                 | [e.g. "None (filled) / 2px solid primary (outlined)"] |
| Input fields    | [e.g. "6px"]  | [e.g. "None"]                 | [e.g. "1px solid #D1D5DB"]  |
| Modals / popups | [e.g. "12px"] | [e.g. "0 8px 24px rgba(0,0,0,0.15)"] | [e.g. "None"]         |

---

## 6. Presentation Slide Defaults

Use these when Claude generates `.pptx` or HTML slide decks.

- **Slide dimensions:** [e.g. "16:9 (1920×1080)"]
- **Title slide:** [e.g. "Logo top-left, title centred, subtitle below in lighter weight"]
- **Content slides:** [e.g. "Heading top-left, body text left-aligned, imagery right half"]
- **Maximum text per slide:** [e.g. "40 words excluding headings"]
- **Chart style:** [e.g. "Flat bars/lines in brand palette. No 3D. Minimal gridlines."]
- **Footer:** [e.g. "Company name (left), confidentiality notice (centre), page number (right)"]

---

## 7. Email & Digital Ads

### Email

- **Max width:** [e.g. "600px"]
- **Header:** [e.g. "Logo centred, 20px padding top and bottom"]
- **CTA button:** [e.g. "Primary colour background, white text, 6px radius, 48px height minimum"]
- **Footer:** [e.g. "Light grey background, unsubscribe link, registered address"]

### Digital Ads

- **Standard sizes:** [e.g. "1200×628 (social), 1080×1080 (square), 1080×1920 (story)"]
- **Text overlay limit:** [e.g. "20% of image area (Meta guideline)"]
- **CTA placement:** [e.g. "Bottom-right for landscape, bottom-centre for square/portrait"]
- **Animation:** [e.g. "Subtle fade/slide only. Max 15 seconds. Loop max 3 times."]

# [Client Name] — Positioning

<!--
  client:        [Client Name]
  version:       v1 (document identity — bump only on a strategic reframe)
  status:        DRAFT | FINAL — [approver name] sign-off [date] on [which items]
  last_updated:  YYYY-MM-DD
  maintained_by: [Your Name]
  framework:     [The positioning framework this document applies — e.g.
                 "April Dunford — Obviously Awesome (five-component positioning)"
                 or "Geoffrey Moore — Crossing the Chasm (adoption life cycle)"]
  canonical:     This markdown file is the source of truth. Any branded .docx/PDF
                 is a generated deliverable — edit this file, then regenerate.

  CHOOSING THE FRAMEWORK — depends on the client's market maturity:
  - Established or well-understood market, competing against known alternatives
    → April Dunford's five-component framework.
  - Disruptive or category-creating product that must cross from early adopters
    to the mainstream → Geoffrey Moore's Crossing the Chasm.
  - Other frameworks may be added. Whichever is used, the document keeps the
    same shape: the Framework Analysis section carries the framework's own
    structure, and the Synthesis sections at the end are filled in for EVERY
    framework — they are the interface the rest of the kit consumes.

  GOVERNANCE — keep this file pure "what is true now":
  - Change history goes in brand/CHANGELOG.md, never in this header. Narrative
    rationale for a change goes in the pull request description.
  - Anything awaiting client confirmation ("flagged, not settled") is a live
    hold: record it in brand/live-holds.md with a scope and lift condition —
    or leave the change on an open PR until the client confirms.
  - Edits touching client-approved strategic content go through a PR, not a
    direct commit. Maintainer-remit word-level fixes may commit directly but
    still get a CHANGELOG entry.
  - Claims and statistics used here must exist in reference/evidence.md.
    Correct a claim there, then reconcile here — never fork the wording.
  - Switching frameworks is a strategic reframe: bump the document identity
    (v1 → v2), rebuild the document under the new framework, and reconcile
    the Synthesis sections and everything downstream of them.
-->

> **Status:** [e.g. "Approved — [approver] sign-off [date] on all strategic items."]
>
> **Framework:** [Framework name], chosen because [one line on the client's market maturity — e.g. "the client competes in an established market against known alternatives" or "the product is category-creating and must cross from early adopters to mainstream buyers"]. The Framework Analysis below follows that framework's own structure; the Synthesis sections at the end are the same for every framework, because the rest of the kit builds on them.

---

## The house view *(optional)*

<!--
  If the positioning rests on a belief about how the client's market actually
  works (a structural problem, a buying-behaviour insight), state it here first
  so the analysis below can build on it. Delete this section if the positioning
  doesn't need one.
-->

[e.g. "Our client's buyers do most of their research before they ever speak to a vendor. By the time a prospect raises a hand, the shortlist is largely set — so the job of marketing is to be on it."]

---

## Framework Analysis

<!--
  The framework-specific body. Use the framework's OWN structure and section
  names — do not force one framework's headings onto another. For reference:

  Dunford — five components, built in order:
    1. Competitive alternatives  (what the buyer would do if the client
       didn't exist)
    2. Unique attributes         (what the client has that the alternatives
       don't)
    3. Value themes              (what those attributes enable for the buyer)
    4. Best-fit clients          (who cares most, defined by situation and
       behaviour)
    5. Market category           (the context that makes the value obvious)

  Moore (Crossing the Chasm):
    - Adoption life cycle position and the chasm (where the product sits;
      visionaries vs pragmatists)
    - Beachhead target segment   (the first pragmatist niche to win)
    - Whole product              (what must surround the core product for
      pragmatists to buy)
    - Market alternative and product alternative (the two anchors that frame
      the category and the differentiation)
    - Competitive Positioning Compass
    - Moore's two-sentence claim

  Keep the components in the framework's prescribed order — most frameworks
  build sequentially, and the synthesis only works if the argument does.
-->

### [Framework component 1]

[Analysis.]

### [Framework component 2]

[Analysis.]

### [Framework component 3]

[Analysis.]

<!-- Add sections per the framework — as many as it prescribes. -->

---

# Synthesis

<!--
  REQUIRED FOR EVERY FRAMEWORK. These sections are the contract the rest of
  the kit depends on: strategy/message-house.md builds its pillars on the core
  claims, brand-context.md distils the statement and best-fit profile, and
  copy tasks take proof points from the evidence register. Where the Framework
  Analysis above already contains a section that answers one of these (e.g.
  Dunford's Best-fit clients, Moore's beachhead), keep the full detail there
  and make the section here a compact summary that points to it.
-->

## Positioning statement

<!--
  The framework's synthesis in its native form — e.g. Dunford's positioning
  statement, or Moore's two-sentence claim ("For (target) who (need),
  (product) is a (category) that (benefit). Unlike (alternative),
  (differentiation).").
-->

[Full statement.]

**One-sentence version:**
> [Client Name] is the [category / frame] that [mechanism] to [outcome] for [buyer].

## Core claims

*The claims the messaging builds on — `strategy/message-house.md` pillars map 1:1 to these.*

1. **[Claim 1 title]** — [one or two lines; where the framework detail lives, name the section above].
2. **[Claim 2 title]** — [as above].
3. **[Claim 3 title]** — [as above].

## Best-fit clients

*Who this positioning is for — Dunford's best-fit profile, Moore's beachhead segment, or the equivalent. A senior salesperson should be able to disqualify a prospect from this section in minutes.*

- **Who:** [role, seniority, company stage]
- **Situation:** [the observable symptoms that make them in-market]
- **Trigger:** [the events that turn the situation into a purchase]
- **Not a fit:** [explicit disqualifiers — positive emphasis where the client requires it]

## Market frame

*The context that makes the value obvious — Dunford's market category, or Moore's market-alternative / product-alternative anchors.*

[Client Name] is a [category label / frame of reference]. [Why this frame, in one or two lines — and any terminology distinctions (e.g. category label vs methodology claim) that copy must respect.]

## Proof points

<!--
  Every claim here must have a row in reference/evidence.md — that file is the
  register of approved wording, source, and vintage. List the claims in use;
  do not restate evidence detail here.
-->

- [Approved claim 1 — exact wording per reference/evidence.md]
- [Approved claim 2]
- [Approved claim 3]

*Gaps to close: [proof the positioning needs but doesn't yet have — tracked as `gap-to-close` rows in reference/evidence.md].*

## What this means in practice

<!--
  Standing execution rules that follow from the positioning. Register rules for
  individual terms belong in brand/brand-voice.md § "Vocabulary Rules" (Preferred Terms) — put a
  row here only when the rule is about how to argue, not which word to use.
-->

| Action | Rationale |
|---|---|
| [e.g. "Lead every asset with the structural problem before naming what the client does."] | [Why] |
| [e.g. "Use '[outcome claim]' as the standard outcome claim."] | [Why] |

## Downstream map

<!--
  What derives from this document. When this file changes, these are the files
  and assets to reconcile — in this order. Status tracking for an in-flight
  reconciliation belongs on the PR, not here.
-->

1. `strategy/message-house.md` — pillars map 1:1 to the core claims above.
2. `brand/brand-context.md` — its "Brand Positioning" and "Key Messages" sections distil this document and must never contradict it.
3. `brand/brand-voice.md` — vocabulary rulings that implement the positioning (preferred terms, register rules).
4. [External assets: website, sales deck, campaign briefs — list the ones this client actually has.]

---

*Owner: [name]. Framework: [name]. Next review: [date]. Version history: `brand/CHANGELOG.md`. Sign-off record: PR history on this file.*

# [Client Name] — Positioning Statement

<!--
  client:        [Client Name]
  version:       v1 (document identity — bump only on a strategic reframe)
  status:        DRAFT | FINAL — [approver name] sign-off [date] on [which items]
  last_updated:  YYYY-MM-DD
  maintained_by: [Your Name]
  framework:     April Dunford — Obviously Awesome (five-component positioning)
  canonical:     This markdown file is the source of truth. Any branded .docx/PDF
                 is a generated deliverable — edit this file, then regenerate.

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
-->

> **Status:** [e.g. "Approved — [approver] sign-off [date] on all five components."]
>
> This document applies April Dunford's five-component positioning framework. Each component builds on the last — read them in order. The positioning statement at the end is the synthesis, not the starting point.

---

## The house view *(optional)*

<!--
  If the positioning rests on a belief about how the client's market actually
  works (a structural problem, a buying-behaviour insight), state it here first
  so every component below can build on it. Delete this section if the
  positioning doesn't need one.
-->

[e.g. "Our client's buyers do most of their research before they ever speak to a vendor. By the time a prospect raises a hand, the shortlist is largely set — so the job of marketing is to be on it."]

---

## 1. Competitive alternatives

*What would the best-fit buyer do if [Client Name] didn't exist?*

<!--
  List what buyers actually use today — including "do nothing" and "spreadsheet"
  if true. Name real competitors. For each alternative, say what it gets right
  and where it fails the buyer. Close the section by naming the gap none of
  them fills — that gap is what the rest of the document argues into.
-->

**[Alternative 1, e.g. "Status quo / manual process"].** [What it is, what it gets right, where it fails.]

**[Alternative 2, e.g. "Named direct competitors"].** [As above.]

**[Alternative 3, e.g. "In-house build / hire"].** [As above.]

**[Alternative 4, e.g. "The big incumbent"].** [As above.]

[Closing line: the gap none of these addresses — the gap [Client Name] is built to fill.]

---

## 2. Unique attributes

*What does [Client Name] have, specifically, that the alternatives don't?*

<!--
  3–5 attributes. Each must be a capability or feature the client genuinely has
  and the alternatives genuinely lack — not an aspiration. Guardrails that
  scope an attribute ("centrality, not totality") live in the attribute text
  itself so they travel with it.
-->

**[Attribute 1].** [What it is and why the alternatives can't match it.]

**[Attribute 2].** [As above.]

**[Attribute 3].** [As above.]

---

## 3. Value themes

*So what? What do those attributes actually enable for the buyer?*

<!--
  2–4 themes. Each theme converts one or more attributes into a buyer outcome.
  These themes become the pillars of strategy/message-house.md — keep the
  mapping 1:1 where possible.
-->

### Theme 1 — [Outcome-led title]

[Because (attribute), the buyer gets (outcome). Spell out the causal chain.]

### Theme 2 — [Outcome-led title]

[As above.]

### Theme 3 — [Outcome-led title]

[As above.]

---

## 4. Best-fit clients

*Which buyers care most about this value — and what makes them different from everyone else?*

<!--
  Define by situation and behaviour, not just firmographics. A senior
  salesperson should be able to read this and disqualify a prospect in minutes.
  Internal-only qualifiers (e.g. funding-stage shorthand) are marked as such —
  keep them out of external copy.
-->

**Role and seniority.**
[Who holds the budget and the problem.]

**Company stage.**
[Size, sector, sales-cycle shape.]

**Current situation.**
[The observable symptoms that make them in-market for this value.]

**Buying trigger.**
[The 2–4 events that turn the situation into a purchase.]

**Operating model.**
[How they want to work with a provider — and what makes a weaker fit.]

**What they're not.**
[Explicit disqualifiers. Positive emphasis where the client requires it — no negative exclusions the client hasn't approved.]

### Secondary best-fit *(optional)*

[A second segment the same value themes serve, with its distinct trigger.]

---

## 5. Market category

*What context makes the value obvious to the best-fit client?*

[Client Name] is a [category label].

[Why this category: the category should be the conclusion of the argument above, not a label bolted on. Note what buying criteria the category implies.]

*Terminology note (optional): [e.g. distinguish the category label from the methodology claim if the kit uses both].*

---

## Positioning Statement

For [best-fit buyer] at [company type] — who [situation / structural problem] — [Client Name] is the [category] that [core value].

Unlike [the alternatives, compressed], [Client Name] [unique attributes as reasons to believe].

**One-sentence version:**
> [Client Name] is the [category] that [mechanism] to [outcome] for [buyer].

---

## How the Framework Connects

| Framework component | [Client Name] answer |
|---|---|
| Structural problem *(if using a house view)* | [One line] |
| What buyers use instead (competitive alternatives) | [One line] |
| What we do differently (unique attributes) | [One line] |
| What this enables (value themes) | [One line] |
| Who cares most (best-fit clients) | [One line] |
| Context that makes value obvious (market category) | [One line] |

---

## Proof Points

<!--
  Every claim here must have a row in reference/evidence.md — that file is the
  register of approved wording, source, and vintage. List the claims in use;
  do not restate evidence detail here.
-->

- [Approved claim 1 — exact wording per reference/evidence.md]
- [Approved claim 2]
- [Approved claim 3]

*Gaps to close: [proof the positioning needs but doesn't yet have — tracked as `gap-to-close` rows in reference/evidence.md].*

---

## What This Means in Practice

<!--
  Standing execution rules that follow from the positioning. Register rules for
  individual terms belong in brand/brand-voice.md §5 (Preferred Terms) — put a
  row here only when the rule is about how to argue, not which word to use.
-->

| Action | Rationale |
|---|---|
| [e.g. "Lead every asset with the structural problem before naming what the client does."] | [Why] |
| [e.g. "Use '[outcome claim]' as the standard outcome claim."] | [Why] |

---

## Downstream Map

<!--
  What derives from this document. When this file changes, these are the files
  and assets to reconcile — in this order. Status tracking for an in-flight
  reconciliation belongs on the PR, not here.
-->

1. `strategy/message-house.md` — pillars map 1:1 to the value themes above.
2. `brand/brand-context.md` — §2 positioning and §7 key messages distil this document and must never contradict it.
3. `brand/brand-voice.md` — vocabulary rulings that implement the positioning (preferred terms, register rules).
4. [External assets: website, sales deck, campaign briefs — list the ones this client actually has.]

---

*Owner: [name]. Next review: [date]. Version history: `brand/CHANGELOG.md`. Sign-off record: PR history on this file.*

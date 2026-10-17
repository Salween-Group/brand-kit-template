# Evidence Register — [Client Name]

<!--
  last_updated: YYYY-MM-DD
  review_cadence: per-sync   # refreshed by the sync loop; event-driven, not date-checked

  The single register of every claim about the client and of the vetted research
  its arguments rest on (the Citation backbone).
  Proof points in strategy/positioning.md, foundation bullets in
  strategy/message-house.md, and key messages in brand/brand-context.md list
  claims — this file holds the approved wording, the evidence behind each one,
  and its status.

  Why one file: claims change on their own cadence (a client roster grows, a
  study is superseded, a stat turns out to be wrong). Correct the claim HERE,
  once, then reconcile the documents that cite it. Never let two documents
  carry different wordings of the same claim.

  When a claim is retired, set its status to `retired`, keep the row (so the
  correction is on record), and if the old wording must never reappear, add
  the phrase to brand/retired-language.md so CI catches it.
-->

## How to use this register

- **Scope — what must be here and what must not.** This register is authoritative for claims about **the client, its sub-brands and partners** (Proof points) and for the recurring third-party research the client's arguments rest on (Citation backbone). A third-party research fact a writer sources fresh for one piece does **not** need a row here — it needs a **named source in the copy** (the External research bullet below sets the conditions); promote it to a backbone row when it recurs or an argument starts leaning on it. The register's silence on a third-party fact is not a defect; **contradicting a row it does carry always is** — the row wins until it is corrected here, never silently in copy.
- **Writing content — claims about the client:** cite claims and statistics about the client (results, tenure, credentials, and client names attached to outcomes) only from Proof points rows with status `usable`, in their exact approved wording and correct vintage. If a claim about the client you want isn't here, flag it — don't improvise one.
- **External research — no row needed:** third-party research (surveys, analyst reports, industry studies) can be cited without a row here, provided that the source and its vintage are named in the sentence, never stated as a bare fact; the vintage is the fieldwork or publication date, not a forward-dated report title ("SEJ's State of Search 2027 survey, fielded June 2026", not "State of Search 2027" alone); the scope the study supports travels with the figure (who was surveyed, how many, which markets or platforms), and a small-cohort or correlational finding keeps its caveat; and it is never presented as the client's own finding. The Citation backbone below is research already vetted. A study outside it is allowed but flagged once for an account-team sense-check — a flag, not a block; promote it to a backbone row when it recurs or an argument starts leaning on it. The register's silence on a third-party fact is not a defect; contradicting a row it does carry always is. If a backbone row carries a caveat, the caveat travels with the citation.
- **AI-search and answer-engine figures — never registered:** follow the class note under the Citation backbone.
- **Client override:** a client may set a stricter rule (for example, "third-party sources need client approval before use"). Where one exists it wins inside the kit: state it here, in place of the External research bullet, and in brand-context.md § "Sensitive Topics & Guardrails". Never loosen a client's stricter rule to match this default.
- **Maintaining:** one row per claim. Correcting a claim is an edit to that row plus a CHANGELOG entry, then a reconciliation pass over the documents that cite it.

## Proof points (claims about the client)

<!-- Status: usable | gap-to-close | retired -->

| Claim (approved wording) | Status | Evidence / source | As of | Notes / where usable |
|---|---|---|---|---|
| [e.g. "Several clients have been with us more than 10 years."] | usable | [e.g. "Client tenure records, verified with ops"] | YYYY-MM | [e.g. "Any channel"] |
| [e.g. "Named case study with quantified pipeline impact"] | gap-to-close | [What's missing and who owns closing it] | YYYY-MM | [e.g. "Blocks the '[claim]' upgrade"] |
| [e.g. "Industry average tenure under three years"] | retired | [e.g. "Not supportable — the ANA/4As 2025 study puts it at ~7 years. Replaced by the row above, DD Mon YYYY."] | YYYY-MM | Do not publish. Phrase listed in brand/retired-language.md. |

## Citation backbone (external research)

<!--
  Third-party research the client's arguments rest on. These back the
  argument in thought-leadership and strategy contexts; whether positioning
  copy itself carries citations is a per-client call — record that call here.
-->

| Claim | Source | Vintage | Caveat |
|---|---|---|---|
| [e.g. "Buying groups of six to ten stakeholders"] | [e.g. "Gartner Digital B2B Buyer Survey"] | [e.g. 2017] | [e.g. "Cite by vintage"] |
| [e.g. "~70% of the buyer journey is complete before vendor contact"] | [e.g. "6sense"] | [e.g. 2023] | [e.g. "Compressing to ~60% in 2025 — check before citing"] |
| [e.g. "95:5 in-market rule"] | [e.g. "Ehrenberg-Bass / Dawes"] | [e.g. 2021] | [e.g. "Heuristic, not law — never cite as a measured figure"] |

**Note on AI-search and answer-engine figures — a deliberately unregistered class:** figures describing how AI assistants source, cite or rank content are **not** added to this backbone. The class re-orders in months, published studies disagree with one another because their query sets differ, and a row here reads as vetted — which invites citation without a freshness check. Absence from this register is therefore never the defect for a claim in this class. What the class does require, every time:

1. **Attribute in copy.** Name the source and the vintage in the sentence.
2. **Carry the scope.** Every rank claim in this class is true of a stated query class on a stated set of platforms. Strip the scope and the claim stops being true.
3. **Verify at the time of writing.** Check the figure against its source on the day the copy is drafted. Anything more than two quarters old is a candidate for correction, not a citation.

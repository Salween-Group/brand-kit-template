# Evidence Register — [Client Name]

<!--
  last_updated: YYYY-MM-DD

  The single register of every claim, statistic, and citation the kit uses.
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

- **Writing content:** cite claims and statistics only from rows with status `usable`, in their exact approved wording. If a claim you want isn't here, flag it — don't improvise one.
- **External citations:** cite by correct vintage (e.g. "Gartner 2017", not "Gartner"). If a row carries a caveat, the caveat travels with the citation.
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

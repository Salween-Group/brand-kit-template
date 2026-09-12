# Brand Kit Template
Starting template for our client brand kits. Markdown files for use with LLMs and other tools.

### What each file does

| File | Purpose | When the tools use it |
|---|---|---|
| `strategy/positioning.md` | The full positioning argument — framework chosen per client market maturity (e.g. April Dunford's five-component positioning, or Geoffrey Moore's Crossing the Chasm), always ending in the same framework-agnostic Synthesis sections — canonical for all strategy | Positioning, messaging-architecture, website, and campaign-strategy work — **not** loaded for everyday copy |
| `strategy/message-house.md` | Messaging architecture: roof, pillars, language bank — derived from the positioning | Strategy and messaging work, campaign planning — **not** loaded for everyday copy |
| `brand/brand-context.md` | Positioning distilled, audiences, competitors, products, durable guardrails | Understanding who the brand is and who it speaks to |
| `brand/brand-voice.md` | Tone, vocabulary, writing rules, example pairs | Writing any copy or content |
| `brand/brand-visual.md` | Colours, typography, spacing, layout, slide/email defaults | Generating HTML, presentations, design briefs |
| `brand/live-holds.md` | Time-bound holds: embargoes, hold-until-announced items, changes awaiting client confirmation — each with scope, lift condition, review-by date | Checked before finalising content; entries are removed when they lift |
| `brand/retired-language.md` | Phrases that were once canonical and are now superseded — enforced by CI | Never quoted in content; CI fails the build if a listed phrase reappears |
| `brand/CHANGELOG.md` | Kit version history plus the ledger of Fathom calls already mined | Reviewed on GitHub; read by brand-sync for call dedupe — never loaded into content chats |
| `project-instructions.md` | System prompt tying the guides together | Pasted into project/app instructions or prompts |
| `reference/evidence.md` | Register of every claim, statistic, and citation — approved wording, source, vintage, status | Cited whenever content uses a claim or statistic |
| `reference/approved-copy-samples.md` | Full-length examples of approved client copy | Calibrating voice, rhythm, and structure when writing content |

### Strategy layer vs operational layer

The kit has two tiers, and precedence between them is explicit:

- **`strategy/`** is the source argument. `positioning.md` is canonical for all strategic
  content; `message-house.md` derives from it (pillars map 1:1 to its Synthesis core claims).
  These files load only for strategy-shaped work — positioning, messaging, website,
  campaign planning.
- **`brand/`** is the operational distillation, loaded for everyday content work.
  `brand-context.md`'s "Brand Positioning" and "Key Messages" sections summarise the positioning and must never contradict it.
  If they disagree, the strategy file wins and the brand file gets a reconciliation pass.

Keeping the tiers separate keeps everyday contexts lean: a LinkedIn post loads the
distillation, not the 300-line argument behind it.

### Durable vs temporary rules

`brand-context.md` and the `strategy/` files hold the durable view of the brand — they
should change slowly. Anything with an expiry (an embargo, a hold-until-announced win, a
change awaiting client confirmation) goes in `brand/live-holds.md` instead, and is deleted
when its lift condition is met. Change history goes in `brand/CHANGELOG.md`, never in the
brand or strategy files themselves — history in the content files gets loaded into every
project chat and crowds out the content.

### Governance: how changes happen

- **Git is the version machinery.** Content files stay pure "what is true now". Change
  history lives in `brand/CHANGELOG.md`; the narrative rationale for a change lives in
  the pull request description. No embedded changelog headers.
- **Client sign-off maps to PRs.** Maintainer-remit edits (word-level fixes, factual
  corrections) commit directly with a CHANGELOG entry. Anything touching client-approved
  strategic content goes through a PR — and if it needs client confirmation, the open PR
  *is* the hold: it stays open until the client confirms. (Alternatively, merge with a
  scoped entry in `brand/live-holds.md` whose lift condition is the client's confirmation.)
- **Claims live in one place.** Every claim, statistic, and citation has a row in
  `reference/evidence.md`. Correct it there once, then reconcile the documents that cite
  it — never fork a claim's wording across files.
- **Superseded copy is machine-checked.** When a hero, claim, or vocabulary ruling is
  replaced, the dead phrase goes into `brand/retired-language.md` the same day. CI
  (`.github/workflows/retired-language-check.yml`) greps the kit on every push and PR
  and fails the build if a retired phrase reappears.
- **Generated deliverables are build products.** The markdown is the source of truth;
  branded .docx/PDF versions are regenerated from it, never edited directly.
- **The voice-guardian pack is a build product too.** An optional
  `reference/voice-guardian-pack.md` — a single shareable file compiling the kit's voice
  rules, vocabulary, examples, and usable claims for deployment as a custom-GPT knowledge
  file or skill reference — is generated by the voice-guardian-pack skill, stamped with
  the source versions and the source commit it was built from, and never edited directly.
  Two workflows guard it, and kits without a pack skip both:
  `.github/workflows/pack-freshness-check.yml` fails any PR that changes a
  voice-relevant file without regenerating the pack, and
  `.github/workflows/pack-stale-on-main.yml` covers the gap the PR gate cannot see — a
  merge that lands voice-source changes without the pack (the gate only runs on PRs)
  opens a `pack-stale` issue on the kit, and the issue closes itself on the push that
  brings the pack current. The pack is exempt from the retired-language grep (it must
  quote retired phrases verbatim to enforce them). The last mile depends on the
  deployment: a mirror the assistant platform owns (for us, a per-client ClickUp file
  read by that client's brand-voice-guardian agent) syncs on a daily diff and reports
  success or failure, while a hand-uploaded GPT knowledge file — or a copy the client
  keeps themselves — stays a human step. Either way the pack's stamp is how you verify
  a deployed copy is current. The full method — pack anatomy, the
  shareable filter, and generation discipline — is documented in
  [`docs/voice-guardian-pack.md`](docs/voice-guardian-pack.md).
- **This public repo is guarded against confidential references.** This template is
  deliberately public, so a CI check (`.github/workflows/client-leakage-guard.yml` —
  this repository only, never client kits) greps every tracked file for a confidential
  term list held outside the repo and fails the build on a hit, reporting the file but
  never the term. Improvements backported from client kits are the known leak path;
  the guard makes that a build failure instead of an after-the-fact scrub.
- **Hold expiry is machine-watched.** Every hold in `brand/live-holds.md` carries a
  review-by date, and holds are expected to expire and be removed — so a scheduled
  workflow (`.github/workflows/holds-expiry-check.yml`) scans the file daily and
  maintains a single tracking issue listing any holds past review-by, for the account
  team to renew or lift. The issue closes itself once every date is current. An expired
  date never means a hold has lifted — the workflow surfaces it; a human confirms.
- **File freshness is machine-watched too.** Every core kit file declares a
  `review_cadence:` in its metadata block. Time-based values (`quarterly`, `monthly`,
  `annual`, `<N>d`) are date-checked daily by a second job in the same
  `holds-expiry-check.yml` workflow; event-driven values (`per-sync` — the file is
  refreshed by the sync loop; `per-rebrand`) and `exempt` (live-holds, whose per-hold
  review-by dates are watched separately) document the freshness contract without a
  date check. The clock reads `last_reviewed:` when present, falling back to
  `last_updated:` — so a review that concludes "still accurate, no changes" is recorded
  honestly by setting `last_reviewed`, never by faking a content change. Files past
  their cadence land in a single self-closing tracking issue, mirrored to the account
  team's ClickUp list like the holds issue. This turns owned review cadences from a
  calendar promise into a mechanism — stale calibration sources (an aging
  `approved-copy-samples.md` is the canonical case) get flagged where the team works.
- **The kit's structure is machine-checked.** Cross-references between kit files
  rot silently as holds are added and deleted, so a lint workflow
  (`.github/workflows/kit-lint.yml`) fails any push or PR that breaks the kit's
  referential integrity: every `brand/live-holds.md` → "Name" pointer must
  prefix-match a real hold heading (quotes normalised, so a heading's status
  suffix can change without breaking pointers — but deleting a hold without
  cleaning up its pointers fails the build); every hold must carry Scope, Lift
  condition, a real and plausible Review-by date, and Source; core files must
  carry real `last_updated` (and version) metadata plus a `review_cadence` from
  the freshness vocabulary (and a real `last_reviewed`, when present); and the
  evidence register must use its declared status vocabulary. History and build products
  (`brand/CHANGELOG.md`, the voice-guardian pack) are exempt from the pointer
  check. On this template, placeholder values downgrade to warnings.
- **Account-team issues mirror into ClickUp — opt-in by label.** Most kit issues are
  ops-facing and stay in GitHub, but holds past review-by are the account team's to
  triage, and account teams live in ClickUp, not GitHub notifications. So
  `.github/workflows/clickup-issue-sync.yml` mirrors issues carrying the `clickup`
  label onto the kit's ClickUp list: opening a labelled issue creates a task (assigned
  to the account manager), editing the issue updates the task, closing the issue
  closes the task. Nobody closes anything by hand in two places; the repo stays the
  source of truth. The holds-expiry check labels its tracking issue automatically;
  add the label by hand to mirror anything else. Opt-in means a future check can
  never spam the account team's list by default — and the label gates task creation
  only, so once mirrored, an issue follows through to close even if the label is
  removed. Per-kit wiring (which list, who to assign) lives in
  `.github/clickup-sync.yml`, shipped empty here so the sync self-skips until a kit
  configures it; the API token is a per-repo Actions secret, never a committed file.

- **Kit structure syncs from this template.** This repo is the canonical base schema:
  every client kit carries the same file inventory and the same CI workflows, and a
  structural improvement born in one kit lands here first, then rolls out — kits are
  never patched from each other. Each kit's README carries a schema stamp recording the
  template commit its structure was last synced to:

  ```
  <!--
    kit_schema_version:  2026-09-12   # date of the template commit this kit's structure matches
    template_commit:     0a1b2c3      # that commit's short sha
  -->
  ```

  An internal sync skill diffs a kit against this template — file inventory, workflow
  content, metadata conventions — and opens a draft PR bringing it up to date, never
  touching the kit's content; the stamp tells that diff where to start. Two exclusions
  are part of the schema contract: `docs/` is showcase material for this repository, not
  kit schema, and `client-leakage-guard.yml` is this repository only — a client kit
  legitimately contains its own client's name. The template carries no live stamp values
  of its own; it *is* the schema.

### File structure

```
brand-kit-template/
├── strategy/
│   ├── positioning.md
│   └── message-house.md
├── brand/
│   ├── brand-context.md
│   ├── brand-visual.md
│   ├── brand-voice.md
│   ├── live-holds.md
│   ├── retired-language.md
│   └── CHANGELOG.md
├── reference/
│   ├── evidence.md
│   └── approved-copy-samples.md
├── .github/
│   ├── clickup-sync.yml   (per-kit ClickUp wiring — empty in the template)
│   └── workflows/
│       ├── retired-language-check.yml
│       ├── kit-lint.yml
│       ├── client-leakage-guard.yml   (this repo only — not part of the kit schema)
│       ├── holds-expiry-check.yml
│       ├── pack-freshness-check.yml
│       ├── pack-stale-on-main.yml
│       └── clickup-issue-sync.yml
├── docs/
│   └── voice-guardian-pack.md
├── project-instructions.md
├── README.md
└── LICENSE
```

---

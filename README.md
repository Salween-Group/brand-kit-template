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
│   └── workflows/
│       └── retired-language-check.yml
├── project-instructions.md
├── README.md
└── LICENSE
```

---

# Brand Kit Template
Starting template for our client brand kits. Markdown files for use with LLMs and other tools.

### What each file does

| File | Purpose | When the tools use it |
|---|---|---|
| `brand-context.md` | Positioning, audiences, competitors, products, durable guardrails | Understanding who the brand is and who it speaks to |
| `brand-voice.md` | Tone, vocabulary, writing rules, example pairs | Writing any copy or content |
| `brand-visual.md` | Colours, typography, spacing, layout, slide/email defaults | Generating HTML, presentations, design briefs |
| `brand/live-holds.md` | Time-bound holds: embargoes, hold-until-announced items, unusable-yet proof points — each with scope, lift condition, review-by date | Checked before finalising content; entries are removed when they lift |
| `brand/CHANGELOG.md` | Kit version history plus the ledger of Fathom calls already mined | Reviewed on GitHub; read by brand-sync for call dedupe — never loaded into content chats |
| `project-instructions.md` | System prompt tying the guides together | Pasted into project/app instructions or prompts |
| `reference/approved-copy-samples.md` | Full-length examples of approved client copy | Calibrating voice, rhythm, and structure when writing content |

### Durable vs temporary rules

`brand-context.md` holds the durable, high-level view of the brand — it should change slowly.
Anything with an expiry (an embargo, a hold-until-announced win, a date to verify) goes in
`brand/live-holds.md` instead, and is deleted when its lift condition is met. Change history
goes in `brand/CHANGELOG.md`, never in the brand files themselves — history in the brand
files gets loaded into every project chat and crowds out the content.

### File structure

```
brand-kit-template/
├── brand/
│   ├── brand-context.md
│   ├── brand-visual.md
│   ├── brand-voice.md
│   ├── live-holds.md
│   └── CHANGELOG.md
├── reference/
│   └── approved-copy-samples.md
├── project-instructions.md
├── README.md
└── LICENSE
```

---

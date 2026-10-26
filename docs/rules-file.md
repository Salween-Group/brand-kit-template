# The rules file (`brand/rules.yml`)

`brand/rules.yml` is the machine-readable index of a kit's **mechanical** rules:
banned and retired terms, vocabulary pairs, protected terms, approved
boilerplate, holds, claim wording, the spokesperson roster, the spelling regime
and the production palette. The schema is
[`docs/rules.schema.json`](rules.schema.json).

It is a **build product**, like the voice-guardian pack. The markdown stays the
source people edit, sign off and argue about; `rules.yml` is regenerated from it
and never edited by hand.

## Why it exists

Tools that gate copy against a kit (the brand-gate engine, the retired-language
CI check, a write-time hook) need exact values. Today they get them by parsing
prose: guessing which quoted span in a banned-words bullet is the banned term
and which is the suggested replacement, which capitalised word in a hold is the
protected party, which table column is "not this". That guessing runs on every
check, nobody reviews it, and each kit's writing habits break it differently.

The rules file moves the interpretation to **one moment, when the kit changes**,
where a human reviews it in the PR diff. Consumers then load YAML and stop
guessing.

## Why YAML is not the source

Clients sign off on prose. The sync loop proposes prose. The reasoning behind a
rule ("cut after the March feedback round") only lives in prose. Making the
YAML canonical would split the kit into a file people read and a file tools
read, with the people's file drifting. Generating the YAML keeps one source and
still gives tools exact values.

## Anatomy

| Key | Mirrors | What a checker does with it |
|---|---|---|
| `generated` | — | Stamp: kit, source commit, source hash, source files. How you verify the file is current. |
| `spelling`, `style` | `brand-voice.md` writing-style and formatting rules | Regime check (en-GB / en-US); testable formatting rules (contractions, heading case, number and date style, em-dash density). |
| `mention_carve_out` | The kit's mention-vs-use rule, where it has one | Downgrades a quoted, corrective mention of a banned or retired term from FAIL to REVIEW. |
| `retired` | `brand/retired-language.md` | FAIL on any literal hit. |
| `banned` | `brand-voice.md` § "Banned Words & Phrases" | FAIL (or WARN) on a hit; `condition` and `exception` carry the rule's own narrowing for adjudication. |
| `vocabulary` | The Use This / Not This table | WARN or REVIEW on a not-term; advisory by nature. |
| `protected_terms` | Names and coined terms with an exact form | FAIL on a listed wrong form. |
| `boilerplate` | Approved boilerplate blocks | Diff any near-match against the approved text. |
| `holds` | `brand/live-holds.md` | FAIL on a `block` literal inside the hold's scope until `review_by`, then flag for renewal. |
| `claims` | `reference/evidence.md` § "Proof points" | Usable wording to match against; retired and gap rows to catch. |
| `roster` | `brand-context.md` § "Approved spokespeople" | Name and title check; an empty roster means nobody may be quoted as the brand. |
| `palette` | `brand-visual.md` § "Palette" | Hex values and tokens for generators. One entry per colour. |
| `pairings` | `brand-visual.md` § "Colour pairings" | Foreground/background pairs by token, each with its permitted use. The rules check computes the contrast ratio of each. |
| `judgement_only` | Every rule-bearing section not extracted above | Nothing mechanical: the list tells the model tier what it must cover, and makes the coverage visible. |

Every rule carries a `source` pointer in the form kit lint already validates
(`brand/brand-voice.md § "Banned Words & Phrases"`, or the live-holds arrow
form). A rule without a source is a schema error.

## Generation discipline

1. **Generate in the same PR as the markdown change.** Whatever changes a
   source file (the sync loop, a samples refresh, a manual edit) regenerates
   `rules.yml` before the PR is opened.
2. **Extract, never invent.** Every literal in `retired`, `banned`,
   `vocabulary`, `protected_terms`, `holds` and `boilerplate` must appear in
   the section its `source` names. If a rule cannot be expressed as literals,
   it goes in `judgement_only` with its source; it is never paraphrased into a
   literal it does not contain.
3. **Keep the preferred wording out of the banned lists.** A banned-words
   bullet that suggests a replacement puts the replacement in `instead`, never
   in `terms`.
4. **Full coverage.** Every section that carries a rule ends up either
   extracted or listed in `judgement_only`. The reviewer's question for the diff
   is "did this edit add, change or remove a rule, and does the YAML show it?"
5. **Stamp it.** `source_commit` is the commit the markdown was read at;
   `source_hash` is computed as below.

## The source hash

`source_hash` is `sha256:` followed by the SHA-256 hex digest of, for each path
in `generated.sources` in the listed order: the path, a newline, the file's
bytes with CRLF normalised to LF, and a newline. A file whose hash no longer
matches its sources is stale.

The default source list is:

```
brand/brand-voice.md
brand/retired-language.md
brand/live-holds.md
brand/brand-context.md
brand/brand-visual.md
reference/evidence.md
```

## Checks

`.github/workflows/rules-file-check.yml` runs on every push to `main` and every
PR. A kit without `brand/rules.yml` skips it. It fails when:

- the YAML does not validate against `docs/rules.schema.json` (fetched from
  this template's `main` branch);
- `source_hash` does not match the current source files (stale file: a source
  changed and the rules file was not regenerated in the same change);
- a `source` pointer does not resolve to a real section (same contract as kit
  lint: H2-H4 heading with numbering stripped, or a bold run-in label, matched
  by prefix, HTML comments ignored);
- a literal does not appear in the section its `source` names (the generator
  invented it);
- `generated.kit` does not name the repository the file is in;
- a palette hex or token does not appear in `palette_source`, or the palette
  carries two or more of this template's example values (`#1A2B4A`,
  `#00B4A6`, `#F2F4F6`, `#1A1A1A`): placeholders extracted as if they were the
  client's colours;
- a pairing names a token the palette doesn't define, or its two tokens don't
  appear in `pairings_source`;
- a pairing's contrast ratio is below what its use needs.

### Contrast

The ratio is WCAG 2.x: relative luminance from the sRGB hex values, then
(lighter + 0.05) / (darker + 0.05), compared unrounded. The thresholds are the
WCAG AA minimums:

| Use | Minimum | Covers |
|---|---|---|
| `body-text` | 4.5:1 | Running text and anything below large text |
| `large-text` | 3:1 | 18pt and up, or 14pt bold and up |
| `graphics` | 3:1 | Icons, chart marks, UI boundaries, focus indicators |
| `never` | — | Ruled out; listed so tools avoid it, not tested |

The ratio is always computed by the check, never read from prose. Where a
client's own guidelines declare a pairing the ratio does not support, the check
still fails: the generator records the pairing as the guidelines state it and
the account lead rules on it (narrow the use, add a darker variant, or accept
the guideline in writing and record the pairing as `never` for text). The
check does not test colours against each other beyond the pairings listed.

A kit's `brand-visual.md` that still carries two or more of the template's
example hex values gets a warning even when the rules file has no palette: it
means the production palette was never filled.

A stamped `source_commit` missing from the repository's history is a warning
only, because a squash merge orphans it. On this template, which carries no
rules file, the workflow checks that the schema is itself a valid JSON Schema
and runs the contrast function against reference values.

Running `reference/eval-cases.md` through the mechanical checks with the rules
file as input, and failing on a score drop, comes with the brand-gate change
that reads it.

## Interaction with the existing checks

- `rules.yml` quotes retired phrases verbatim by design. The retired-language
  check scans only `*.md` files, so no exemption is needed.
- Kit lint's section-reference check scans markdown only; the rules file's own
  pointers are validated by the rules check above.
- Until every kit carries a current rules file, consumers fall back to parsing
  the markdown when the file is missing or stale.

# Brand Eval Cases

<!--
  client:        [Client Name]
  version:       1.0
  last_updated:  YYYY-MM-DD
  review_cadence: quarterly   # refreshed alongside approved-copy-samples; also update whenever a rule the cases test changes
  maintained_by: [Your Name / Team]
-->

> **Purpose:** This file is the kit's answer key — short snippets of realistic copy, each labelled with whether it should **pass** or **fail** the kit's rules, and which rule decides it. Anything that regenerates or evolves — the voice-guardian pack on every rebuild, a brand-checking engine on every change — retakes this test and reports its score before the change merges. A score drop names exactly which rule enforcement broke.

> **Maintenance:** Aim for 15–30 cases. Cover every rule *family* the kit enforces (retired language, banned vocabulary, live holds, claims and evidence, boilerplate integrity, spelling and style, tone), and keep **pass cases** alongside the fail cases — a checker that flags everything is as useless as one that flags nothing, so the passes guard against over-flagging. Seed new cases from This-Not-That voice examples, real breaches caught in review or audit, and each samples refresh (the shortlist's "rule this exemplifies" rationale is a ready-made pass case). When a rule is retired or a hold lifts, update or retire its cases in the same change — kit lint's pointer checks will fail the build if a case still points at a rule that no longer exists, which is deliberate.

---

## How these cases are used

- **Voice-guardian pack regeneration** ends by running every case against the freshly built pack ("given this pack as your only brand knowledge, should this snippet pass or fail?") and reporting the score in the PR — e.g. `27/30 correct; missed: EC-04, EC-11, EC-19`. A score below the previous pack's is a red flag to resolve before merging, not after deployment.
- **Brand-checking tooling** (any skill or engine that gates copy against this kit) uses the same cases as its regression set: after an engine change, every case is re-run and misses are reported per case id.
- Scores are **advisory, human-reviewed** — a miss can mean the pack regressed, the engine regressed, or the case went stale. The reviewer decides which; the score's job is to make the question unskippable.

## Case format

One case per `###` heading, id `EC-NN` (stable — retire an id rather than reuse it). Fields, in order:

- **Expected:** `pass` or `fail` — nothing else.
- **Tests:** a pointer to the deciding rule, in one of the kit's two checked pointer forms: a section reference (file plus § and the quoted section name) for rules that live under a heading, or the live-holds arrow form for holds. Kit lint validates both, so a case pointing at a deleted rule fails the build.
- **Tier:** `deterministic` (a literal/mechanical rule — phrase lists, figures, spelling regime, roster titles) or `judgement` (tone, framing, scope — needs a model or a human to call).
- **Snippet:** the copy under test, as a blockquote. Realistic and short — one to three sentences, the way the violation (or the correct usage) actually shows up in drafts.
- **Why:** one line — what the right verdict turns on.
- **Source:** where the case came from — a real breach (say where and when), a This-Not-That example, a samples-refresh rationale, or `synthetic`.

Fail snippets deliberately quote retired phrases and hold-breaching copy verbatim — this file is exempt from the retired-language CI gate for exactly that reason (same rationale as the generated guardian pack). Never quote *actually confidential* material in a snippet; recreate the violation synthetically instead.

---

## Cases

<!-- Delete the three example cases below once the first real cases are added. -->

### EC-01: [Retired figure in body copy]

- **Expected:** fail
- **Tests:** brand/retired-language.md § "Retired phrases"
- **Tier:** deterministic
- **Snippet:**
  > [e.g. A sentence using a superseded figure exactly as it used to be approved — "Acme now serves 130 countries across its network."]
- **Why:** [e.g. Uses the retired reach figure; the current figure lives in the approved boilerplate.]
- **Source:** [e.g. synthetic, seeded from the retired-phrases table]

### EC-02: [Banned word with on-brand alternative available]

- **Expected:** fail
- **Tests:** brand-voice.md § "Banned Words & Phrases"
- **Tier:** deterministic
- **Snippet:**
  > [e.g. "We're thrilled to announce our latest launch!"]
- **Why:** [e.g. Banned effusive vocabulary plus an exclamation mark outside a quote.]
- **Source:** [e.g. This-Not-That Example 2]

### EC-03: [Approved claim used correctly]

- **Expected:** pass
- **Tests:** reference/evidence.md § "Proof points"
- **Tier:** deterministic
- **Snippet:**
  > [e.g. A sentence citing a `usable` register row in its exact approved wording.]
- **Why:** [e.g. Correct wording, correct vintage — must NOT be flagged; this case guards against over-flagging.]
- **Source:** [e.g. approved-copy-samples Sample Set 1]

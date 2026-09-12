# The voice-guardian pack

*How a brand kit ships its voice rules to tools that can't read the repo.*

## The problem

A brand kit like this one keeps every voice rule, vocabulary ruling, approved claim,
and live hold in governed markdown: changes land by PR, CI greps for retired language,
holds carry review-by dates. That governance only works where git works.

But most of the places people actually *write* can't see the repo. A custom GPT gets a
knowledge file. An assistant skill gets a reference document. A project chat gets pasted
context. The moment brand rules leave the repo as copy-pasted fragments, they fork:
the kit moves on, the deployed copy doesn't, and three weeks later an assistant is
confidently enforcing last month's vocabulary.

## The answer: a compiled build product

The voice-guardian pack is **one shareable markdown file** —
`reference/voice-guardian-pack.md` — that compiles everything a "brand voice guardian"
assistant needs to review and rewrite copy against the brand: role and behaviour, hard
rules, vocabulary, voice and tone, calibration examples, the usable-claims register, a
holds snapshot, and escalation rules.

The design principle is the same one this kit applies to its branded document
deliverables: **the markdown sources are the truth; the pack is a build product.** It is
generated from the kit, stamped with the source versions *and the source commit* it was
built from, and regenerated whenever the sources change. It is never edited directly —
a correction goes to the kit, and the kit regenerates the pack.

Three properties follow from treating it as a build:

- **Staleness is computable, not vibes.** The stamp carries the exact commit the pack
  was built from. `git log <stamped-sha>..main -- <the voice source files>` lists
  precisely what has changed since; an empty list means the pack is current.
- **Regeneration is incremental.** Diff the sources since the stamp, update only the
  affected sections plus the stamp itself. Small diffs keep the review meaningful.
- **CI can enforce that regeneration happened** without needing to judge its content
  (see "Enforcement" below).

## Anatomy: nine sections, in a deliberate order

LLMs weight early instructions more heavily, and context truncation eats from the
bottom. So the pack front-loads behaviour and rules, and puts narrative where it can
afford to be lost:

| § | Section | What it carries |
|---|---|---|
| 0 | About this file | Generated date, source commit, per-source version stamp, the build-product statement, the staleness rule |
| 1 | Role and behaviour | Review → violations with the rule cited → rewrite; never invent claims; strategy-level copy is flagged, never silently fixed; holds and retired phrases are never overruled |
| 2 | The brand in one page | One-liner, boilerplate (verbatim), house view, positioning sentence, core claims, audiences, locked hero |
| 3 | Hard rules | The durable guardrails as never/always statements |
| 4 | Vocabulary | Preferred-terms table, register rules, approved language bank, banned words, retired phrases **verbatim** |
| 5 | Voice and tone | Personality in practice, tone spectrum and shifts, writing style rules, POV |
| 6 | This, not that | Every calibration pair, compressed to off-brand / on-brand / why |
| 7 | Claims the copy may state | The approved claims in approved wording — and the closing rule that an unlisted claim does not exist |
| 8 | Live holds snapshot | Active holds as "flag, don't decide" items, or an explicit "none active as of [date]" |
| 9 | Escalation | When the guardian stops and hands off to a human |

Two ordering rules matter more than the rest. First, **§6 is the highest-value section
per token** — if the pack must shrink, cut the §2 brand narrative before touching a
single example pair. Second, compression never applies to rules: locked copy and
guardrails travel verbatim or near-verbatim; only explanatory prose gets compressed.
Never drop a rule to save space, and never add one the kit doesn't contain.

The pack also teaches its own reader to distrust it: §0 carries a **30-day staleness
rule** — past that, the guardian treats the holds snapshot as unverified and caveats
any ruling that depends on recent vocabulary, recommending a check for a regenerated
version.

## The shareable filter

The pack is built to leave the governed environment — an OpenAI-hosted knowledge file,
a shared skill — so it is compiled through a filter, applied to everything before it
enters. The organizing idea: **keep the rule, drop the paper trail.**

**Strip:**

- Personal names and attributions — maintainers, approvers, client stakeholders — and
  governance provenance: ruling dates, meeting references, changelog citations. The
  deployed guardian needs the rule, not the story of how it was decided.
- Competitor names and competitive intelligence. Competitor-derived rules are restated
  neutrally: "this positioning angle is category-saturated — never the headline claim"
  carries the rule without naming who saturated it.
- Internal-only material: internal shorthands (keeping the outward rule they produce),
  internal benchmarks, anything the kit marks as not cleared for external use.
  Unlaunched or unratified wording is in this class — the pack carries the *hold*
  ("flag any line presented as a tagline as premature") without reproducing the wording
  itself.
- Repo apparatus: changelog content, PR conventions, file paths as instructions. The
  deployed guardian cannot read the repo, so every rule must be self-contained.

**Keep, deliberately:**

- Retired phrases **verbatim** — the guardian cannot catch what it cannot see. The same
  goes for banned words and locked canonical copy.
- Claims approved for external use, with their guardrails travelling alongside (NDA
  rules, "unnumbered by design" notes).
- Register distinctions that are themselves rules ("X is internal register; client-facing
  copy prefers Y") — the distinction is guidance, not a leak.

And the tie-breaker: **when a filter call is unsure, withhold and say so in the PR
body.** A human reviewer can restore an over-cautious omission in thirty seconds; a
leaked line in a hosted knowledge file cannot be unshipped. The reviewer restores; the
pack never leaks.

## Generation discipline

- **The pack reflects merged canon.** It is built from freshly fetched `main`, never
  from a working copy that might be behind, and never from a feature branch — with one
  exception: regenerating on a still-open PR's branch to satisfy the freshness check on
  that PR. Even then, verify the PR is still open *immediately before pushing*: a PR can
  merge in the minutes between reading its state and pushing to its branch, and a
  regeneration pushed to a merged branch is stranded work that no gate will ever
  surface.
- **The pack lands by PR, never direct commit.** The shareable filter is exactly the
  kind of judgment a human should review. The PR body states the base commit the pack
  was built from, what was stripped, what was deliberately kept, and any borderline
  calls the reviewer may want to restore.
- **Regeneration starts with arithmetic, not rewriting.** Compare the stamped source
  commit against `main` for the voice source files. Nothing changed → the pack is
  current; say so and stop, rather than churning the stamp for its own sake.

## Enforcement: CI guards the build, judgment stays in the generator

Two workflows in this template guard the pack, and both skip cleanly on kits that don't
have one:

- [`pack-freshness-check.yml`](../.github/workflows/pack-freshness-check.yml) fails any
  PR that changes a voice-relevant source file without also regenerating the pack. The
  check is deliberately diff-based — *did the pack move when its sources moved* — not
  content-based. Regeneration judgment lives in the generator; CI only enforces that it
  ran.
- [`pack-stale-on-main.yml`](../.github/workflows/pack-stale-on-main.yml) covers the gap
  the PR gate cannot see. The freshness check runs on pull requests, so a merge that
  lands voice-source changes without a pack update leaves `main` silently stale — no
  red X anywhere. This watcher opens a `pack-stale` issue on the kit when that happens,
  and the issue closes itself on the push that brings the pack current.

The general lesson behind the second workflow: **never read the absence of a CI failure
as freshness.** A gate that runs on PRs proves nothing about what a merge race left on
`main`. The stamp is the ground truth; the issue is just the alarm.

One deliberate exemption: the pack must quote retired phrases verbatim in order to
enforce them, so `reference/voice-guardian-pack.md` is excluded from the
retired-language grep — alongside `brand/retired-language.md` itself and the changelog.

## Deployment, and the last mile

The pack deploys three ways:

- **Custom GPT:** §1 (role) and §3 (hard rules) go into the instructions field, where
  they can't be truncated away; the full pack becomes the knowledge file.
- **Assistant skill:** §1 becomes the skill's instruction body; the full pack rides
  along as a reference file.
- **Synced mirror:** the pack is mirrored into a file the assistant platform itself owns
  — for us, a "Brand Kit" file in each client's ClickUp folder, read by that client's
  brand-voice-guardian agent. A scheduled job diffs that mirror against the repository
  copy daily, updates it when the repository has moved, and reports on success as well
  as failure, so a sync that stops is visible rather than silent.

Whether the last mile can be automated depends on which of those you are in, and it is
worth being precise about it rather than assuming the worst case. A mirror the platform
can write to closes the loop: a regeneration reaches the deployed assistant within a day
and nobody has to remember. A hosted GPT or skill whose knowledge file is uploaded by
hand does not, and neither does a copy the client keeps themselves — those stay human
steps, every time, and the handoff message for every regeneration says so: *the
previously deployed copy is now stale until re-uploaded.*

The §0 stamp is what makes either case checkable: date plus source commit is how anyone,
including the client, verifies that a deployed copy is current — without having to trust
that a sync ran. It also makes two things legible that would otherwise read as faults. A
daily sync means a deployed copy can sit a day behind `main` and still be healthy. And a
mirror is a mirror: the repository remains the source of truth, so a rule edited in the
deployed copy is a divergence to reconcile, not a change.

## Why this shape

The whole system is one idea applied consistently: **brand voice is source code.**
Sources are governed and reviewed; deliverables are compiled, stamped, and reproducible;
staleness is detected by machines and resolved by humans; and anything that leaves the
governed environment passes through an explicit, reviewable filter on the way out. The
pack is just the compiler target that lets the governance travel to tools that will
never run `git pull`.

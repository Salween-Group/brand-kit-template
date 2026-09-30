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

The voice-guardian pack is **one markdown file** —
`reference/voice-guardian-pack.md` — that compiles everything a "brand voice guardian"
assistant needs to know about one client's brand to review and rewrite copy against it:
client scope, the brand narrative with its audiences and competitive landscape, hard
rules, vocabulary, voice and tone, calibration examples and approved published copy,
the usable-claims register, a holds snapshot, and escalation rules.

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
  affected sections, and rewrite the stamp. Small diffs keep the review meaningful.
- **The pack carries no history of itself.** What changed between versions belongs in
  the kit's changelog and the regeneration PR, not in the pack. The assistant reads
  every line of the pack on every review, so a growing log of past regenerations is
  pure cost to it.
- **CI can enforce that regeneration happened** without needing to judge its content
  (see "Enforcement" below).

## Anatomy: ten sections, in a deliberate order

LLMs weight early instructions more heavily, and context truncation eats from the
bottom. So the pack front-loads scope and rules, and puts narrative where it can
afford to be lost:

| § | Section | What it carries |
|---|---|---|
| 0 | About this file | Generated date, source commit, per-source version stamp, a link to the kit's repository and to the exact commit, the build-product statement, the staleness rule. Nothing else: no change notes |
| 1 | Client scope | Which client the rules cover and what it is, that they apply to that client's copy only, and the non-negotiables: never invent claims; strategy-level copy is flagged, never silently fixed; holds and retired phrases are never overruled |
| 2 | The brand in one page | One-liner, boilerplate (verbatim), house view, positioning sentence, core claims, differentiators, content framework and key messages, locked hero; then every audience and ICP segment in full, and the competitive landscape |
| 3 | Hard rules | The durable guardrails as never/always statements |
| 4 | Vocabulary | Preferred-terms table, register rules, approved language bank, banned words, retired phrases **verbatim** |
| 5 | Voice and tone | Personality in practice, tone spectrum and shifts, writing style rules, POV, and the copy conventions from the visual guide (heading case, caption and label capitalisation, text layout in documents) |
| 6 | This, not that | Every calibration pair, compressed to off-brand / on-brand / why; then real approved copy, quoted verbatim, a few samples per format |
| 7 | Claims the copy may state | The approved claims in approved wording — and the closing rule that an unlisted claim does not exist |
| 8 | Live holds snapshot | Active holds as "flag, don't decide" items, or an explicit "none active as of [date]" |
| 9 | Escalation | When the guardian stops and hands off to a human |

Two ordering rules matter more than the rest. First, **§6 is the highest-value section
per token** — if the pack must shrink, cut the §2 brand narrative prose before touching
a single example pair, and never cut the audience or competitor detail. Second,
compression never applies to substance: rules, locked copy, audience and competitor
detail, and approved samples travel verbatim or near-verbatim; only explanatory prose
and repetition get compressed. Never drop a rule to save space, and never add one the
kit doesn't contain.

**Completeness beats brevity.** The pack is the assistant's only view of the kit. Our
first packs were built compact, for hosted knowledge files with tight limits, and came
out at a fifth to a third of their kit's size: audiences cut to a line, competitors
stripped, approved samples reduced to fragments or described instead of quoted. A
reviewer working from that can judge a sentence, but not whether the copy speaks to the
right buyer or claims ground a competitor already owns. Real published copy matters for
the same reason: invented example pairs teach sentences, while real copy teaches rhythm,
structure, and how far a piece travels before it names a service. Samples are capped
per format so the section stays readable.

**And §0 stays small.** Left unchecked, each regeneration appended a paragraph to §0
explaining what it changed. Within a few weeks §0 was the largest section in one pack,
bigger than the claims register and the holds snapshot put together, and those notes
were exactly where personal names slipped past the filter. §0 is now rewritten whole on
every build, and the build fails if it carries anything but the stamp, the repository
links, the build statement, and the staleness rule.

**The pack carries brand rules, never assistant behaviour.** How to review, what a
review looks like, and any workflow steps belong to the assistant's own instructions,
written once for every client. Behaviour repeated in every pack drifts from those
instructions and, worse, contradicts them, and a reviewer told that "the kit is the
authority" then has two authorities.

**The headings are a contract.** The ten `## N. Heading` lines are identical in every
pack, number and text, verbatim and in order, because the assistant finds sections by
them from outside the repository, where no kit check can see a moved section. This is
the one place the kit's names-not-numbers convention doesn't apply: that convention
protects hand-written files a kit can insert sections into, and a generated pack has
one fixed layout. The contract is checked before every publish; a pack whose headings
differ is not published.

The pack also teaches its own reader to distrust it: §0 carries a **30-day staleness
rule** — past that, the guardian treats the holds snapshot as unverified and caveats
any ruling that depends on recent vocabulary, recommending a check for a regenerated
version.

## The filter

Everything passes through a filter before it enters the pack. The organizing idea:
**keep the rule, drop the paper trail.** How strict the filter is depends on where the
pack goes. Ours is published only to a document our own staff can read, so it carries
competitor context. A copy that leaves the organisation, such as a hosted GPT knowledge
file or a copy the client keeps, needs the stricter rule on competitors described below.

**Strip:**

- Personal names and attributions — maintainers, approvers, client stakeholders — and
  governance provenance: ruling dates, meeting references, changelog citations. The
  deployed guardian needs the rule, not the story of how it was decided.
- For any copy that leaves the organisation: competitor names and competitive
  intelligence. Competitor-derived rules are restated neutrally: "this positioning
  angle is category-saturated — never the headline claim" carries the rule without
  naming who saturated it.
- Internal-only material: internal shorthands (keeping the outward rule they produce),
  internal benchmarks, anything the kit marks as not cleared for external use.
  Unlaunched or unratified wording is in this class — the pack carries the *hold*
  ("flag any line presented as a tagline as premature") without reproducing the wording
  itself.
- Repo apparatus: changelog content, PR conventions, file paths as instructions. Every
  rule must be self-contained, readable without the repo. The one exception is the
  repository link in §0, which identifies the kit.
- Build history: regeneration notes, eval scores, filter notes. They belong in the
  changelog and the PR, never in the pack.
- From approved samples: engagement figures (internal benchmarks), and links the
  assistant cannot resolve.

**Keep, deliberately:**

- Retired phrases **verbatim** — the guardian cannot catch what it cannot see. The same
  goes for banned words and locked canonical copy.
- Claims approved for external use, with their guardrails travelling alongside (NDA
  rules, "unnumbered by design" notes).
- Register distinctions that are themselves rules ("X is internal register; client-facing
  copy prefers Y") — the distinction is guidance, not a leak.
- For an internal destination: the competitive landscape, named. It is context for
  judging copy, not permission for copy to name a competitor; the kit's rules on
  competitor commentary still apply.

And the tie-breaker: **when a filter call is unsure, withhold and say so in the PR
body.** A human reviewer can restore an over-cautious omission in thirty seconds; a
leaked line in a published document cannot be unshipped. The reviewer restores; the
pack never leaks.

## Generation discipline

- **The pack reflects merged canon.** It is built from freshly fetched `main`, never
  from a working copy that might be behind, and never from a feature branch — with one
  exception: regenerating on a still-open PR's branch to satisfy the freshness check on
  that PR. Even then, verify the PR is still open *immediately before pushing*: a PR can
  merge in the minutes between reading its state and pushing to its branch, and a
  regeneration pushed to a merged branch is stranded work that no gate will ever
  surface.
- **The pack lands by PR, never direct commit.** The filter is exactly the
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
  watched sources include the visual guide, because the pack carries its copy
  conventions. The
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

The pack deploys two ways:

- **Synced mirror:** the pack is mirrored into a document the assistant platform itself
  owns. For us, that is a "Brand Kit" doc in each client's ClickUp folder, read by one
  brand-guardian agent that serves every client: the agent's instructions define how to
  review, and each client's doc defines that client's brand. A scheduled job overwrites
  each doc with an exact copy of the repository's pack, reads it back to verify, and
  raises an issue on any failure, so a sync that stops or drifts is visible rather than
  silent.
- **Hand-uploaded copy:** a hosted GPT knowledge file, an assistant skill's reference
  file, or a copy the client keeps themselves. The assistant's behaviour lives in its own
  instructions field or skill body, not in the pack, and a copy that leaves the
  organisation goes through the stricter filter on competitors.

**A mirror must be a copy, not a rewrite.** Our first mirror was an agent that updated
each doc from the repository, and it paraphrased as it went: it dropped sentences,
merged two versions of one pack, and reintroduced a word the client had banned. Nothing
upstream could see it, because every upstream check reads the repository, not the doc.
Copying a file is a mechanical job; it should be done by code, overwrite the whole
document, and prove the result matches.

Whether the last mile can be automated depends on which of those you are in, and it is
worth being precise about it rather than assuming the worst case. A mirror the platform
can write to closes the loop: a regeneration reaches the deployed assistant within the
hour and nobody has to remember. A hand-uploaded copy does not, and neither does a copy
the client keeps themselves — those stay human steps, every time, and the handoff
message for every regeneration says so: *the previously deployed copy is now stale
until re-uploaded.*

The §0 stamp is what makes either case checkable: date plus source commit is how anyone,
including the client, verifies that a deployed copy is current — without having to trust
that a sync ran. And a mirror is a mirror: the repository remains the source of truth,
so a rule edited in the deployed copy is overwritten on the next sync, not kept.

## Why this shape

The whole system is one idea applied consistently: **brand voice is source code.**
Sources are governed and reviewed; deliverables are compiled, stamped, and reproducible;
staleness is detected by machines and resolved by humans; and anything that leaves the
governed environment passes through an explicit, reviewable filter on the way out. The
pack is just the compiler target that lets the governance travel to tools that will
never run `git pull`.

# SIGNAL Role Views — progress notes

Status doc for picking this work back up — written so another AI agent (or a human)
can continue it cold, without re-deriving context from scratch.

## What this repo is

A standalone, browser-viewable version of an interactive study/pitch tool built for
**Chibuzor Emekalam**, Frontend Lead on the **SIGNAL** project (a value-governance
pilot MVP that Auracule Tech Systems Ltd is building for a client called **Praxis**).

- `index.html` — the live page. Self-contained HTML/CSS/JS, no build step, no
  framework. Google Fonts (IBM Plex family) is the only external dependency.
- A mirror of this same file also lives as a Claude Artifact (private, Claude-account
  only): `https://claude.ai/code/artifact/7f43ec9e-acd4-48b7-a768-0aea306ff08a`.
  **These two copies are kept manually in sync** — there is no automation. Any
  content edit should be made in both places, or the two will drift (this has
  already happened once — see "Known past bugs" below).
- `note.txt` — a short plain-text summary of the CEO screen's four key numbers
  (Target, MAPV, Forecast, Delivered), written for quick re-reading before a
  presentation.
- `Auracule_SIGNAL_Architecture_Defence.pptx` — the source pitch deck this whole
  page is built from. **Gitignored deliberately** — it contains confidential client
  details (pricing, team allocation %, the client's name). Do not commit it.

A companion artifact exists for a different part of the same presentation —
**"Aldor Order Architecture"** (`https://claude.ai/code/artifact/0875f907-1490-4a54-beaf-2e3e9d6f6045`)
— covering a separate live demo of an already-shipped product (Aldor). It has not
been pushed to this repo; it only exists as a Claude Artifact.

## What SIGNAL actually is

A system that tracks a "promised value outcome" (e.g. "this initiative will save
$2m") through a 9-stage lifecycle, from a raw idea to independently proven, banked
value: **Opportunity → Value Case → Gates (PG0–PG5) → Commitment → Delivery →
Validated → Banked → Embed → Sustain**.

At any point, four different roles open SIGNAL and see the **same underlying data**,
reshaped around their own question:
- **CEO** — will we hit the target?
- **CFO** — can we trust the value?
- **Initiative Owner** — what do I personally owe right now?
- **Finance** — what's in my validation queue?

Chibuzor's actual job on the project: the **web app and all four role HOME
screens** — not the backend calculation/authority engine (that's a colleague,
Eseigbe's, job) and not the mobile app (a colleague, Nwakwue's, job).

## What `index.html` contains — an 8-beat walkthrough

Built as a "presenter mode" page: click through beats via numbered buttons, arrow
keys, or Prev/Next. A hidden "Notes" toggle (off by default — this matters, see
below) reveals presenter cues: the exact line to say, timing, and staging direction.

1. **One principle, two products** — bridges from a live demo of a different
   product (Aldor) into this pitch: "the client renders, it never decides."
2. **Four questions, one system** — the four role questions above, each with a
   "See it answered →" link that jumps straight to the beat that proves it.
3. **One app, two threads** — the full 9-stage lifecycle, click-through, each stage
   tagged by which surface handles it (Web / Mobile / Backend / Informal /
   Not specified). Includes a correction note: Gates run **PG0→PG5** (six levels,
   not five — PG0 still counts, at 25%), and Gates are only stage 3 of 9.
4. **What a CEO sees at 7:55am** — the one screen with *real* deck numbers (not
   invented): Target $50m, MAPV $47m, Forecast $44m, Delivered $31m, plus
   "Since last review" / "Needs your action" sections.
5. **One dataset. Four lenses.** — the role switcher (CEO / CFO / Owner / Finance
   tabs). Ends with a "never shown here" strip (manual ratings, raw ledger rows,
   etc.) that's identical across all four roles — proof the simplicity is
   deliberate, not accidental.
6. **Four clicks deep. Still know where you are.** — a breadcrumb drill-down demo
   (Portfolio → Exception → Initiative → Evidence) proving context never resets.
7. **What never moves** — plants the immutability distinction (Delivery/Forecast
   change constantly; Commitment/Gate history never do, once locked) without
   explaining the mechanism — that's deliberately left to someone else's section
   of the real presentation.
8. **Close** — the deck's own tagline: "Sophisticated underneath. Simple on
   screen."

Below the 8 beats: a "Don't say" guardrail box (always visible), and a collapsible
**Appendix** with scope ownership, the full lifecycle explorer, and a web-vs-mobile
work-split table.

## What's real vs. invented — read this before changing numbers

This is the single most important thing to preserve in any future edit.

- **Beat 4 (CEO screen) numbers are real**, copied from the deck's own mockup:
  Target $50m, MAPV $47m (94% coverage, $3m gap), Forecast $44m, Delivered $31m,
  and the "Since last review" / "Needs your action" bullet lists.
- **CFO / Owner / Finance screen numbers (Beat 5) are invented** — the deck only
  gives the *field names* for these three screens (no mockup, unlike the CEO
  one). They are tagged "illustrative" on the page itself for this reason.
- The invented numbers are **not arbitrary** — they were deliberately built to all
  correlate through one example: a **"Supply Chain Consolidation" initiative with
  a $3m challenged value**, which is the same $3m as the CEO screen's MAPV gap
  and "Supply Chain $3m gap" action item. The thread runs:
  - CEO: MAPV gap = $3m, VaR banner names "Supply Chain $3m gap"
  - CFO: Challenged value = $3.0m; Forecast($44m) − Original Commitment($41m) = $3m
    (i.e. the entire forecast-vs-commitment gap *is* this one disputed item)
  - Owner: "Submit Gate evidence for 'Supply Chain Consolidation' ($3m) — due in
    3 days"
  - Finance: "Validate 'Supply Chain Consolidation' evidence — $3m challenged"
  - Drill-down beat (6): the example path is Portfolio → "Supply Chain $3m gap" →
    "Supply Chain Consolidation" → Evidence — same thread again.
  - The CFO pipeline (Delivered $31m → Validated $27m → Banked $6.5m) is
    strictly decreasing on purpose, echoing the same "fewer dollars clear a
    stricter bar" pattern as the real CEO funnel.
  - **If you change any one of these numbers, update the others so the thread
    still holds.** Don't reintroduce unrelated placeholder numbers (an earlier
    version had a disconnected "$620k Regional Rollout" example — removed
    deliberately for this reason).
- Who actually raises a "challenge" in the first place (vs. who resolves it) is
  **not specified in the deck** — Scenario 2 (slide 19) describes the resolution
  (Owner resubmits evidence, Finance runs an "enhanced re-assurance review") but
  never states who flags it initially. Don't assert an answer to this if asked;
  say it's an open gap.

## Known past bugs, already fixed — don't reintroduce them

1. **Beats 4 and 5 showed the CEO screen two different, inconsistent ways.** Beat
   4 originally had a single collapsed "Value at Risk" banner that silently
   dropped the "Since Last Review" section entirely; Beat 5's CEO tab had the full
   two-section version. Fixed by making Beat 4 match Beat 5 exactly (both now show
   "Since last review" + "Needs your action" as two separate boxes).
2. **CSS specificity bug in the mobile responsive rules.** A mobile override
   `.harrow{ width:36px; }` had *lower* specificity than the base rule
   `.handoff .harrow{ width:100px; }`, so it silently never applied — the arrow
   stayed full-width on phones regardless of the media query. Fixed by matching
   the selector exactly (`.handoff .harrow` in both places). **General lesson for
   this file: any mobile override must repeat the full selector chain of the rule
   it's overriding, not a shorter one** — CSS specificity doesn't care about
   media-query order.
3. **The old `pending_ended`-style placeholder tags** ("placeholder structure" in
   orange, "from slide 11" in green) were replaced with a single quiet
   "illustrative" tag — the originals read as backstage/meta text if the page is
   screen-shared live to an audience. See "Audience-safe by design" below.

## Audience-safe by design — don't undo this

This page is meant to be screen-shared live to Praxis stakeholders, not just used
privately. Everything coaching-related is deliberately hidden by default:
- The **"Notes" toggle** (top-right, off by default) gates all presenter cues —
  exact spoken lines, timing, staging direction, the "Don't say" box, the
  appendix footer disclaimer. CSS: `.presenter-note{ display:none; }` /
  `.wrap.notes-on .presenter-note{ display:block; }`.
- Headlines and subheads on each beat read like actual product copy ("One
  dataset. Four lenses.") not like stage directions ("Switch roles live, say
  X"). Keep new beats consistent with this — don't put instructional text in the
  always-visible headline/subhead.

## Responsive

Breakpoints at `640px` and `380px`. Respects `prefers-reduced-motion` throughout
(all entrance animations have a reduced-motion fallback that just shows the final
state with no transition). `overflow-x:hidden` on `html,body` as a safety net.

## Open items / what's not done yet

- **GitHub Pages is not yet confirmed live.** Needs: repo → Settings → Pages →
  Deploy from branch → `main` / root.
- The real Praxis prototype ("v1.2", referenced on slide 11 of the deck) has not
  been reviewed — this whole page is reconstructed from the pitch deck only, not
  from that prototype or from SIGNAL's actual codebase (which doesn't exist yet).
- No Sponsor HOME screen exists anywhere in the deck (slide 12 lists only CEO,
  CFO, Owner, Finance) even though slide 3 lists Sponsor as one of four roles
  with a question. This is flagged honestly in Beat 2's Sponsor card rather than
  invented — keep it that way.
- The Aldor artifact (companion, Section B material) has not been added to this
  repo or given the same responsive/audience-safe treatment as this one.

## If you're an AI agent picking this up

1. Read this file fully before changing anything.
2. If asked to change a number on Beats 4 or 5, re-check the "Supply Chain $3m"
   thread above and update every screen it touches, not just one.
3. Edit `index.html` directly (no build step). If a parallel Claude Artifact copy
   is mentioned by the user, ask whether they want it kept in sync — there's no
   automatic sync between the two.
4. Preserve the Notes-toggle-hidden pattern for anything presenter/coaching-only.
5. Git identity on this machine is already configured (`Chibuzor`,
   `chibuzormekalam@gmail.com`); remote is `https://github.com/ZOEYTECH1/signal.git`
   on branch `main`. Push access required the `CHIBUZOR-coder` GitHub account to
   be added as a collaborator — already done once, should still hold.

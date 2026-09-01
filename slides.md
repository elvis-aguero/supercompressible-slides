---
theme: seriph
title: Supercompressible Metamaterial — Full Provenance
info: |
  A complete provenance record of every genuinely new idea tested across 23 closed
  agentic runs on the Bessa rocking-mast supercompressible metamaterial, in
  anti-chronological order (most recent run first). One slide per genuinely new idea
  — the first time it's tested with real data, you see its compression video — plus
  one summary slide per run.
class: text-center
transition: slide-left
mdc: true
---

<!--
============================================================================
DECK FORMAT CONTRACT (advisor-specified, agreed 2026-07-29; reorganized by
importance and de-staled 2026-08-30) — durable reference for any future
edit session. This comment is not a slide; it is not meant to render.
Read this before adding or editing any slide. Rules are numbered by how
fundamental they are, not by the date they were written.
============================================================================

1. ONE SLIDE PER GENUINELY NEW IDEA, NUMBERED D<n>. REVISITS OF THE SAME
   IDEA ARE D<n>-2, D<n>-3, ... — SAME SLIDE, MAJOR.MINOR VERSIONING.
   (Renumbering scheme adopted 2026-08-30, replacing the old separate
   `class: restudy-slide` category — see the migration note at the end of
   this rule for why.)

   A new BASE number (D<n>) is earned only by a genuinely new design idea
   that has never had a slide before. A follow-up test of that SAME idea
   — a wider search, a bug fix, a contact migration, a different position
   for the same mechanism — is not a new idea; it is `D<n>-2` (or `-3`,
   `-4`, ...: count up from the base idea = implicit "-1"). Think
   major.minor versioning: the major number is the mechanism, the minor
   number is which pass at testing it this is.

   TITLE FORMAT: every idea-slide's title — base or revisit — is `D<n>`
   (or `D<n>-<k>`) followed by ` &middot; ` and a real qualifier: the
   design's own name for a base idea ("D42 &middot; Serpentine (wavy
   in-plane) longeron"), and what changed THIS pass for a revisit ("D24-3
   &middot; Mid-span placement, not near the joint"). A bare `D<n>-<k>`
   with no qualifier tells a reader nothing without opening the slide —
   the number alone is not what makes the scheme navigable.

   A revisit slide is a FULL idea-slide (rule 2's template, `class:
   idea-slide`, all linting rules apply) — not a lighter format. It uses
   the SAME 4 bullets (What/Origin/Stats/Verdict); Origin becomes "what
   prompted THIS revisit" (a contract change, a new infra capability, a
   consistency check) rather than re-explaining the base mechanism, which
   already has its own D<n> slide to point back to. If a revisit's own
   Stats funnel is thin (one validation point, one imperfection sweep),
   report it honestly at that size — n=1 is a valid Stats line, not a
   reason to skip the format.

   H1-AS-ORACLE-WIRING-CHECK IS EXCLUDED FROM THE DECK, ENTIRELY, ALWAYS.
   Several runs' H1 is not a design hypothesis at all — it is the run's
   one-time oracle-wiring sanity check. That kind of H1 gets no slide,
   ever. (This does NOT mean every hypothesis literally numbered "H1" is
   excluded — plenty of runs' H1 is a real, substantive design test.)

   MIGRATION NOTE (2026-08-30): before this date, a revisit got `class:
   restudy-slide` and a lighter 3-bullet format (What changed/What was
   tested/Result), titled "D<n> revisited". That class is retired — full
   migration completed 2026-08-30 (see git log for the commit), every
   revisit in this deck now carries a real D<n>-<k> number and the full
   4-bullet template. One deliberate simplification made during that
   migration: where a single slide covered thin, incidental revisits of
   several different base ideas at once (one design each, "enough to
   verify a code path, not a family"), the whole slide was folded into
   the numbering of whichever idea it was substantively about, rather
   than split into several near-empty slides — a judgment call, not a
   rule, apply the same way only when a genuine split would produce
   slides with nothing real to say.

2. THE 4-BULLET TEMPLATE (exactly 4 bullets, left column of a two-column
   layout — no more prose on the main slide, for every idea-slide
   including every D<n>-<k> revisit):
     (a) What      — precisely what was tried, in plain physical terms:
                      what changed about the design, what stayed the
                      same. Free/fixed parameter bounds live ONLY in the
                      speaker notes' Input space (rule 9), never
                      duplicated here.
     (b) Origin    — where the idea came from, AND the PHYSICAL MECHANISM
                      that motivates it: why, mechanistically, would this
                      help the mast coil further, absorb more
                      compression, or raise its stiffness? A citation is
                      supporting evidence for that mechanism, not a
                      substitute for stating it — "Rathore & Grason 2011"
                      alone names a source, not a reason; "Rathore &
                      Grason 2011 — a crosslinked bundle carries an
                      intrinsic torque a single member doesn't, because
                      the crosslinks resist relative bending/twisting
                      between sub-beams" states the mechanism the
                      citation backs. Use a real, specific citation, or
                      the honest "common sense / resize of family X" if
                      that's actually what it was — never fabricate a
                      literature grounding that isn't real. If a real
                      citation is claimed, add a numbered footnote below
                      the bullets with the actual reference; if only a
                      named theory/author was cited without a delegation
                      verifying a specific paper, the footnote must say
                      so plainly rather than invent a fake
                      author/year/journal. For a D<n>-<k> revisit, Origin
                      is what prompted THIS pass (a fix, a contract
                      change, a new capability) — the base mechanism
                      lives on D<n>'s own slide.
     (c) Stats     — a FIXED-FORMAT structured data line, not free prose
                      (a deliberate, scoped exception to the
                      plain-language bar below — this is a data readout
                      meant to be read as numbers; mechanistic reasoning
                      about WHY still belongs in the Verdict bullet).
                      Exactly this shape:

                        n=<N> → <C> coil → <R> riks → <G> good (<X>× Bessa)
                        p50/p90/p100 — σ_crit: a/b/c · mcs: d/e/f · mls: g/h/i

                      Funnel line: N = total designs evaluated; C = number
                      that passed the coilability gate (Stage 1); R =
                      number with a CONVERGED Riks solve (Stage 2 actually
                      completed — a non-converged salvage read does not
                      count toward R, even when its own measured quantity
                      is trustworthy under rule 2b below); G = number that
                      passed EVERY feasibility criterion. The Bessa
                      multiplier attaches ONLY to G — if G=0, omit it
                      entirely ("0 good", nothing to compare). Always
                      normalize against the fixed Bessa point (0.1306
                      kPa), NEVER a per-campaign "target" or the current
                      incumbent record — Bessa is the one constant every
                      slide in this deck can be compared against
                      directly, and the incumbent changes every time a
                      run closes.

                      Quartile line: p50/p90/p100 (median, 90th
                      percentile, max) for σ_crit, mcs, and mls, ALL THREE
                      computed over the SAME population — the R
                      (Riks-converged) design set, never a different
                      population per metric.

                      R=0 CASE: when no design reached a converged Riks
                      solve, state instead, on the same line:
                        quartiles unavailable — <one-clause reason>
                      This exact lead-in phrase, always.

                      Best-good line: the actual best GOOD (feasible)
                      design's inputs and outputs, e.g. "best good:
                      a=.00774 b=.01417 pitch=.68 top_d=.044 → σ=.2712
                      mcs=.99 mls=.017" (same `ratio_`-stripping
                      compaction as Input space, 5-var cap with "+N more"
                      beyond that — this line stays on the visible,
                      canvas-budgeted slide). If G=0: "best good: none
                      (0/N passed every criterion)".

                      CLEARED line — APPROVAL, NOT RANKING. The objective
                      is a conjunction of two THRESHOLDS (σ_peak ≥ 2×
                      Bessa = 0.2244 kPa AND a novel mechanism), so the
                      question an idea answers is "did it clear?", not
                      "where did it place?":

                        cleared: <K> of <R> decided ≥ 2× Bessa (0.2244)
                                 · novel: yes | no <one-clause reason>

                      If K=0: "cleared: none". If the designs that
                      cleared are duplicates of the family's own control,
                      say so — a family whose only clearing member is its
                      control has not been tested. Keep the "(X× Bessa)"
                      multiplier on the best-good line — it's
                      informative — but the DECISION is the threshold,
                      never a comparison against the current incumbent
                      (which converts passes into apparent failures as
                      the incumbent drifts).

                      Idea-specific findings that don't fit this shape (a
                      correlation, a surrogate-adequacy R², a mechanistic
                      aside) may follow the funnel+quartile line as
                      additional free text in the SAME bullet — the fixed
                      format is a floor, not a ceiling.
     (d) Verdict   — a FIXED-FORMAT status line, then 1-3 sentences of
                      causal reason, plain language. Two independent axes,
                      always in this order:

                        <STATUS>[ (RETRACTED|DISQUALIFIED|SUPERSEDED)] · <PRACTICAL>
                        <causal reason>

                      or, for D24-D43-and-later slides using the newer
                      taxonomy:

                        <CAMPAIGN> · <IDEA> · <SCOPE>
                        <causal reason>

                      STATUS: exactly one of SUPPORTED / FALSIFIED /
                      INCONCLUSIVE — the Popperian charter's own
                      vocabulary, non-negotiable, always the first word.
                      Optional flag: (RETRACTED) when evidence that once
                      supported this verdict was later found wrong (the
                      original verdict stood correctly at the time);
                      (DISQUALIFIED) when the evidence still stands but
                      doesn't count per the apples-to-apples/novelty
                      contract; (SUPERSEDED) when the evidence was right
                      AND counted at the time, but the contract itself
                      has since changed in a way that could alter the
                      conclusion ("re-test me", not "I was wrong"). Never
                      more than one flag.

                      PRACTICAL: exactly one of WORKS / DEAD-END / WEAK /
                      MIXED / UNTESTABLE — the CURRENT, FINAL answer to
                      "does this actually help build a real printable
                      supercompressible mast", independent of STATUS. A
                      (RETRACTED) or (DISQUALIFIED) verdict is ALWAYS
                      practically DEAD-END, full stop, regardless of the
                      raw figure.
                        WORKS      — mechanism is real, helps, no
                                     disqualifying flag.
                        DEAD-END   — mechanism doesn't help, actively
                                     hurts, or the disqualifying flag
                                     above applies.
                        WEAK       — mechanism is real but the effect is
                                     far below the target.
                        MIXED      — inconsistent across designs, no
                                     reliable predictive pattern.
                        UNTESTABLE — the registered hypothesis was never
                                     validly put to a test at all.

                      CAMPAIGN (D24-and-later taxonomy): did the search
                      actually reach the mechanism with trustworthy
                      numerics? One of POWERED (real n, right regime,
                      trustworthy — unmarked/implicit when clearly true)
                      / UNDERPOWERED (real data, but n too small or short
                      of the discriminating regime) / BLOCKED (a
                      solver/numerical wall, or the mechanism never
                      engaged, prevented a fair test) / ARTIFACT (what
                      was measured is now known contaminated by a
                      specific bug, pending re-solve).

                      IDEA: given everything now known, what should a
                      future agent DO about this mechanism? One of
                      VALIDATED (real, trust it, build on it) / REFUTED
                      (tested with real power, the physical direction
                      argues against it) / FERTILE-PARAMETRIC (this point
                      failed, untried territory in the SAME design space
                      might not) / FERTILE-REWORK (the theme is sound,
                      this embodiment is the wrong vehicle — build a
                      different realization) / UNKNOWN-NO-EVIDENCE (the
                      campaign never actually produced information about
                      the mechanism itself). Exactly ONE IDEA value per
                      slide — if a slide seems to need two, split it
                      (rule 1).

                      SCOPE: a short noun phrase naming EXACTLY which
                      claim IDEA is judging — never the whole family
                      name. "ring-radius growth", not "compliant rings".

                      Reason line(s): causal explanation only — WHY the
                      mechanism did or didn't work, not a restatement of
                      the status, and not a repeat of the Stats bullet's
                      own numbers.

                      APPEND-ONLY: never edit an old verdict's STATUS or
                      words to match new evidence or a new contract — the
                      record is append-only, because a verdict was a
                      correct call under the rules/evidence of its own
                      time and rewriting it destroys the audit trail
                      future readers depend on. New evidence earns a new
                      D<n>-<k> slide (rule 1), whose Origin names what
                      prompted it. Reformatting an existing slide's
                      STRUCTURE (e.g. migrating an old free-form restudy
                      into this template) is allowed and does not violate
                      append-only, provided no number and no conclusion
                      changes — the policy protects a verdict's WORDS,
                      not the container carrying them.

                      D24-D43-and-later slides use CAMPAIGN·IDEA·SCOPE.
                      Older slides keep STATUS·PRACTICAL until someone
                      has reason to re-derive them individually — never
                      mass-convert on a find/replace, since CAMPAIGN and
                      IDEA require actually re-checking what was tested.

2a. ABLATION / CONTROL FAIRNESS (added 2026-08-30, after a real miss this
    same session). When a slide claims a mechanism "is responsible for"
    a reading via a with/without comparison, the ablated/control
    baseline MUST be a minimal, non-cherry-picked reference — never this
    study's own best-known incumbent design, chosen for reasons unrelated
    to the mechanism under test. A design that reads "with insert: X, without
    insert: Y, therefore the insert does/doesn't matter" is only a fair
    test if "without insert" is a plain, unremarkable version of the
    host — not the single best design the whole study has ever found. If
    a literal "start from the study's actual reference baseline (e.g.
    circular Bessa) + this mechanism" comparison isn't buildable at all —
    for instance because the mechanism structurally requires a cross-
    section family the reference baseline doesn't use — that must be
    stated plainly in the slide's own notes, not silently sidestepped by
    comparing against whatever already-optimized design the mechanism
    happened to be grafted onto. See D24-3's own Verdict/notes for the
    worked example this rule is grounded in.

2b. NOVELTY, TWO KINDS (added 2026-08-30). The Stats bullet's `novel:`
    field and the Verdict's SCOPE must distinguish which kind of novel is
    being claimed, whenever the distinction matters:
      MECHANISM NOVELTY  — a genuinely new physical principle, never
                            applied to this rocking-mast problem before.
                            This is the strong bar PROBLEM_STATEMENT.md's
                            "Challenge" section actually asks for.
      POSITIONAL/PARAMETRIC NOVELTY — an already-tried mechanism,
                            relocated, retuned, or re-combined (e.g. the
                            same bistable insert moved from near a ring
                            joint to mid-span). Real, useful, evidenced —
                            but it does NOT by itself satisfy the strong
                            novelty bar, and a slide must say so rather
                            than let a positional finding read as if it
                            were a new mechanism. If a future agent could
                            reasonably ask "haven't we already tried this
                            mechanism?", the honest answer belongs on the
                            slide, not just in the notes.

2c-VIS. RIGHT-COLUMN MEDIA (codified 2026-08-30; this rule existed as an
        idea but was never written down before this date — the gap let a
        real requirement get skipped twice in one session before it was
        caught, and is now also enforced by `lint_slides.py`, see below).

        A compression video is REQUIRED, not optional, for the first
        slide reporting a genuinely new idea or ANY D<n>-<k> revisit,
        whenever the design underwent real, visible deformation. The
        ONLY valid exception is a design whose own real deformation is
        visually indistinguishable from undeformed (e.g. failure at ~3%
        compression) — and that exception must be STATED, not silently
        defaulted to, in the same visual slot the video would occupy.
        "No render yet, ask if you want one built" is NEVER an
        acceptable substitute: if a real solved ODB exists, render it.

        A real sigma-vs-compression chart (`*_mini.png`) is REQUIRED
        alongside the video whenever a chart would show something the
        caption can't — most commonly a two-design comparison
        (with/without a mechanism, before/after a fix, genuine/ambiguous)
        or a stress history the reader would otherwise have to take on
        faith from the Stats numbers alone.

        BUILD EVERY CHART WITH `bo/mini_chart.py` — NEVER A FRESH ONE-OFF
        SCRIPT (rule tightened 2026-08-31, after the one-off-script pattern
        this replaces produced two real, shipped bugs in a single day: an
        aspect ratio that drifted from the deck's own convention, and a
        transparent background that was illegible in the wild — both
        structurally impossible once the convention lives in one tested,
        committed function instead of being re-derived from memory on
        every call). Its own docstring is the authoritative, VERIFIED
        description of the convention (checked directly against a real
        established chart's own source data 2026-08-31, after the
        previously-written description here — "encoding each point's own
        sigma magnitude" — turned out to be wrong):

          x-axis: mcs, the FULL UNWINDOWED history — never truncated at
                  the feasibility window, set dynamically from the data's
                  own max, never hardcoded.
          y-axis: sigma, in MULTIPLES OF THE BESSA POINT (never raw kPa),
                  ALWAYS LINEAR — never log-scale, for any reason,
                  including a dominant artifact spike (standing
                  instruction, 2026-08-31 — do not re-derive this).
          color:  GREY MEANS "PAST THE CAP" (corrected twice, 2026-08-31 —
                  first tried grey-for-low-strain/red-for-high, then a
                  separate blue plus a vertical crossing-line for
                  past-cap; both rejected). For mls in [0, 0.02] — the
                  range where pass/fail is still being decided — color is
                  a real, NEVER-GREY red gradient (light red at 0% strain
                  to dark red at 2%), normalized to that fixed range so
                  "how red" is comparable design to design. Past 2% the
                  curve turns flat GREY, like a UI element greying out
                  once disabled — the exact strain value no longer
                  matters once the design has already failed this
                  criterion. No second annotation, no vertical line: the
                  grey IS the signal.
          style:  solid = primary design; dashed = optional comparison.

        EVERY CHART BAKES IN AN OPAQUE WHITE BACKGROUND (matplotlib default
        `savefig(transparent=False)`, baked into `bo/mini_chart.py` itself
        now) — a transparent background only reads correctly against a
        pure-white page and goes illegible wherever the viewer's theme or
        the mirror's own background isn't (caught 2026-08-31: three
        mini-charts shipped transparent and were unreadable in the wild).
        `lint_slides.py` BLOCKS a referenced `.png` whose corners aren't
        fully opaque.

        `lint_slides.py` WARNS (does not block) when an idea-slide's
        right column has no `<img>` reference to a `.gif`/`.png` at all —
        this catches an entirely missing media slot mechanically, though
        it cannot judge whether a chart is needed for a given slide's
        own comparison; that judgment stays a review-time call.

        CAPTIONS UNDER A GIF/CHART SHOULD BARELY BE USED — special cases
        only, never a place to relocate real analysis prose that belongs
        in the speaker notes. `lint_slides.py` WARNS when a caption runs
        past 10 words; move whatever isn't essential to orient the reader
        at a glance into the notes instead of growing the caption.

3. THE PLAIN-LANGUAGE BAR (applies to all 4 bullets): no unexplained
   jargon in the visible slide body. A bare "ρ" or "r", an unglossed
   "magnitude ratio", or a made-up proper noun for a parameter sub-range
   does not belong on the slide face — a reader with no solid-mechanics
   or statistics background must parse every bullet without asking "what
   does that mean?". Two ways to satisfy this: (1) speak in
   physical/outcome terms instead of the underlying statistic — this is
   preferred; or (2) if a technical term is unavoidable on-slide, define
   it in the same clause the first time it appears. Reserve ρ/r/p-values
   for speaker notes. Everything else — reasoning, caveats, provenance
   history, full parameter dumps, technical asides — MUST go in the
   slide's Slidev speaker notes (an HTML comment immediately after the
   slide content, before the next `---`), never in the slide body. (Do
   not write that comment's own open/close delimiters literally inside
   THIS contract comment — a literal closing sequence anywhere in this
   text terminates the contract comment itself early.)

   CHARACTER BUDGET, measured not guessed: this deck's canvas is
   980x552px. Rendered headlessly at `layout: two-cols-header` + a
   `text-sm leading-snug` wrapper, the left column has 416px of usable
   height below the header, at a measured line-height of 25.2px -> a
   hard ceiling of ~16.5 lines total across all 4 bullets (content
   taller than this clips silently — Slidev does not fit content to the
   frame). Measured wrap rate is ~62 characters/line in the ~419px-wide
   left column. Target ~14-15 lines total => a working budget of ~190
   characters PER BULLET, INCLUDING the bold label. This is a target,
   not a license — distribute the ~14-15 line total across the 4 bullets
   by how much each one actually needs, and cut real content into
   speaker notes rather than let any slide clip. Re-verify after edits:
   the only trustworthy check is rendering the built deck and measuring
   `scrollHeight` vs the 552px canvas (`assets/_m6.mjs`) — reading the
   markdown is not sufficient, wrapping depends on real font metrics.

4. GIF REQUIREMENT: NATIVE ABAQUS/CAE VIEWER EXPORT ONLY.
   The right half of the two-column layout is one image or GIF exported
   NATIVELY from Abaqus/CAE's own Viewer/visualization module — never
   the matplotlib/COORD-field-reconstruction pipeline used elsewhere in
   this repo. The point is source truth directly from the simulation
   tool, with no custom re-derivation of geometry between the ODB and
   the image. The renderer lives at presentation/render/render_odb.py.
   Known gotchas, solved once and documented here so nobody has to
   rediscover them a third time:
     1. `vp.setValues(displayedObject=odb)` raises "TypeError:
        displayedObject; found Odb, expecting StubType" unless
        `from viewerModules import *` is imported first.
     2. This study's rings have NO solid geometry — each is a 0-D
        reference point — and `ANALYTICAL_SURF` is an oversized,
        idealized rigid plane for the Riks BC, not physical ring
        geometry; left visible it fills the frame. Fix: restrict the
        display group to the structural (beam-element) instance via
        `displayGroupOdbToolset.LeafFromPartInstance`. If a future ODB
        genuinely has no faithful way to show ring position, say so in
        the speaker notes rather than fabricate ring geometry.
     3. `renderStyle=FEATURE` is not a valid Abaqus constant — use
        `SHADED`.
     4. B31 beam elements render as bare centerline wireframe unless
        `vp.odbDisplay.basicOptions.setValues(renderBeamProfiles=ON)` is
        set (`basicOptions`, not `commonOptions`).
     5. Colour by a physically meaningful field, not an unexplained
        default — contour on `E11` where it exists
        (`setPrimaryVariable(variableLabel='E', outputPosition=
        INTEGRATION_POINT, refinement=(COMPONENT, 'E11'))`), legend ON.
        Probe the ODB's own fieldOutputs and fall back to `LE11` when
        `E` doesn't exist (shells, pin-jointed trusses) — never hardcode
        by element type. If colour carries no data meaning, turn it off
        entirely.
     6. Camera: the generic `session.views['Iso']` preset does not
        reliably give a usable angle for this mast geometry. Compute an
        explicit camera from the structural instance's own bounding box
        (elev=22°, azim=-50°, z-up, parallel projection), held fixed
        across all frames (fit once on frame 0) so any visible rotation
        is the structure's own real coiling motion.
     7. Legend placement/size: move it clear of the geometry
        (`viewportAnnotationOptions.setValues(legendPosition=(x, y))`,
        percent of viewport, tuned per canvas aspect) and shrink it to
        fit (`numIntervals=6`, smaller `legendFont`,
        `legendNumberFormat=SCIENTIFIC`, `legendDecimalPlaces=2`). A
        `setValues()` call not raising is not proof the pixels moved —
        always re-render and LOOK at the PNG after any legend/camera
        tweak.
     8. Portrait canvas (~2:3, e.g. 600x900) for the default layout;
        LANDSCAPE mode (design-left, legend-right, 900x600) is the
        newer, preferred layout for designs wider than they are tall —
        set the viewport's own `width`/`height` BEFORE `fitView()`, and
        after `fitView()`, project the design's own full-animation
        bounding box through the fitted camera basis and zoom out if the
        design's real screen-space half-width would leave less margin
        than the legend's own share of the canvas needs (a fixed-
        geometry family this was tuned against will get a no-op; a
        wider family gets the margin it needs).
     9. Ring annotation: draw a schematic circle through each ring's
        joint nodes' CURRENT positions (read from `fieldOutputs['COORD']`
        INSIDE the per-frame loop, never from a node/mesh attribute read
        once outside it — `node.coordinates` is always the UNDEFORMED
        position). Draw entirely OUTSIDE Abaqus in a PIL post-process
        pass, as a thin dashed, semi-transparent, neutral-gray circle —
        visually nothing like the solid shaded/strain-colored beam
        profiles, never mixed into the ODB's own displayGroup, no
        in-image text label (the styling itself is the signal). Recompute
        from field-output data every single frame, for ANY animated
        overlay that isn't Abaqus's own native per-frame render — never
        assume which ring (if either) is fixed; check via COORD.
   No-winner convention: always show a faithful native-Abaqus image of a
   TYPICAL (not necessarily the single best) design from that idea's
   search — never leave an empty image slot for a negative result. This
   applies to the GIF ONLY (added 2026-09-01, after a real, repeated miss:
   several `mini_chart.py` charts silently plotted a "typical" population
   member instead of the specific design the Stats bullet's own "best
   good" line describes, producing a chart peak that flatly contradicts
   the visible text with no disclosure anywhere on the slide). A
   stress-history chart's whole job is to illustrate a claim already made
   in words — it MUST chart the specific named design(s) the slide's own
   text discusses (the best-good design, or an explicit comparison pair),
   never a generic "representative" substitute. If the actual best-good
   design's own raw solve no longer exists to chart, say so directly in
   the caption or Deferred — do not silently substitute a different
   design's curve.

5. PROVENANCE (five rules, all non-negotiable once physics/metric change):
   (a) ONE PROVENANCE PER SLIDE. Every number on a slide and its gif must
       come from the SAME oracle version. Never pair a re-rendered gif
       with numbers from a different oracle era, or new numbers with an
       old gif. Re-render only as part of a full re-test of that design
       (which earns its own D<n>-<k> slide, rule 1).
   (b) EVERY GIF TRACES TO AN ARCHIVED ODB (under `data/idea_odbs/<id>/`
       when applicable, or a scratch path named in the slide's own
       notes), whose provenance records the exact inputs and solve
       recipe. A gif with no traceable ODB behind it does not belong in
       the deck.
   (c) EVERY NUMBER TRACES TO A RUN AND A DELEGATION, named in the
       slide's speaker notes (Timeline, rule 9) — e.g. "D002 of run
       20260830T004106".
   (d) CONTRACT CHANGES NEVER REWRITE AN EXISTING SLIDE'S DATA. Not its
       numbers, not its gif, not its verdict. A re-test earns a new
       D<n>-<k> slide; the old slide keeps everything it had.
   (e) A CROSS-CUTTING CAVEAT IS STATED ONCE, on the "How the rules
       changed" slide — never repeated in every affected caption, which
       is how such a caveat rots out of date.

6. SUMMARY-SLIDE REQUIREMENTS. One summary slide per closed run, no
   exceptions — this is stated as plainly as rule 1 in the deck's own
   `info:` header and is not something that needs a separate request
   before being written; it comes with every run's idea/revisit slides,
   same commit.
     - Every hypothesis row's `Idea` column names the real D<n> or
       D<n>-<k> slide(s) that row produced, or a bare dash for a
       whole-design-space claim with no slide of its own. A `D<n>` with
       no matching `# D<n>` slide anywhere is a BLOCKING lint error (a
       dangling pointer); a cell carrying prose instead of a real
       pointer is a warning — the prose case is the one that actually
       happened once (a falsified family's summary row said "archived"
       and the family became invisible to the next reader). One slide
       per genuinely new idea REGARDLESS OF VERDICT.
     - Every run summary states real USD cost. It is the only number
       that makes "was this run worth it" answerable. This is NOT
       simply telemetry's total — the strategizer's own spend is often
       missing from `summary.json` (its persistent adapter doesn't
       always report usage) and must be recovered from
       `debug/transcripts/strategizer/*.jsonl` and added back by hand.

7. ORDERING: anti-chronological across runs (most recent run first).
   WITHIN a run: the run-summary slide comes FIRST, then that run's own
   idea/revisit slide(s) immediately after it. Any speaker-note text
   that says "see the idea slide above" from a run-summary slide is
   WRONG under this ordering; it must say "below".

8. LAYOUT DIRECTIVE: `layout: two-cols-header`, NOT `layout: two-cols`.
   Under plain `two-cols`, the `# Title` line lives inside the split and
   only spans the LEFT column's half-width. `two-cols-header` gives the
   title its own full-width row above the split; the body below still
   needs explicit `::left::` then `::right::` markers. Wrap the left
   column's bullet list in `<div class="text-sm leading-snug">...</div>`
   — this is the font size the character budget (rule 3) is calibrated
   against; do not silently change it without re-measuring the budget.

9. SPEAKER-NOTES FORMAT — applies to every idea-slide, including every
   D<n>-<k> revisit. Exactly these five labels, bold Markdown
   (`**Label:**`), one per paragraph, in this order when more than one
   is present — all optional except Input space and Seed:

     Input space — MANDATORY. The sole home for the free/fixed parameter
                    list with sampled bounds. One line per free
                    parameter:
                      <var>&isin;[lo,hi] — <physical meaning>
                    Meaning may be omitted for a self-explanatory name,
                    but the BOUNDS may never be. One trailing line for
                    fixed parameters. Uncapped — speaker notes carry no
                    canvas budget, list every free parameter.
     Seed         — MANDATORY. Always present:
                      FERTILE — <a perturbation that would count>
                      BARREN  — <why no perturbation can clear the bar>
                    FERTILE MUST NAME AN EXAMPLE PERTURBATION after a
                    literal em-dash (—, or `--` in source) — without one
                    it is an invitation, not a direction; the linter
                    checks for this literal character, not the HTML
                    entity `&mdash;`.
     Deferred     — caveats, judgment calls, or infra bugs found but NOT
                    resolved on this slide. Kept separate from Seed:
                    Seed answers "is this idea worth another shot",
                    Deferred answers "what's unresolved about THIS
                    analysis".
     Timeline     — one line per delegation, `D0XX: <one-clause
                    summary>`, even for a single delegation — this is
                    what satisfies rule 5(c). Do NOT restate the best
                    design's own numbers here — that duplicates the
                    Stats bullet's "best good:" line.
     Infra        — where the model actually gets built and solved: the
                    oracle module, the Stage-1/Stage-2 preprocessor
                    scripts, the fidelity-gate function and its
                    criteria, and the archived ODB/scratch source path
                    the slide's gif traces to (rule 5(b)).

   Linter: WARN only. A slide missing Seed warns; a slide with these
   labels out of order warns; nothing here blocks a commit.
============================================================================
-->

# Supercompressible Metamaterial
## Full provenance, in order

Every idea, every run, in the order it actually happened

<div class="text-sm opacity-70 mt-8">
A collection of ideas tried
</div>

---
layout: two-cols-header
class: baseline-slide
---

# The original baseline

::left::

<div class="text-sm leading-snug">

Every target in this deck is stated as a multiple of this design, everything else
is presented in anti-chronological history. We are looking for designs that achieve at least 80% maximum
compression strain (mcs), and at most 2% maximum local strain (mls).

- **Design:** circular longeron cross-section, 3 longerons, 1 storey. Circular top and bottom rings
- **Geometry:** ratio_d=0.02005, ratio_pitch=0.25, ratio_top_diameter=0.2505.
- **Result:** <u>&sigma;_peak=0.1122 kPa/longeron</u> (current metric; 0.1306 kPa in the retired
  eigenvalue metric &mdash; same solve, see notes), mls=0.0198, mcs &gt;= 0.8.

<div class="text-xs opacity-50 mt-2">
Verdict symbols used throughout: ✅ supported &middot; ❌ falsified &middot; ❔ inconclusive &middot; ⏳ pending (registered, not yet tested this run).
</div>

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/bessa_baseline_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Bessa point, re-solved 2026-07-31 for this deck.</div>
</div>

<!--
Re-solved 2026-07-31 via the exact same two-stage NO-CONTACT pipeline
test_nocontact_anchors.py uses for this anchor (energy-free StaticRiksStep -- "Riks" is the
arc-length method, the standard way Abaqus traces a structure's full force-vs-compression curve
through buckling and post-buckling, step by step, rather than just predicting where buckling
starts; supercompressible_lin_buckle_pretwist.py -> supercompressible_riks_pretwist.py),
specifically to render a native-Abaqus gif for this lead slide -- no ODB (Abaqus's output file
holding the full solved simulation) for this exact point existed in the permanent archive before
now. Solved sigma_crit=0.1306 kPa (the critical buckling stress -- the load per longeron at which
the structure first buckles, from a quick linear eigenvalue analysis, as distinct from sigma_peak,
the actual peak stress measured later from the full nonlinear Riks solve) (expected 0.1306, exact
match to 4 sig figs), mls=0.019795. ODB archived at
data/idea_odbs/bessa_baseline/ (PROVENANCE.txt has full inputs and the solve
recipe). See PROBLEM_STATEMENT.md lines 133-137 for the original definition of
this point and why it's the study's reference floor.

Deliberately NOT following the 4-bullet What/Origin/Stats/Verdict idea-slide
template -- this is not a hypothesis this study tested, it's an external
reference point, so there is no verdict to render. Per explicit user instruction:
describe the design and show the gif, no reasoning/justification needed.

Corrected 2026-08-26 (deck audit, item 1): this slide's headline read sigma_cr,nd=0.1306 kPa
unqualified -- the retired Stage-1 eigenvalue metric, per PROBLEM_STATEMENT.md's own text
("0.1122 kPa/longeron in the current sigma_peak metric (0.1306 kPa in the retired eigenvalue
metric)"). Every x-Bessa figure elsewhere in this deck is computed against 0.1122, so the deck's
own foundational reference slide was showing a number inconsistent with what it is the reference
FOR. Verified directly, not just from the PS's own prose: re-reduced the SAME archived ODB
(data/idea_odbs/bessa_baseline/results.pkl, no new solve needed) via the current windowed
sigma_peak methodology (peak of the real load-displacement response within the compression-cap
window) -- gives 0.112199 kPa, matching PROBLEM_STATEMENT.md's 0.1122 to the digit. No new solve
was run; this is the same 2026-07-31 ODB, read two ways.
-->

---
class: summary-slide
---

# Run `20260830T004106` — summary

<div class="text-sm leading-snug">

Bistability tested three ways: near the joint (D24), a chain of segments (new), a mid-span
insert (new). One reading passes every check but a thin one; the more novel chain remains
genuinely open, not a result yet.

</div>

<div class="text-xs leading-tight">

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | &ge;1 untried literature mechanism exists | &#10003; | Chained-arch pursued; 2 others need real shell physics | D44 &rarr; |
| H3 | Chained-arch fails energy-free | &#10003; | 71/72 non-convergent | D44 &rarr; |
| H4 | The validated chain point is imperfection-robust (no contact) | &#10007; | Only 3/8 feasible; 5/8 fail via ring-passthrough | D44 &rarr; |
| H5 | Contact fixes that failure | &#10003; | 8/8 feasible, 8/8 converged, with contact | D44 &rarr; |
| H6 | A wider search beats the current best reading | **&#8253;** | Found; genuineness untested by this hypothesis alone | D44 &rarr; |
| H7 | The chain's joint strain survives a real 3D check | &#10007; | Corrected strain 0.0381 &mdash; ~2&times; the ceiling | D44 &rarr; |
| H8 | A straight end-buffer reduces that strain | **&#8253;** | Reduces it, not conclusively below ceiling | D44 &rarr; |
| H9 | The buffer mitigation is a clean fix | &#10007; | Passes strain; reading itself is spike-suspicious | D44 &rarr; |
| H10 | A mid-span insert avoids the strain problem | &#10003; | Corrected strain 0.0198, under ceiling | D24 rev. &rarr; |
| H11 | That design is imperfection-robust | &#10003; | 6/8 (75%) feasible corrected &mdash; majority | D24 rev. &rarr; |
| H12 | Ring-flare rescues the chain's joint-strain failure | &#10003; | Corrected strain 0.0192, 4.1% margin | D44 &rarr; |
| H13 | That flare-rescued design is imperfection-robust | &#10003; | 5/8 (62.5%) feasible corrected | D44 &rarr; |
| H14 | That design's reading is genuine, not a spike | **&#8253;** | 22.8&ndash;27.9% sustained fraction &mdash; ambiguous | D44 &rarr; |
| H15 | D24's original design is genuine under the current oracle | **&#8253;** | 20.65% &mdash; indistinct from the chain's own ambiguous reading | D24 &rarr; |

</div>

<div class="text-sm leading-snug">

&nbsp;&middot;&nbsp; **74 delegations, 210 ledgered evals, ~11 h of 12 h**, GATED after 10 review rounds &nbsp;&middot;&nbsp; **Cost: $67.38**
</div>

<!--
H1 (excluded per rule 2): routine oracle-wiring reconfirm against run17_rectangle, SUPPORTED,
0.02% deviation.

CREDITED RESULT: mid_span_bistable (D24-3) -- a real, non-artifact reading, passes the
joint-strain check by a thin 0.8% margin, majority-robust. OPEN LEAD: chained_arch (D44) -- more
novel, higher raw numbers, validity genuinely unresolved after real effort (not disproven).

MECHANISM-ATTRIBUTION CORRECTION (added post-run, user-caught): this run's own notebook argued
the mid-span insert is "genuinely responsible for the capacity" by comparing it against the same
design with the insert shrunk to nothing. That ablation's own "without insert" baseline turns out
to BE run17_rectangle's own already-optimized geometry -- the single best design in this entire
study, chosen by search for reasons having nothing to do with bistability. Comparing against an
already-near-optimal design and finding no improvement doesn't show a mechanism isn't pulling its
weight; it shows it doesn't beat the best thing this study has ever found, which is a much weaker
and less interesting claim. See D24-3's own notes for the full correction and why a
literal "circular Bessa + bistability" comparison isn't available either.

GATE HISTORY (10 rounds, the most of any run to date). Early rounds (~002-004): the run initially
credited mid_span_bistable as clearing the novelty floor without directly re-testing D24 under
the current oracle for a fair comparison -- REJECTed until that comparison (H15) was actually
run. Later rounds (~005-009): REJECTed repeatedly on run-adequacy (PROBLEM_STATEMENT's
unconditional "exhaust the budget" clause) until the two named literature alternatives (Jiang
shell, Krankel/Wadee weave) were checked against the corpus and found to require real shell
physics this study's beam model can't approximate -- not a hand-wave, a demonstrated boundary.
call_010: PASS.

RETROSPECTIVE FLAGS: 15 of 46 delegations flagged (CONSISTENCY only). 5 ERROR_RETURN events this
run, all harness-level (stale revision hashes on concurrent notebook edits, one wrong cell name)
-- self-corrected via retry, not science bugs.

INFRA BUILT THIS RUN, NOT YET PROMOTED TO GOLD: bo/D44_oracle_chained_arch.py,
bo/D24_3_oracle_mid_span_bistable.py, scripts/supercompressible_lin_buckle_mid_span_bistable.py,
scripts/supercompressible_riks_chained_arch_contact.py,
scripts/supercompressible_riks_mid_span_bistable_contact.py, plus a modification to
scripts/supercompressible_lin_buckle_chained_arch.py. Promotion is the user's call.
-->

---
class: idea-slide
layout: two-cols-header
---

# D24-3 &middot; Mid-span placement, not near the joint

::left::
<div class="text-sm leading-snug">

- **What:** same single bistable insert as D24, moved to the longeron's MID-SPAN (flanked by
  plain segments) instead of against a ring joint — both joints now see ordinary geometry.
- **Origin:** isolates whether D24's benefit survives away from the joint, and (rule 2a)
  whether the insert itself, not just its host design, pulls its own weight.
- **Stats:** n=1 winning design + imperfection sweep + 1 ablation.<br>
  &sigma;<sub>peak</sub>=0.5838 kPa (2.6&times; target), joint-strain margin 0.8%, feasible
  6/8 draws. Ablation vs `run17_rectangle` (not minimal, rule 2a): insert-free reads HIGHER
  at every compression level (table in notes).<br>
  cleared: 1/1 &middot; novel: no — attribution unresolved.
- **Verdict:** POWERED &middot; UNKNOWN-NO-EVIDENCE &middot; insert's own contribution vs a
  minimal reference<br>
  Design is real and feasible, but its ablation compared against the study's own optimized
  incumbent, not a minimal host (rule 2a) — the insert-free baseline reads higher at every
  level. Whether the mechanism helps a minimal host remains untested. **Deeper gap: this
  oracle never checks for a genuine snap at all — see notes (verdict audit, 2026-08-31).**

</div>

::right::

<div class="flex flex-col gap-1" style="height: 440px">
  <div class="flex items-center justify-center" style="height: 150px">
    <img src="/gifs/D24-3_mid_span_bistable_mini.png" style="max-height: 150px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D24-3_mid_span_bistable_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center px-2">Insert (solid) vs ablated host (dashed) — host's
  early peak is a confirmed 2-frame artifact, not real capacity (see notes).</div>
</div>

<!--
**Chart correction (2026-08-31, rebuilt with `bo/mini_chart.py`):** now plots the full
unwindowed history (both curves reach mcs=1.0), colored by local strain (mls) per the
deck's corrected convention (rule 2c-VIS), not the old sigma-colored, window-truncated
version. Neither curve ever crosses the 2% strain cap (max 1.93%/1.98%), consistent with
the 0.8% joint-strain margin already cited above — neither curve ever turns the flat grey
the color scale reserves for "past 2%".

**Deeper gap (2026-08-31, verdict audit):** `bo/D24_3_oracle_mid_span_bistable.py` never computes
a genuine-snap diagnostic at all — checked directly, every "snap" reference in that file is
a comment assuming the mechanism, not a checked field (unlike `bo/D44_oracle_chained_arch.py`
and the D24/D24-2 oracles, which at least attempt `arch_snap_reversal`, even though it has
never once come back confirmed there either — see D24-2's Seed). This ablation compares two
designs without ever confirming either one actually snaps.

**Input space:** same design vector as D24's own base slide (mid-span adds no new free
parameter); this pass additionally sampled imperfection angle from Bessa's own
lognormal(4&deg;,1.2&deg;) distribution (D19, 8 draws) — not a design parameter.

**Seed:** FERTILE — the fair test this run didn't run: does a single bistable insert improve on
a MINIMAL, non-cherry-picked rectangular longeron of comparable dimensions (not specifically
`run17_rectangle`'s own search-optimized numbers)? A literal "circular Bessa + bistability"
comparison isn't available either — checked directly in `bo/D24_3_oracle_mid_span_bistable.py` and
`bo/D44_oracle_chained_arch.py`: both hardcode a solid RectangularProfile cross-section, because
the mechanism's own defining quantity (bistability_Q = rise/thickness) needs the same
directional, anisotropic bending stiffness a rectangular section gives and a round one doesn't
have in the same distinguishing sense. Nobody has built or tested a round-cross-section bistable
variant in this study. So rectangular is a necessary ingredient here, not a separable confound —
you can't fairly ask "is rectangular alone better" as if rectangular were removable. The real,
still-open question is whether this idea, realized in its minimal necessary form, does something
a comparably-sized plain rectangular beam doesn't — not whether it beats the single best design
this entire study has ever found.

**Mechanism-attribution correction, in full (user-caught, 2026-08-30):** the run's own notebook
compared the winning design (arch_rise_ratio=0.30, f_insert_length=0.30) against the same design
with `f_insert_length` shrunk to 0.02 (near-zero insert length, i.e. "no insert"). That ablated
design's other four dimensions (ratio_a=0.009213, ratio_b=0.033238, ratio_pitch=0.681277,
ratio_top_diameter=0.04444) are bit-for-bit `run17_rectangle`'s own confirmed-optimal geometry
(`bo/confirmed_anchors.json`) — the single best design in this whole study, found by a real
search for reasons unrelated to bistability. Pulling the actual per-frame stress-vs-compression
curves for both (not just the summary numbers) and comparing at matched compression levels:

| compression | with insert | without insert (=run17_rectangle) |
|---|---|---|
| 5% | 0.583 kPa | 0.608 kPa |
| 10% | 0.553 kPa | 0.590 kPa |
| 20% | 0.462 kPa | 0.507 kPa |
| 30% | 0.368 kPa | 0.426 kPa |
| 50% | 0.235 kPa | 0.276 kPa |
| 70% | 0.122 kPa | 0.164 kPa |

The plain, insert-free baseline reads HIGHER at every single compression level, not lower. The
run's own ablation check is still valid for what it actually tested — the with-insert design's
own reported peak (0.5838 kPa) is real, not a numerical spike; the ablated design's own headline
number (10.2 kPa) IS a spike (confirmed from the raw per-frame history: it appears for exactly 2
increments before crashing back to the same smooth curve as the with-insert design), and the
run's sustained-fraction check correctly caught that. But "the with-insert reading is trustworthy"
and "the insert is responsible for the capacity" are different claims, and only the first one is
actually supported by this comparison. The second remains untested.

**Timeline:** D17/D18 (this run, H10/H11): winning point + imperfection sweep + the (confounded)
ablation. D19: 8-draw robustness sweep. See D44's own slide for the chained-arch thread this
restudy was compared against (H15).

**Infra:** bo/D24_3_oracle_mid_span_bistable.py,
scripts/supercompressible_{lin_buckle,riks}_mid_span_bistable_contact.py (new this run, not yet
promoted to gold). Winning ODB:
/oscar/scratch/eaguerov/sc_oracle_mid_span_bistable/riks_c6a667fa1ab047128b4b6b1910fcf2b3/;
ablation ODB: riks_fcfc9c5f0a594aa6a9d42b8d99c7ef0c/ (same SCRATCH dir).
-->

---
layout: two-cols-header
class: idea-slide
---

# D44 &middot; Chained (multi-segment) bistable arch longeron

::left::

<div class="text-sm leading-snug">

- **What:** replace one longeron with N=2&ndash;6 genuinely bistable (Q=rise/thickness &ge;
  2.31) shallow-arch segments chained end-to-end, so the longeron snaps through several times in
  a controlled sequence as it compresses, instead of buckling smoothly like an ordinary beam.
- **Origin:** Correa, Seepersad &amp; Haberman (2015) &mdash; a chain of sequential
  negative-stiffness cells; a genuine connectivity change (a SEQUENCE of discrete snap-through
  events), not a single modified segment.
- **Stats:** n=182 &rarr; 129 coil &rarr; 99 riks &rarr; 0 good (clean)
  p50/p90/p100 &mdash; &sigma;_peak: 0.62/0.71/3.10 &middot; mcs: 0.63/0.95/0.95 &middot; mls:
  0.020/1.0/1.0
  cleared: unresolved (see Verdict) &middot; novel: yes &mdash; a genuine connectivity change
  best good: none confirmed both genuine and joint-safe at once (see Verdict)
- **Verdict:** POWERED &middot; FERTILE-PARAMETRIC &middot; joint-strain vs sustained-capacity
  trade-off<br>
  A real trade-off was mapped, not a dead end: flaring the rings + straightening the end
  segments passes joint-strain (4.1% margin) but its sustained-capacity reading is ambiguous
  (22.8&ndash;27.9%, unresolved even after a 250&times;-finer re-solve). More end-segment
  curvature at the same flare gives unambiguous genuine capacity (65.8%) but fails joint-strain
  by 11%. More flare made both worse. No point tested yet satisfies both.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 440px">
  <div class="flex items-center justify-center" style="height: 150px">
    <img src="/gifs/D44_chained_arch_mini.png" style="max-height: 150px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D44_chained_arch_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center px-2">D032 (solid) vs H12 (dashed).</div>
</div>

<!--
**Input space:** n_segments&isin;{2,...,6} &mdash; discrete chain length. arch_rise_ratio,
ratio_a, ratio_b, ratio_pitch, ratio_top_diameter &mdash; same physical meaning as every other
rectangular-cross-section family in this study. end_rise_scale&isin;[0,1] &mdash; how much the
TWO end segments (the ones framing directly into a ring joint) taper their own curvature down
from the interior segments' full bistable rise (1.0 = no taper, 0.0 = end segments fully
straightened). Fixed: young_modulus=3500 MPa, ratio_shear_modulus=0.3677, D1=100mm.

**Seed:** FERTILE — a proper 2D search over (end_rise_scale, ratio_top_diameter)
specifically in the region between D032 (genuine but joint-strain-fails) and H12's own point
(joint-strain-passes but ambiguous) is the concrete, well-defined next step. This is NOT a
mechanism restart &mdash; the FAMILY is confirmed capable of both a genuine sustained
&sigma; response and a joint-strain pass, just not (yet) both in the same design.
**Corrected 2026-08-31 (verdict audit):** "confirmed capable" here means a non-spike,
sustained stress reading — it does NOT mean the bistable snap-through mechanism itself is
confirmed to have engaged. Checked directly: `arch_snap_reversal` (the oracle's own
genuine-snap diagnostic) is unpopulated on 0 of 294 chained-arch solves ever run, D032 and
the D030 fine-grid re-solve included. The sibling D24 family ran this same check
repeatedly and never found a real snap in any properly-resolved solve either — a specific,
named reason to doubt "the mechanism is confirmed," not proof it fails.

**Deferred:** two other literature-grounded bistable mechanisms (Jiang et al. 2018 doubly-curved
shell; Krankel/Wadee woven column) were reviewed and NOT pursued &mdash; both require real
shell-element (S4R) physics this study's B31-beam infrastructure cannot faithfully approximate
(checked directly against the corpus's full text, not asserted). Building and validating new
shell infrastructure was out of this run's remaining budget.

**Timeline:**
- D002: literature review, 3 candidates identified.
- D003 (H3): chained-arch, energy-free, 71/72 non-convergent.
- D005 (H4): validated point, no-contact imperfection sweep &mdash; 3/8 feasible, majority fail
  via ring-passthrough.
- D007/D008 (H5): contact-migrated, SAME 8-draw sweep &mdash; 8/8 feasible, complete reversal.
- D009 (H6): zoom-BO over the exposed 6D box, finds a point exceeding the then-current best
  reading.
- D010/D011 (H7/H8): real 3D restrained-warping check &mdash; joint strain fails by ~2&times; a
  straight end-buffer taper helps but not conclusively.
- D013 (H9): end_rise_scale=0.20 mitigation &mdash; passes strain, reading itself spike-suspicious.
- D021/D022 (H12): ring-flare (ratio_top_diameter=-0.40) + end_rise_scale=0.0 &mdash; passes
  joint-strain with 4.1% margin.
- D023 (H13): 8-draw sweep at the flare-rescued point &mdash; 5/8 (62.5%) feasible corrected,
  3/8 fail to converge at all (a genuinely fragile solver basin, not just a strain failure).
- D027 (H14): sustained-fraction check on the flare-rescued point &mdash; 22.8%, ambiguous
  (dominated by an early-buckling spike per PROBLEM_STATEMENT Lesson 6's own standard).
- D030: a 250&times;-finer Riks re-solve to rule out a coarse-increment artifact specifically
  &mdash; shifts the true peak (mcs=0.0525, &sigma;=0.4327 kPa, still 1.93&times; target) but
  D031's recomputed sustained fraction on the corrected curve is 27.9% &mdash; still ambiguous.
- D032/D033/D034: mapped the end_rise_scale-vs-flare trade-off directly &mdash; D032
  (end_rise_scale=0.4) is genuinely sustained (65.8%) but fails joint-strain by 11%; D033 (more
  flare) made both worse; D034 hit the same spike signature seen at ~20 other combinations.
- D029/D035 (H15, this run's final comparison delegation): D24's own original design re-solved
  fresh under the current oracle &mdash; sustained fraction 20.65%, statistically
  indistinguishable from this family's own 22.8-27.9% ambiguous band.

**Chart correction (2026-08-31):** the H12 curve on this slide's own mini-plot was rebuilt
from D030's fine-grid re-solve (`riks_432eda2b8acc4d49b2bd8c9a5da1613f`, &sigma;_peak=0.4327
kPa, mcs_at_peak=0.0525), not D021's original coarse ODB
(`riks_2187327444c4421fa655079a9794c886`, &sigma;_peak=0.5987 kPa at the same coarse-increment
mcs_at_peak=0.00125 artifact this slide's own Timeline already diagnoses). The coarse ODB's
raw curve carries a dominant early spike that visually contradicts this slide's own caption
("not a visible spike difference") — the fine-grid curve is what the caption was written to
describe. No number in the visible bullets changed; only which ODB the chart itself reads from.

**Second chart correction (2026-08-31, rebuilt with `bo/mini_chart.py`):** now plots the full
unwindowed history (both curves reach mcs=1.0), colored by local strain (mls) per the deck's
corrected convention (rule 2c-VIS). Neither D032 nor the D030 fine-grid curve ever crosses the
2% strain cap (max 1.72%/1.75%) — the ordinary beam-theory `mls` this chart shows is not what
disqualifies D032; that is the SEPARATE, stricter real-3D joint-warping check
(`validation/warping_check`), which is not part of this chart's data at all. Neither curve
ever turns the flat grey the color scale reserves for "past 2%", for that same reason.

**Infra:** bo/D44_oracle_chained_arch.py, scripts/supercompressible_lin_buckle_chained_arch.py
(modified this run), scripts/supercompressible_riks_chained_arch_contact.py (new this run) —
none yet promoted to gold.
-->

---
class: summary-slide
---

# Run `20260829T005522` — summary

<div class="text-sm leading-snug">

One real bug fix (H2, twist-buckling) and one real reproducibility collapse (H3/H9,
crosslinked-bundle). Everything else closed FALSIFIED/INCONCLUSIVE; no design cleared
feasibility this run.

</div>

<div class="text-xs leading-tight">

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Corrected-joint mast can reach feasibility | **&#8253;** | 2/20 decided, both fail badly (mcs=.12/.55) | D41 rev. &rarr; |
| H2 | Corrected joint lets Fang's twist mechanism engage | &#10003; | twist_energy_fraction 1.13e-4&rarr;0.1218, 1078&times; | D41 rev. &rarr; |
| H3 | Shifting crosslink position defers the snap past 80% | **&#8253;** | bias=0.0 baseline is a genuine divergence, not a plateau | D40 rev. &rarr; |
| H4 | High-Q bistable-arch Riks failures hide a real snap | **&#8253;** | "Convergence" under Explicit is inertia noise (ALLKE/ALLIE 21-23&times; over cap) | D24 &rarr; |
| H5 | Longeron-midspan stop avoids the ring-RP defect | **&#8253;** | Still diverges at mcs~0.51; rules out shared ring-RP DOF | D31 &rarr; |
| H6 | Point B is a genuinely different structural regime | **&#8253;** | "Load reversal" criterion is genuinely ambiguous as stated | D43 &rarr; |
| H7 | Coilability failure driven by twist_angle too large | &#10007; | Shrinking twist_angle LOSES coilability — opposite of predicted | D41 rev. &rarr; |
| H8 | Full 6D search finds a real bistable snap | &#10007; | 13/42 converged; the one "snap" is a known artifact | D24 &rarr; |
| H9 | Full 10D search finds a feasible design | &#10007; | 48 dispatched, 1 converged, that one infeasible (mcs=.242) | D40 rev. &rarr; |
| H10 | Capacity comes from the arch, not host geometry | **&#8253;** | Registered test came back infeasible/artifactual | D24 &rarr; |
| H11 | Adaptive BO finds a feasible grain-beam design | **&#8253;** | 21 points, near-random — no incumbent to guide search | D43 &rarr; |
| H12 | Full search of fixed joint finds a feasible design | **&#8253;** | 2/20 decided, both infeasible | D41 rev. &rarr; |

</div>

<div class="text-sm leading-snug">

&nbsp;&middot;&nbsp; **44 delegations, 171 ledgered evals, 10.87 h of 12 h**, GATED after 4 review rounds

 &nbsp;&middot;&nbsp; **Cost: $68.28**
</div>

<!--
H1/H2/H7/H12 DETAIL (twist_buckle). D002 found and fixed a real joint-DOF bug: the inherited
local datum released rotation about the joint's own approximate radial direction, not each
oblique rod's own bottom-to-top axis, structurally suppressing Fang et al.'s twist mechanism
regardless of geometry. Fixed (four coupling variants tried; see D41-2's own Infra
note), validated: twist_energy_fraction rose 1078x. But the corrected design still only
reaches mcs=0.03 (H1). D011 (H7) tested whether SMALLER twist_angle recovers coilability --
it does not; all 8 points fail Stage-1 outright, the opposite of the predicted recovery. D019
(H12) ran a full 20-design adaptive search of the corrected-joint family: only 2/20 dispatches
ever reached a decided verdict (5 Stage-1 rejects, 13 unresolved non-convergence), both
infeasible. Twist and coilability trade off sharply in this family; whether any point
resolves that trade-off is still open.

H3/H9 DETAIL (crosslinked_bundle). D004's own 9-point crosslink_spacing_bias sweep at the
D020 optimum found its own bias=0.0 reconfirmation salvaged (non-converged), with mcs=0.7173
(not 0.7191). D008's stabilization + 1800s escalation didn't fix it (0/5 riks_converged=1).
D012 (decisive): re-solved the SAME point on the plain, non-stabilized path at 9x the time
budget (5400s) -- still fails, returning in only 1197s with a confirmed genuine arc-length
divergence ("TIME INCREMENT REQUIRED IS LESS THAN THE MINIMUM SPECIFIED"), matching D004's
own reading to 6+ significant figures. D015 (H9) ran a real 48-eval BO campaign over the
family's full 10D box -- 38/48 reached Stage 2, only 1/48 (2.6%) ever converged, and that one
design was infeasible (mcs=0.242). No design in this family is currently confirmed working.

H4/H8/H10 DETAIL (bistable_arch). D010 (H4) escalated the 3 non-converged high-Q points to
Abaqus/Explicit dynamics -- all 3 "complete" numerically but fail the quasi-static-validity
gate hard (ALLKE/ALLIE 21-23x over the 0.05 threshold), i.e. inertia/impact noise, not a
legitimate reading. D014 (H8) ran a real, adaptive 42-point 3-phase zoom-BO campaign over the
family's full 6D box -- 13 converged, 11 strictly feasible (genuinely working designs exist),
but exactly 1 shows any snap-reversal and it is the same documented coarse-increment spike
artifact. D016 (H10) tried to attribute the best non-snap design's capacity to the arch
mechanism specifically vs. host cross-section/pitch alone -- the registered test came back
infeasible/artifactual (stab_ratio 2.2x its own cap); the host-alone comparison is a separate,
unregistered measurement, reported but not a clean answer to what was asked.

H5 DETAIL (secondary_stop). D017 attached the stop to a genuine FE node on the primary
longeron's own mesh (stop_attachment="longeron_midspan") instead of ZTOP_REF_POINT or a driven
surface -- zero shared equations with the ring reference point -- and it still diverges at
the identical mcs~0.51 with the identical residual signature every construction has shown
since D003. Conclusively rules out "shared ring-RP DOF set" as the cause across five
independent attachment/base variants now. One combination remains untried:
stop_construction="same_part" WITH this longeron-midspan attachment (each tested individually,
never together) -- outside this delegation's authorized scope, flagged for a future run.

H6/H11 DETAIL (grain_beam). D009 (H6) targeted "Point B" specifically -- the exact open
question flagged on D43's own prior slide. Result: genuinely ambiguous under the registered
falsification criterion, whose "load reversal" definition didn't match this study's own
established compression-only convention used elsewhere. D018 (H11) ran a further real
adaptive BO campaign (21 points) over the family's full 7D box -- found nothing, but thin: no
feasible/converged incumbent ever existed to seed the acquisition, so it fell back to
near-random Sobol sampling rather than a GP-guided search.

THE GATE HISTORY (4 rounds). call_001: REJECT -- CRITICAL, pipeline.ipynb was missing its
mandatory verdict/analysis cells entirely (a forward reference to "the Verdict cell" that did
not exist), plus a stale Hypotheses cell (H4 shown as "pending", H5/H6 entirely absent despite
being closed). call_002: REJECT -- both cell-structure findings resolved (independently
re-derived both headline numbers from the ledger and confirmed a match), but a NEW critical
surfaced: the notebook closed on a negative result with 19% of the wall-clock budget still
unspent, directly against PROBLEM_STATEMENT.md's explicit "exhaust the time limit... REJECT
a run you know has not used its time allocation" clause. call_003: REJECT -- still 11%
budget remaining (89% used) on a negative result, plus a specific literature-identified
alternative explanation for H2 (the ring's own bulk rotation, not the rod-joint DOF) left
unaddressed. call_004: PASS -- budget now at 91% used with one more genuine delegation (D020)
closing H5's last untried construction since call_003, and H2's alternative explanation
resolved by direct code inspection (the top ring's reference point carries no rotational BC
at all, confirmed against the bottom ring's explicit ur1/ur2/ur3=0). One MINOR finding
survived uncorrected: the Verdict cell's own hypothesis-count language (7/11/12) should read
"twelve" throughout -- cosmetic, does not affect any conclusion.

RETROSPECTIVE FLAGS (8 of 44 delegations flagged, all CONSISTENCY, none BLOCKED). Two are
worth a future run's attention, neither resolved here: (1) D009's flag that
bo/D43_oracle_grain_beam.py's convergence gate (requires literal Riks completion) is stricter
than bo/oracle_circular.py's (the PROBLEM_STATEMENT-named reference oracle, which had no such
distinction at all) -- FIXED post-run, see below. (2) D004's flag that a prior claim
("mls~0.003" at the crosslinked_bundle D020 baseline) didn't reproduce -- this run's own
re-solve of the same point got mls~0.0205, just over the 0.02 ceiling; the stale figure has
been removed from D40's slide. D001's flag (whether H2's "confound" framing matches Fang et
al.'s own model) was resolved the same run by direct code inspection (see H1/H2 detail above).

INFRA PROMOTED TO GOLD, POST-RUN (2026-08-29, later the same day, user-authorized). The H2
joint-DOF fix (commit 4c3da12); the secondary_stop D007/D017 diagnostic infra (commit
2b2f8b1); the grain_beam DataGenerator registration wrapper (commit a016152). Separately, the
window-closed-before-failure convention was applied uniformly to oracle_circular.py and
D43_oracle_grain_beam.py (commit d5aa47e) -- resolving retrospective flag (1) above: a result is
now decided if the specific quantity feasibility is judged on reflects real data confirmed
before any solver failure, on every family, not just the newer ones that already had this.
-->

---
class: idea-slide
layout: two-cols-header
---

# D41-2 &middot; Corrected joint lets the rod genuinely twist

::left::
<div class="text-sm leading-snug">

- **What:** corrected the longeron-ring joint's released-rotation axis to each oblique rod's
  own bottom-to-top axis (was the ring's shared radial direction) — the axis Fang et al.'s
  mechanism needs to twist about. Re-solved the matched validation point, then a 20-design
  follow-up search under the fix.
- **Origin:** D41's own base slide found the mechanism wasn't engaging — the joint axis was
  inherited unchanged from every straight-longeron family; tests whether fixing it works.
- **Stats:** n=1 validation point + 20-design follow-up.<br>
  Twist-strain fraction: 0.011%&rarr;12.2% (1078&times;) — engages, but only 3% compression.
  Follow-up: 5 Stage-1 rejects, 13 non-convergent, 2 decided (mcs=0.12, 0.55).<br>
  cleared: 0/2 &middot; novel: yes — genuine construction fix, not a resize.
- **Verdict:** UNDERPOWERED &middot; FERTILE-PARAMETRIC &middot; twist/coilability
  trade-off<br>
  Joint fix works — genuine twisting confirmed (1078&times;) — but the validated point and
  the follow-up's own decided pair (12%, 55%) all fall far short. Whether ANY point in this
  family reaches feasibility with the fix remains unknown; only 2/20 follow-up decided.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-2 px-4">
  <div class="text-sm opacity-70 text-center">No new video or chart (rule 2c-VIS exception):
  the corrected design's own failure point (3% compression) is visually indistinguishable
  from the undeformed mast, and a stress-history curve over that same sliver of range would
  show nothing a number doesn't already say. See D41's own base slide for what an ordinary
  (uncorrected-joint) collapse in this family looks like.</div>
</div>

<!--
**Input space:** same design vector as D41's own base slide (the joint-DOF fix is a
construction correction, not a new parameter); the 20-design follow-up re-searches that same
family's existing bounds under the corrected joint.

**Seed:** FERTILE, narrower now than the original slide's own Seed note — the joint-DOF fix
is done and confirmed working (see Result). What remains untested is whether ANY point in
this family's design space reaches feasibility (mcs>=0.80) with the corrected joint; a
20-design search found none, but explored only a thin slice (2/20 reached a decided
result). The open question is now specifically the twist/coilability trade-off, not the
joint construction.

**Prior attempt, reconciled (2026-08-31, verdict audit):** this was not the first fix
attempt. Run `20260826T012550` H4 (delegation D006, 3 days earlier) already "rebuilt the
chiral-twist joint so the rod is genuinely free to rotate... the exact confound diagnosed
on D41's own slide," measuring twist_energy_fraction peak=0.0731 (7.3%), 0 strict feasible
— that run's own text called it "clos[ing] the mechanism a second time, this time with the
confound actually removed." This slide's own D002 measured 0.1218 (12.2%) on the same
family. The two are not the same construction (D006's own notes describe a from-scratch
joint rebuild; this slide's Input space above describes a rotation-axis correction) and
the two numbers were never reconciled anywhere in the deck before this note. Both agree on
the practical conclusion (twist genuinely engages, feasibility still fails), so the
Verdict is unaffected — but a future agent comparing "twist_energy_fraction" across the
deck should know these are two different fixes to the same family, not one number cited
twice.

**Timeline:** D002 (run 20260829T005522, H2): the joint fix + matched-point validation.
H12 (same run): a 20-design follow-up search using the fixed joint -- 5 Stage-1 rejects, 13
unresolved non-convergence, 2 decided (both infeasible, mcs=.12/.55). Routed to H2 SUPPORTED
/ H1 & H12 INCONCLUSIVE per runs/20260829T005522/debug/strategizer_notes/hypotheses.json.
**Added (2026-08-31, verdict audit):** the same run's H7 (D011, 8 points) directly tested
this slide's own "twist/coilability trade-off" question from the other direction -- SMALLER
twist_angle, hoping to recover coilability -- and got the opposite of the predicted result:
all 8 points fail Stage-1 outright. Between H12 (larger search, still infeasible) and H7
(smaller twist, still fails, and worse), the trade-off looks sharp in both directions, not
just underexplored in one.

**Infra:** the joint fix lives in scripts/supercompressible_riks_twist_buckle.py and
supercompressible_lin_buckle_twist_buckle.py (promoted to gold, commit 4c3da12) -- see
either file's own module docstring for the full four-variant derivation of why a naive
"release twist at both ends" choice is a rigid-body mechanism, not a fix.
-->

---
class: idea-slide
layout: two-cols-header
---

# D40-2 &middot; The archived 71.9% never actually converged

::left::
<div class="text-sm leading-snug">

- **What:** re-solved the family's best-cited design (D020, archived at 71.9% compression)
  under two solver configurations — 9&times; larger time budget, and a non-stabilized path —
  then a 48-design adaptive search of the whole space.
- **Origin:** this headline had never been independently re-verified; checks whether it
  reproduces and whether ANY design in the family is confirmed working.
- **Stats:** n=48 &rarr; 38 Stage-1 &rarr; 1 Riks-converged &rarr; 0 good (0&times; Bessa).<br>
  D020 re-solved twice: both non-converged, agree to 6+ sig figs (mcs=0.7173) — a real
  arc-length divergence, not a timeout. Wider search (24 seeded+24 active): 1/48 converged,
  at mcs=0.242.<br>
  best good: none &middot; cleared: none &middot; novel: no — reproducibility check.
- **Verdict:** ARTIFACT &middot; REFUTED &middot; D020's own archived 71.9% headline<br>
  The family's best-cited result does not reproduce: both re-solves agree with each other
  but confirm a genuine divergence, not the archived reading. The 48-design search found
  only 1 convergent point anywhere, at 24%. No design in this family is confirmed working.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 440px">
  <div class="flex items-center justify-center" style="height: 140px">
    <img src="/gifs/D40-2_crosslinked_bundle_mini.png" style="max-height: 140px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D40_crosslinked_bundle_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-60 text-center px-2">D012's re-solve, unwindowed; greys out past the 2% cap.</div>
</div>

<!--
**Input space:** same 10-parameter design vector as D40's own base slide; the 48-design
adaptive search (24 seeded + 24 active) resamples that same space, no new parameter added.

**Chart correction (2026-08-31, rebuilt with `bo/mini_chart.py`):** now plots the full
unwindowed history in multiples of Bessa, linear, colored by local strain (mls) with the
deck's corrected convention (see rule 2c-VIS), not the old sigma-colored, window-truncated
version. The curve visibly turns grey at mcs&asymp;0.72 — confirming, from real per-frame
data, that "matches D004's reading" (cited elsewhere on this slide as
mcs=0.7173) was always the same point as the strain-cap crossing, not a coincidence.

**Seed:** FERTILE — the family's own construction, not this one design point, is the open question
now: something prevents a clean Riks solve near this optimum, and no confirmed working
design currently exists anywhere in the space searched. Untried: whether a different
crosslink placement/spacing entirely (outside the neighborhood re-tested here) avoids
whatever this design point is hitting.

**Timeline:** D004 (run 20260829T005522, H3): 9-point crosslink_spacing_bias sweep at the
D020 optimum, best mcs=0.7173 at bias=0.0 (the baseline itself) -- all 9 points salvaged
(non-converged). D008: stabilization + 1800s escalation on the same 5 points, 0/5 reached
riks_converged=1. D012 (decisive): re-solved the bias=0.0 baseline on the plain,
non-stabilized path at 9x the time budget (5400s) -- returned in 1197s with a confirmed
genuine arc-length divergence ("TIME INCREMENT REQUIRED IS LESS THAN THE MINIMUM
SPECIFIED"), matching D004's own reading to 6+ significant figures. D015 (H9): a real
48-eval constrained-BO campaign (24-point seeded DoE + 24 active) over the full 10D box --
38/48 reached Stage 2, 1/48 (2.6%) reached riks_converged=1, and that one design was
infeasible (mcs=0.242).

**Infra:** no code changed for this family this run -- D40_oracle_crosslinked_bundle.py and its
Riks script are unchanged. The finding is entirely about this specific design point's own
reproducibility, not a construction bug. Sigma-history chart built from D012's own real,
340-frame salvaged history:
/oscar/scratch/eaguerov/sc_oracle_crosslinked_bundle/riks_26dc76db026249d093d739469e0dc99a/
results.pkl (reduced with this study's usual sigma = |RF[2]|*1000/(pi*D1^2/4*n_longerons_
effective) formula, n_longerons_effective=8 for n_longerons=4 x n_sub_beams=2).
-->

---
class: summary-slide
---

# Run `20260826T233507` — summary

<div class="text-sm leading-snug">

This run closed the grain-beam family (H3) at n=44 real dispatches, and — from a completely
different code path, read-only, zero new solves — independently re-derived the exact
contact-artifact finding already on D42's slide. The correction is not a one-off analysis quirk.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Serpentine reproduces its own headline in a fresh run, plus a widened box and imperfection robustness | &#10003; | &sigma;_peak=0.646302 kPa, 0.0% diff from D42's own value; box 8/28 feasible; imperfection 5/6 feasible (0.48&ndash;0.72 kPa) | D42 &rarr; |
| H2 | A second, independent novel mechanism exists beyond serpentine | &#10007; | Literature-only scouting (11 papers); no candidate judged independent of grain-beam; best alternative (a self-contact family) flagged despite a weak prior track record (48.6% max compression) | &mdash; |
| H3 | Grain-beam's literal chiral sub-lattice keeps its lowest buckling mode global, escaping the shell-based dead end | &#10007; | 44 real Stage-2 dispatches (tightened Riks settings); 0 converged; 1/44 clears mcs&ge;0.80 &amp; mls&le;0.02 but never reaches LPF=1.0 | D43 &rarr; |
| H4 | Serpentine's late-&sigma; rise is genuine bend-twist post-buckling capacity | &#10007; | Independent CPRESS re-derivation (read-only, 0 new solves) on D004's own ODB reconfirms D42's 2026-08-26 correction: a contact artifact | D42 &rarr; |

&nbsp;&middot;&nbsp; **10 delegations, 155 ledgered evals, 8.85 h of 10 h**, UNGATED after 3 review rounds

 &nbsp;&middot;&nbsp; **Cost: $28.21**
</div>

<!--
H1 DETAIL. D004 re-solved D42's exact winning design (bo/oracle_serpentine.py, now the canonical
namespace='serpentine' entrypoint) and reproduced sigma_peak=0.646302 kPa to a 0.0% difference --
this run's own point estimate, not a re-read of the archived ODB. A widened-box campaign (28 real
Stage-2 dispatches) found 8/28 feasible, best 0.48059 kPa. A 6-draw imperfection-robustness study
found 5/6 feasible (0.481644-0.717763 kPa); the 1 infeasible draw (3.14deg imperfection) failed
Stage-2 convergence (salvaged partial ODB, riks_strain reached only 0.59) and is non-comparable,
not folded into the feasible range.

H2 DETAIL. D006 (backup-candidate scouting while the grain-beam campaign ran) reviewed 11 papers
and evaluated 6 candidate second-mechanism families against PROBLEM_STATEMENT.md's own named
exclusions (rigid-linkage reduction, over-stiff substitution suppressing global coiling) -- 4 of 6
failed once actually read against a direct quote, not skimmed. The remaining top pick, a
self-contact chiral-truss family (Farzaneh et al.), was recommended despite this study's existing
self-contact family (D33/D34) having a weak track record (best-ever 48.6% compression, well under
the 80% floor, never confirmed load-bearing). Scouting only -- not built or tested this run.

H3 DETAIL. D003 inherited a partially-built grain-beam family from an earlier interrupted attempt
(oracle, prefilter gate, Stage-1/Stage-2 scripts, an 8-point Stage-1 screen already complete) and
root-caused a failed Stage-2 validation: the Riks surface `ALL_LONGERONS_SURF` was built from
EVERY ring-hoop and bar edge, so interior grain-ring joint nodes (2 ring edges + 2 bar edges
meeting) triggered Abaqus's own input-processor rejection ("MORE THAN TWO UNDERLYING ELEMENTS
HAVING A COMMON NODE") before the job ever started. D005's first real campaign (70 dispatches,
pre-fix settings) found 0/70 converged; D007 diagnosed the population as MIXED -- some designs are
genuine settings-independent snap/bifurcation dead ends, others were merely settings-starved -- and
tightened the Riks increment controls (maxNumInc=8000, initialArcInc=1e-3, minArcInc=1e-12,
maxArcInc=0.05, MAX_SOLVE_SECONDS=2400s). D008 baked this into the canonical
scripts/supercompressible_riks_grain_beam.py + bo/D43_oracle_grain_beam.py. D009's follow-up campaign
(44 real dispatches under the tightened settings, surviving a mid-campaign CEI-BO seed-diversity bug
that wasted 13/15 solves on bit-identical re-proposals -- see BLOCKED below) genuinely rescued some
previously-starved designs (1/44 now reaches mcs&ge;0.80 outright vs 0/70 before), but the
family's snap/bifurcation behavior right at LPF=1 held as a real physical wall for every design
tested, including the closest ("Point B": R=3.931, t=0.535, alpha=4.772, beta=1.526, chirality=-1,
w=2.539; mcs=0.8178, mls=0.0197), which dies to "TIME INCREMENT REQUIRED IS LESS THAN THE MINIMUM
SPECIFIED" just short of the finish line -- see D43's own slide.

H4 DETAIL. D010 was a targeted, time-boxed (<15 min), read-only follow-up: the critic flagged that
this run's notebook draft hadn't caught up with D42's own 2026-08-26 mechanism correction already
on record in the deck. D010 opened D004's still-extant Riks ODB (no re-solve), extracted per-frame
CPRESS/RF3 field output via a fresh script (a distinct code path from whatever produced the
2026-08-26 slide correction), and found CPRESS is exactly 0.0 for frames 0-63 (spanning the entire
genuine, contact-free buckling event and its post-buckling valley) and turns nonzero at frame 64,
after which RF3 and CPRESS rise monotonically together to the final frame -- 26x larger than the
true contact-free structural peak. Independent, second-code-path confirmation that D42's headline
sigma_peak is driven by the wavy longeron contacting the rigid loading disc, not by bend-twist
post-buckling capacity.

THE CRITIC'S ARC (3 review rounds, never reached PASS). call_001: no CRITICAL finding. call_002:
MAJOR -- the notebook's grain_beam funnel count (65 screened out / 54 reached Stage 2) was
authoritative-sounding prose backed by a broken `campaign_summary.summarize()` call for this
family's data (a `decided_key` default that doesn't exist in this family's schema), so the printed
funnel would not reproduce those numbers if the notebook cell were actually executed -- the
underlying 54-count is independently correct and verifiable via direct QueryStore, so the
conclusion (H3 FALSIFIED, objective floor cleared) is not invalidated, but the "authoritative"
framing overstated what the code actually derived. call_003: REVISE again -- the same
`campaign_summary` call still had two independent bugs (`n_prefiltered` computed by string-matching
a `note` field that never contains the word "prefilter" for this family; `is_decided()` defaulting
to a `decided_key` column, `window_closed_before_failure`, that does not exist anywhere in the
store). Fixable without new evaluations, but the run exhausted its 10h budget before a 4th pass
could land -- UNGATED, not FAILED: the scientific verdicts stand, the notebook's own funnel-count
code does not yet correctly reproduce them.

RETROSPECTIVE FLAGS: none flagged this run (14/14 retrospectives clean) -- the closest to a genuine
finding was D007's own FRICTION note (undocumented QOS cap on ad-hoc sbatch jobs outside the async
dispatch machinery, worked around via `--account=mbessa-condo`), not rising to a deck-level issue.

BLOCKED (D009, self-diagnosed, not a capability gap): a mid-campaign top-up batch landed only 1/15
new real rows -- traced to `bo/cei_core.py`'s async CEI acquisition being near-deterministic once
conditioned on similar training data, so a different outer `seed` only diversifies the initial
Sobol DoE, not the ~74 subsequent CEI proposals; 73/80 candidates across two "differently seeded"
runs were bit-identical, silently dedup-dropped, wasting real Abaqus compute. Worked around with a
pure OS-entropy random top-up. Flagged for whoever owns `cei_core.py`, not fixed this run.

INFRA BUILT THIS RUN, not yet promoted to gold: the grain-beam family itself (bo/D43_oracle_grain_beam.py,
bo/prefilter.py:passes_grain_beam_slenderness, scripts/supercompressible_{lin_buckle,riks}_grain_beam.py
+ pp), now falsified but real, reusable infra; the tightened Riks increment-control settings (D007/
D008); D009's `campaign_summary.py`-adjacent `build_final_summary.py` (reusable funnel-count builder,
the fix the critic wants applied to `campaign_summary.py` itself, not yet done). Promotion is the
user's call.
-->

---
layout: two-cols-header
class: idea-slide
---

# D43 &middot; Grain-beam (chiral sub-lattice) longeron

::left::

<div class="text-sm leading-snug">

- **What:** A literal, periodic B31 beam-element mesh along each longeron: repeating stiffer
  "grain" inclusions (locally-enlarged cross-section) connected by slender, chirally-offset bar
  pairs — a real discretized lattice, not a homogenized section.
- **Origin:** Pancella &amp; D'Annibale (2025)&sup1; — a periodic chiral-grain lattice carries a
  homogenized extension-shear/bend-twist coupling from material chirality itself (the grain-bar
  offset), not from centerline geometry the way serpentine's coupling is — testing whether that
  distinct channel keeps the lowest buckling mode GLOBAL coiling, not local grain/bar buckling,
  the failure mode that killed this study's prior shell-based chiral attempts (D26/D27/D38).
- **Stats:** n=119 &rarr; 54 coil &rarr; 0 riks &rarr; 0 good
  quartiles unavailable — 0/54 Stage-2-eligible designs converged (44 real dispatches, tightened
  settings; best mcs=.818, mls=.0197, never reaches LPF=1.0)
  cleared: none &middot; novel: yes — a literal chiral sub-lattice mesh, unlike D26/D27's shells
  or D41's twist joint
  best good: none (0/54 passed every criterion)
- **Verdict:** POWERED &middot; FERTILE-REWORK &middot; chiral-lattice embodiment<br>
  Lowest mode stays global for some designs (54/119 pass Stage 1), but no Riks solve ever
  completes — the snap near full compression is a real obstacle, confirmed at scale (44
  dispatches; looser numerics rescued lower-mcs designs but not the finish), not a numerics
  artifact.

</div>

::right::

<div class="flex flex-col items-center justify-center gap-1" style="height: 400px">
  <img src="/gifs/D43_grain_beam_native.gif" style="max-height: 340px; max-width: 100%" class="rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Stage-1 Mode 1, "Point B" — no Riks history exists.</div>
</div>

<div class="text-xs opacity-50 mt-1">
&sup1; Pancella &amp; D'Annibale (2025), "A Timoshenko-like equivalent beam model for the static
analysis of a chiral metamaterial", <i>Continuum Mechanics and Thermodynamics</i> 37:59 — cited
&amp; verified against the study's own literature corpus (CorpusList).
</div>

<!--
**Input space:** n_cells&isin;[3,8] — discrete grain-inclusion count. R&isin;[3.0,4.0] — grain
radius (relative). t&isin;[.40,.55] — bar thickness. w&isin;[2.0,3.5] — bar width. alpha&isin;
[1,5], beta&isin;[1,5] — grain/bar chirality-offset shape parameters. chirality&isin;{-1,+1} —
discrete handedness. Fixed: n_longerons=3, n_storeys=1, D1=100mm, ratio_shear_modulus=.3677.

**Seed:** BARREN — the failure is not parametric within the tested box: D009's 44-point campaign
(seed=1 continuation + seed=2 top-up, the latter mostly wasted on a near-deterministic CEI-BO
acquisition re-proposing already-ledgered points — see notes) plus a pure-random top-up all
converge on the same wall (0 designs reach LPF=1.0), and D007's diagnosis (genuinely different
solver settings genuinely rescue SOME designs to mcs&ge;0.80, but not to full compression) rules
out a numerics-only explanation. What's untested: whether a fundamentally different Riks
stabilization strategy (energy-dissipation stabilization rather than pure arc-length control,
which this study's charter otherwise avoids as a science-methodology change requiring approval)
could push past the snap point at all, or whether the snap is a genuine structural dead end for
this topology regardless of solver.

**Deferred:** whether the 1/44 design that individually clears both mcs&ge;0.80 and mls&le;0.02
sub-criteria ("Point B") represents a genuinely different structural regime from the other 43, or
sits on the same wall by coincidence of being closest at time of failure — not adjudicated this
run, would need a targeted local sweep around Point B's own coordinates specifically to answer.
Still open as of 2026-08-29 (run 20260829T005522, H6 -- see Timeline below): a targeted
re-examination of Point B found the answer genuinely ambiguous under the registered
falsification criterion, not a clean confirm/refute -- Point B's status cannot move past
INCONCLUSIVE until that criterion's "load reversal" definition is resolved to a single,
stated meaning.

**Timeline:**
D002: literature review — identified Pancella &amp; D'Annibale (2025) as the grounding citation,
distinguished from Frenzel/Wu-Qi-Liao's 3D chiral-truss precedent (deferred to D006 as a possible
H2 candidate, ultimately not pursued as independent of this family).
D003 (this run): inherited a partial build, root-caused and fixed the Stage-2 contact-surface
topology bug, completed the family's first real Stage-2 validation attempt.
D005 (this run): first real campaign, 70 dispatches, pre-tightened-settings, 0/70 converged.
D007 (this run): diagnostic — mixed-population diagnosis, tightened Riks increment controls.
D008 (this run): baked D007's settings into the canonical oracle/scripts.
D009 (this run): follow-up campaign, 44 real dispatches under tightened settings, 0/44 converged,
1/44 clears both feasibility sub-criteria individually.
D009 (run 20260829T005522, H6 -- different run, same delegation number): targeted
re-examination of "Point B" specifically, the exact open question this slide's own Deferred
note above raised. Result: genuinely ambiguous under the registered falsification criterion --
its "load reversal" definition didn't match this study's own established compression-only
convention used elsewhere -- routed to INCONCLUSIVE, not a clean confirm/refute of Point B's
regime.
D018 (run 20260829T005522, H11): a further real adaptive BO campaign (21 points) over the
family's full 7D box -- found nothing, but thin: no feasible/converged incumbent ever existed
to seed the acquisition, so it fell back to near-random Sobol sampling rather than a
GP-guided search.

**Infra:** bo/D43_oracle_grain_beam.py, bo/prefilter.py:passes_grain_beam_slenderness,
scripts/supercompressible_lin_buckle_grain_beam.py + _pp.py,
scripts/supercompressible_riks_grain_beam.py (tightened increment controls: maxNumInc=8000,
initialArcInc=1e-3, minArcInc=1e-12, maxArcInc=0.05, MAX_SOLVE_SECONDS=2400).
ODB: /oscar/scratch/eaguerov/sc_oracle_grain_beam/lin_29e1c5e40f4a4905b8cbf9d17dfc8961/ (Point B's
Stage-1 LIN_BUCKLE solve — the family's own best-found point, per this slide's no-Riks-history
convention; no Stage-2/Riks ODB exists for this or any grain-beam design).
-->

---
class: summary-slide
---

# Run `20260826T012550` — summary

<div class="text-sm leading-tight">

This run found a genuinely new mechanism clearing the incumbent for the first time since
`run17_rectangle`, and caught its own overclaim about why before it shipped.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | The kinematic-depth-cap wall holds generally, across families | &#10007; | Reconfirms prior findings; not a fresh mechanism test this run | — |
| H4 | Chiral twist-buckling escapes the cap once the D41 joint confound is fixed | &#10007; | 0 strict feasible even with the rod free to twist; twist_energy_fraction caps at 7.3% | D41 &rarr; |
| H5 | Crosslinked beam bundle (D40's near-miss) escapes via targeted post-buckling shaping | &#10007; | 0/59 Stage-2 converged | D40 &rarr; |
| H1/H3/H6 | Serpentine (wavy in-plane) longeron clears both floors (own slide) | &#10003; | &sigma;_peak=0.6460 kPa — 2.88&times; target, 1.06&times; incumbent | D42 &rarr; |
| H7/H8 | Robust to manufacturing imperfection (8, 8 independent draws) | &#10003; | 6/8, 7/8 feasible; &sigma; 0.48&ndash;0.73 kPa across draws | D42 &rarr; |
| H9 | Peak local strain is not at a rigid joint | &#10003; | Peak at arc-length fraction 0.75 (mid-span); joint-zone strain 0.0122 vs 0.0190 windowed peak | D42 &rarr; |

**Caught by its own critic, not by hindsight:** the first draft claimed the new post-buckling
channel *causes* the 6% margin — but two delegations had already reported the opposite (margin
traces to zoom-BO refinement, not the newly opened box). The critic's MAJOR finding forced the
claim down to "plausible, not demonstrated" — existence stands, causation doesn't, D42 says so.
&nbsp;·&nbsp; **12 delegations, 279 evals, 7.5/12 h**, GATED after 4 review rounds
&nbsp;&middot;&nbsp; **Cost: $75.70**
</div>

<!--
H4 DETAIL (folds in here, refinement of D41 per rule 1). Delegation D006 rebuilt the chiral-twist
joint so the rod is genuinely free to rotate independent of the ring's own rigid-body rotation --
the exact confound diagnosed on D41's own slide. 45 ledgered evals, 0 strict feasible,
twist_energy_fraction peaked at 0.0731 (still far below a 50% dominant-mode bar), and 21 of 45
points reached a >=10x comparison bar on an unrelated axis without ever engaging twist. Closes
the mechanism a second time, this time with the confound actually removed -- D41's own finding
was not an artifact of the locked joint.

H5 DETAIL (folds in here, refinement of D40 per rule 1). Delegation D010 targeted the crosslinked
bundle's asymptotic post-buckling stiffness directly (shaping the crosslink connector's own
stiffness curve, not just its magnitude) -- 0/59 Stage-2 converged, mcs-vs-lambda correlation
0.02 (no relationship), best found mcs_windowed=0.081. D007's own retrospective flagged a real
premise mismatch in its own task brief (assumed D40's 71.9% figure came from a finite/compliant
connector; it came from D017's rigid kinematic tie) -- investigated with real diagnostic solves
rather than accepted at face value, per this delegation's own CONSISTENCY-flagged retrospective.

THE CRITIC'S FULL ARC (4 review rounds). call_001: no finding, verified provenance and the
literature corpus entry. call_002: MAJOR -- the causal claim above overstated what D005/D008's
own delegation reports established (quoted verbatim above). call_003: RESOLVED -- the notebook
was rewritten to hedge the causal claim explicitly, re-verified against the raw transcripts, not
just re-claimed. call_004: no CRITICAL/MAJOR remaining, GATED.

RETROSPECTIVE FLAGS (4, all genuine, all resolved in-run except one). D001 (literature reviewer)
flagged a real inconsistency between PROBLEM_STATEMENT.md's new Lessons-learned section 6 (the
splice-in-disguise warning, added the same advisor session) and the D24-revisited slide's own
Verdict text, which had not been updated to match -- fixed as its own commit, this session.
D005/D006/D007 (implementers/datagenerator) each flagged a task-brief premise that didn't match
the underlying code or a prior run's own mechanism, investigated and resolved with real evidence
rather than trusted or silently worked around.

BLOCKED (D006, matches TRAPS.md #9): a concurrent-write ledger-loss bug inside the vendored
a3dasm harness dropped some of D006's own campaign rows mid-run. Recovered via the campaign's own
aggregate JSON output (not lost, just not individually re-derivable from the ledger) -- the same
class of bug already documented, not a new one.

INFRA BUILT THIS RUN, not yet promoted to gold: bo/oracle_serpentine.py (the real result),
bo/oracle_chiral_twist.py, bo/oracle_crosslink_bundle.py, matching scripts/ pre/post-processors,
and a genuinely new addition to bo/prefilter.py -- a local-radius-of-curvature slenderness gate
for wavy centerlines, extending the existing global beam-theory-validity check to a failure mode
only a non-straight member can have. Promotion is the user's call.

COST RECONCILIATION. telemetry/summary.json records $74.13 with an EMPTY strategizer entry in
by_role (same gap as the prior run). Summing directly from the strategizer's own transcript:
$1.57. Actual: $74.13 + $1.57 = $75.70.
-->

---
layout: two-cols-header
class: idea-slide
---

# D42 &middot; <u>Serpentine (wavy in-plane) longeron</u>

::left::

<div class="text-sm leading-snug">

- **What:** Offset each longeron's centerline from the straight ring-to-ring chord by a sinusoid
  in the TANGENTIAL direction — perpendicular to the mast's own coiling-bow plane, not within it
  — with a strongly anisotropic cross-section (stiff in-plane, compliant out-of-plane).
- **Origin:** Shi, Huang, Yu &amp; Li (2024)&sup1; — an anisotropic serpentine strip buckles OUT
  of its own planform via a coupled bend-twist mode (a double-eigenvalue bifurcation), a
  different post-buckling channel than the planar coiling every other family here shares.
- **Stats:** n=140 &rarr; 121 coil &rarr; 61 riks &rarr; 51 good (5.76&times; Bessa)
  p50/p90/p100 — &sigma;_crit: .12/1.27/5.61 &middot; mcs: .85/.94/.95 &middot; mls: .041/.057/.097
  cleared: 38 of 61 decided &ge; 2&times; Bessa (0.2244) &middot; novel: qualified — a peak
  alone isn't distinctive (Bessa has one too); see Verdict
  best good: pitch=.5327 top_d=.1298 a=.00622 b=.02033 amplitude=.03164 n_undulations=2 &rarr;
  &sigma;=.6460 mcs=.93 mls=.019
- **Verdict:** POWERED &middot; VALIDATED &middot; wave-driven disc contact<br>
  Clears both targets (2.88&times;, 1.06&times; floor). **Correction (2026-08-26):**
  contact-driven, not bend-twist — an ablation control never touches the disc; this design's
  late &sigma; tracks the disc's CPRESS. **Novelty qualified (2026-08-28, PI review):** a peak
  isn't distinctive — Bessa has one too (early, ordinary buckling, then decays; CPRESS=0
  throughout). Novel is deferring it to late compression via real contact, under the 2% strain
  ceiling throughout. Mesh convergence open — see notes.

</div>

::right::

<div class="flex flex-col gap-2" style="height: 420px">
  <div class="flex items-center justify-center" style="height: 155px">
    <img src="/gifs/D42_serpentine_mini.png" style="max-height: 155px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 257px">
    <img src="/gifs/D42_serpentine_landscape.gif" class="rounded shadow-lg" style="max-height: 257px; max-width: 100%" />
  </div>
</div>

<div class="text-xs opacity-50 mt-1">
&sup1; Shi et al. (2024), "Double-eigenvalue bifurcation and multistability in serpentine
strips" — cited &amp; verified against the study's own literature corpus (CorpusList).
</div>

<!--
**Input space:** ratio_pitch&isin;[.35,1.20] — storey height / D1, narrowed at the low end where
the new local-curvature gate binds hardest. ratio_top_diameter&isin;[0,.60] — taper, kept
non-negative so this family's result is never confounded with the already-closed "flare the
rings" lever. ratio_a&isin;[.003,.020] — OUT-of-plane (radial) cross-section half-dimension, kept
small so radial bending/twisting stays the compliant channel. ratio_b&isin;[.015,.05] — IN-plane
(tangential) half-dimension, kept large relative to ratio_a (aspect ratio spans ~1&ndash;16).
amplitude_rel&isin;[.01,.08] — peak tangential wave offset / D1, lower-bounded so the wave is a
genuine planform feature, not a near-straight re-test of the baseline. n_undulations — discrete
wave-period count. Fixed: n_longerons=3, n_storeys=1, twist_angle=0, ratio_shear_modulus=.3677.

**Verdict, full text (trimmed from the visible bullet 2026-08-28 to fix a confirmed 514px
render clip, headless-measured):** the existence claim (clears both the 2&times;-Bessa target
2.88&times; and the incumbent floor 1.06&times;, holds up under 2 independent imperfection
studies, peak strain mid-span) is solid. **Correction (2026-08-26, advisor session, direct
ablation):** the claimed mechanism is not what's actually happening. Re-solving the identical
design with amplitude_rel&rarr;0 (a straight-centerline control, same cross-section/pitch) shows
the control's CPRESS at the rigid loading disc stays exactly 0 for its entire history, run all the
way to full geometric closure — it never reaches the disc. The serpentine design's late &sigma;
rise (mcs&asymp;85% to its window's close) tracks that SAME disc's CPRESS rising in lockstep
(4&rarr;214 kPa). The headline number comes from the wave's shape bringing the member into
contact with the rigid loading disc, not from the claimed bend-twist post-buckling channel — real
and wave-caused (the control disproves a generic every-design-eventually-squishes story).
**Novelty resolved (2026-08-27):** re-solved the actual Bessa reference point (not just the
matched-cross-section control) under the same contact oracle — it never touches the disc anywhere
in its own history, and its own peak occurs early (mcs&asymp;15%) before decaying monotonically
to near-zero, the opposite shape from D42's late rise. The floor does not do what D42 does; this
is a genuinely distinct, contact-mediated channel. **Mesh check (2026-08-26):** &sigma;_peak
itself is not fully mesh-converged — see below. **Independently reconfirmed (run
`20260826T233507`, D010):** a second, unrelated CPRESS extraction on the same ODB — a distinct
code path, zero new solves — reproduces the identical frame-by-frame finding: contact-free
through frame 63, CPRESS and RF3 rising together from frame 64 on.

**Sharpened 2026-08-28 (PI review, actioning the ADVISOR CAVEAT below):** the PI pointed out that
Bessa's own design also has a stress peak, so "novel because it has a late peak" was never a
precise enough claim — every compressed member peaks somewhere over its own loading history,
Bessa's included. The comparison that actually matters is not "does it peak" but "what KIND of
peak is it." Bessa's is an ordinary early elastic-buckling maximum (mcs&asymp;15%) followed by
monotonic softening (&sigma; decaying toward zero) — the textbook post-buckling signature, with
zero contact anywhere (CPRESS=0, all 63 frames) and nothing that looks like a design running out
of room. D42's is a late, contact-driven RISE (&sigma; climbing in lockstep with CPRESS from
frame 64 on) that stays under the 2% local-strain ceiling the entire time it's happening — a
qualitatively different event (stiffening against a hard kinematic limit, not softening after a
critical load), and one Bessa's own design never exhibits at any point in its history. So: having
"a peak" is not what's novel (concede that point fully); reaching one LATE, via genuine contact,
without ever breaching the strain ceiling, is — and Bessa's own re-solved reference is the direct
evidence that this specific combination is not something "any design eventually does."

**Seed:** FERTILE — narrowed (2026-08-26): a cross-section-swap probe (identical wave, isotropic
CircularProfile substituted for RectangularProfile, radius matched to the SAME cross-sectional
area) still drives the member into real disc contact (COPEN closes to exactly 0, both surfaces,
mcs&asymp;65-70%) and produces the same qualitative late-&sigma; rise, so the effect is not specific
to Shi et al.'s anisotropic bend-twist mode — it survives a completely different, isotropic
cross-section as long as the WAVE is present. What's still untested: WHY the wave's coiled shape
reaches the disc while the straight control's does not. Track the longeron's own 3D trajectory
frame-by-frame near the contact-engagement point for both to see what geometric quantity actually
diverges — axial position, radial excursion, or something else. That would settle whether this is
an exploitable geometric lever or an accident of where D1=100mm places the disc relative to this
design's own coil radius (one probe, not a swept campaign — the circular substitute is also
substantially stiffer pre-contact, ~2.3&times; Bessa vs the rectangle's ~0.3-0.4&times;, since an
isotropic circle at matched area is much stiffer than a highly-elongated anisotropic rectangle in
its own weak/radial direction).

**Deferred:** RESOLVED (2026-08-26, advisor session) — the causal-mechanism question the critic
left open (call_002) is no longer just hedged. A direct ablation (identical design,
amplitude_rel&rarr;0) disproves BOTH candidate explanations on the table: not the claimed
bend-twist post-buckling channel (the control's own CPRESS at the loading disc is exactly zero
throughout, so nothing about the anisotropic cross-section alone produces this), and not a
generic "every design eventually bottoms out against the disc" story either (the control's
&sigma; just monotonically fades toward zero, run all the way past mcs=100% nominal, with no late
rise at all). The real cause: the wave's own shape brings the member into disc contact where the
straight member's shape does not, in the SAME compression range. Still open: WHY (see Seed above)
— and whether that contact-mediated load path is a real, exploitable structural lever or a
boundary-condition accident specific to this disc's placement.

THE COMPRESSION-LIMIT CONSTRAINT, EXPLAINED (added 2026-08-27, expanding the advisor caveat
below into an actual physical account, not just a flag). Why would ANY design's &sigma; rise late
in compression, independent of what its own "novel" feature is doing? Because &sigma;_peak is the
MAXIMUM reaction force over the whole compression window, and once a design's own members run out
of room to bend/coil freely — either by geometrically exhausting their own coiling motion, or (as
here) by physically contacting a rigid surface — continuing to advance the prescribed compression
means pushing against something far stiffer than the original compliant structure: a hard
kinematic limit, not a buckling member. That's a generic "running out of give" effect, the
mechanical equivalent of a spring reaching solid height, and it says nothing in itself about
WHATEVER specific feature (a wave, a twist, a splice) the design under test happens to have — any
design pushed far enough toward its own compression ceiling will show some version of this same
late rise. The ablation control above already demonstrates the generic case directly: even the
STRAIGHT centerline control shows a real early elastic peak (&sigma;=0.119 kPa at mcs&asymp;6%,
1.06&times; Bessa) before fading — an ordinary compression response with no wave involved at all.

ADVISOR CAVEAT (2026-08-27, PI review — ACTIONED 2026-08-28, see "Sharpened" note above and the
visible Stats/Verdict wording): a high &sigma;_peak reached simply because a design approaches
ITS OWN compression limit
is technically valid but not novel by itself — Bessa's own original baseline already has this
property (its own ablation control above shows an ordinary early elastic peak, &sigma;=0.119 kPa
at mcs&asymp;6%, unrelated to any wave). What would make D42 genuinely new is showing the
contact-driven LATE rise is a distinct, exploitable phenomenon beyond "any design close enough to
the disc eventually sees &sigma; rise" — not yet settled either way. No new evidence gathered
this entry; this is a scoping note for whoever writes the family's final verdict, not a finding.

**RESOLVED 2026-08-27 (same day, real re-solve, not more argument):** re-solved the ACTUAL Bessa
reference point (ratio_d=.02005, ratio_pitch=.25, ratio_top_diameter=.25053, imperfection=.067 --
not the matched-cross-section proxy control used above) through `bo/oracle_circular.py`'s CURRENT
contact-enabled oracle -- the archived reference ODB (`data/idea_odbs/bessa_baseline/`) was solved
2026-07-31 via an explicitly NO-CONTACT pipeline, so this is the FIRST time the study's own
normalization anchor has been checked under the same physics D42 was. sbatch job 5420896, separate
allocation; raw ODB/results archived at `data/idea_odbs/20260827_bessa_point_contact_resolve/`
(the sbatch wrapper itself misreported this job as FAILED -- the Abaqus solve completed cleanly
regardless; see that directory's own PROVENANCE.txt).
sigma_peak=0.112199 kPa -- matches the archived no-contact figure to 6 significant figures;
contact changes nothing about the reference floor's own headline number. CPRESS extracted
read-only at all 63 Riks frames: **exactly 0.0 at every frame** -- the Bessa point never touches
the disc, anywhere in its compression history. Full sigma-vs-mcs shape (from the same results.pkl):
peaks EARLY at mcs&asymp;13-18% (&sigma;&asymp;0.1120 kPa), then decays MONOTONICALLY to near-zero
(&sigma;&asymp;0.003 kPa) by mcs&asymp;98-101% -- the opposite shape from D42's late, contact-driven
rise, and consistent with (stronger evidence than, since this is the literal anchor, not a proxy)
the matched-cross-section ablation control's own early-peak-then-fade behavior already documented
above. **The caveat is resolved, not just scoped**: the reference floor does not do what D42 does.
D42's contact-driven late rise is a genuinely distinct channel, not a re-discovery of a property
Bessa's own design already has. `novel:` promoted from an unqualified assertion to a directly
tested one -- see the Stats bullet's own novel: line and the main Verdict above, both updated.

PS &sect;6 self-check (2026-08-26): this family uses `RectangularProfile` (not circular) — the
SAME profile type &sect;6 flags for the D24 splice, where the rectangular cross-section quietly
cleared the bar with the "new" component contributing nothing. Re-running the ablation's own
COPEN (contact-gap) and &sigma; fields frame-by-frame settles that this is not the same pattern,
but not for the reason first written here (corrected same day): the control does NOT sit near
zero throughout. It has a normal early elastic peak at mcs&asymp;6% reaching &sigma;=0.119 kPa
(1.06&times; Bessa) — matching this slide's own cited "incumbent floor (1.06&times;)" almost
exactly — then decays smoothly and monotonically to near-zero by mcs&asymp;100%, the same
coiling-then-fading response every straight-centerline family in this study shows. Its contact
gap closes from 2.033mm (t=0) to only ~1.05mm by its own solve's deepest frame (mcs&asymp;100-102%),
never reaching the disc — so it never gets the SECOND, contact-driven rise the serpentine gets
(gap starts closing by mcs&asymp;64%, fully closed by mcs&asymp;90%, driving &sigma; to 5.76&times;).
The corrected mechanism: the wave doesn't create load-bearing capacity where none existed — the
rectangular cross-section alone already reaches the incumbent floor early — it adds a late,
contact-driven SECOND event on top of that same baseline response. Removing the wave leaves the
early peak intact but forfeits the late one; it is not riding along on the cross-section the way
D24's splice rode along on its baseline, since the floor-clearing peak is common to both and the
2&times;-Bessa-clearing margin is entirely the late event's own.

MESH-REFINEMENT CHECK (2026-08-26, deck audit item 3 — offered twice earlier this session,
run for real this time). Same design, same protocol as the Kresling mesh study: baseline mesh
(divisor 300, matching the archived winner) vs. 2&times; (600) vs. 4&times; (1200), re-solved
from scratch since the original winner's raw ODB no longer exists on scratch.

    divisor   sigma_win (kPa)   mcs_win   max_local_strain (raw, unwindowed)
    300           0.6463         0.9286        0.05007
    600           0.5729         0.9260        0.05010
    1200          did not converge ("TOO MANY ATTEMPTS") -- same failure mode as Kresling's own 4x

sigma_peak (the actual headline metric) drops 11.4% under 2&times; refinement -- real, not noise,
and larger than it looks against a 5.76&times;-Bessa headline. mcs_win is stable (-0.3%). The raw
max_local_strain scalar is essentially perfectly converged (+0.06%) -- so the strain reading
itself is fine; it's specifically the contact-pressure-driven sigma_peak that is mesh-sensitive,
consistent with it coming from a late, sharp CPRESS spike rather than a smooth bending response.
Unlike Kresling, there is no known geometric singularity here to explain it, and unlike Kresling
there is no 3rd point: 4x fails to solve, so whether sigma_peak is settling toward a stable value
or still drifting is UNRESOLVED, not ruled out. This does not overturn the existence claim -- even
the 2x-refined value (0.5729 kPa = 5.11x Bessa) clears both the 2x-Bessa target and the incumbent
floor comfortably -- but the precise headline multiplier (5.76x) should be read as accurate to
roughly +-1 significant figure, not to 3, until a solver that can push past 2x refinement (finer
local seeding near the contact patch specifically, rather than a uniform global divisor, is the
likely next step) settles it.

**Timeline:**
D001: literature review — found and distinguished the Shi et al. 2024 precedent from D19's
already-closed meander family.
D003: oracle build (bo/oracle_serpentine.py) + the local-radius-of-curvature slenderness gate
(bo/prefilter.py) needed for a wavy, not just straight, member.
D005: seed campaign (H3/H1) — 15 feasible, best 0.5639 kPa.
D008: extended-box campaign (H6) — 36 new feasible, winning point 0.6460 kPa.
D009/D011: imperfection-robustness studies (H7/H8) — 8 and 9 independent draws.
D012: peak-strain-location check (H9) — confirmed mid-span, not joint.
Advisor session (2026-08-26, post-run): direct ablation (amplitude_rel&rarr;0 control, identical
cross-section/pitch, re-solved via bo/oracle_serpentine.py's own evaluate()) plus a CPRESS trace
on both ODBs — disproved the run's own bend-twist claim and the generic-squish alternative,
identified real disc-contact engagement as the actual cause of the late-compression rise.

**Infra:** bo/oracle_serpentine.py (Stage-1/Stage-2 dispatch, windowed_metrics reduction, plus a
serpentine_out_of_plane_fraction diagnostic that checks whether the bend-twist mode actually
engages), scripts/supercompressible_lin_buckle_serpentine.py,
scripts/supercompressible_riks_serpentine.py, scripts/supercompressible_riks_serpentine_pp.py.
ODB: /oscar/scratch/eaguerov/sc_oracle_serpentine/riks_47facf20e3c342b692ebe3c32272f997/ (D008's
own winning design — the run's own headline point, not a no-winner-convention "typical" pick,
since this idea's own Result bullet already headlines this specific number).
-->

---
class: summary-slide
---

# Run `20260825T012642` — summary

<div class="text-sm leading-snug">

This run's one new mechanism (chiral twist-buckling) hit a bounded negative — the actual headline
came from re-testing an OLD backlog idea (D24) under the run's own contact oracle, closing a
comparability caveat that idea's slide had left open since 2026-08-18.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Literature has &ge;1 untried mechanism escaping the curvature cap | &#10003; | Fang et al. 2025 chiral twist-buckling | — |
| H2 | Oracle-wiring reconfirm | &#10003; | 0.02% deviation | — |
| H3 | Twist-buckling mast escapes the curvature cap | **&#8253;** | Bounded negative — twist fraction 4400&times; below the "dominant" bar, worsening not plateauing | D41 &rarr; |
| H4 | Locking top-ring rotation forces rod-level twist instead | **&#8253;** | Confounded gate + a direct literature contradiction | — |
| H5 | D24's exact original point still clears, under the current oracle | **&#8253;** | Reconfirmed (4.68&times;) — but its own wording turned unfixably ambiguous mid-campaign | D24-2 &rarr; |
| H6 | A refined "Rank-3" candidate clears the floor | &#10003; | Median 1.6487 kPa, 9 draws (7.35&times;) — a genuine severe test | D24-2 &rarr; |

**H6, not H3, is this run's real result** — reconfirming an old idea under a newer oracle is
exactly the kind of result rule 1 asks this deck to carry, not discard.
&nbsp;·&nbsp; **13 delegations, 97 ledgered evals, 10.3 h of 12 h**, GATED after 8 review rounds

 &nbsp;&middot;&nbsp; **Cost: $48.67**
</div>

<!--
THE GATE HISTORY, IN BRIEF (8 rounds, full detail on the D24-revisited slide that follows).
Every round found something real and checkable: a duplicate-row/median miscount, an overstated
strain-floor claim contradicted by rows inside the same population it described, an 8/10-vs-7/10
feasible overclaim off by exactly the row the same paragraph flags as infeasible, and a
gate-pass audit note that lagged 3 edit rounds before catching up to the file it described. None
touched the headline number itself — call_008 independently re-derived it to 6 decimal places
from a fresh ledger query and found no residual finding.

THE LEDGER-UNDERCOUNTING DISCOVERY, THIS RUN'S REAL INFRASTRUCTURE FINDING. Four delegations
(D008, D010, D011/D012, D013) independently rediscovered the same root cause: this study's own
`OracleDataGenerator.execute()` (bo/datagen.py) records a per-call `imperfection` value only as
an OUTPUT annotation (`_imperfection_rad`), never as a declared input — so a3dasm's dedup-on-write
(which correctly keys on whatever's in `_input_data`, and is NOT itself buggy) cannot distinguish
two imperfection draws at the same nominal geometry and silently keeps only the first. D014 alone
disclosed 28 real Abaqus invocations behind just 11 ledgered rows. Root-caused and documented in
`docs/TRAPS.md` #9. **FIXED 2026-08-25 (later the same day, post-run):** `_imperfection_rad` now
stores `which="input"` when a real value is given (never for the non-sampling `imp=None` case —
a NaN there would break dedup for every other oracle, since NaN != NaN defeats the dedup key).
Self-tested, applied to all 3 call sites, committed.

A SECOND, SMALLER CAPABILITY GAP (RESOLVED, NO ACTION): no tool exists to revise a hypothesis's
own registered `prediction`/`falsification_criterion` text after proposal. Considered adding one
— rejected on review: it would let a hypothesis's wording be adjusted after seeing which evidence
is favorable, which is goalpost-moving by another name. The propose-new/retract-old pattern H5→H6
already used is the correct guard, not a workaround for a missing feature. No change.

INFRA PROMOTED TO GOLD (2026-08-25, later the same day). `bo/oracle_bistable_arch.py`,
`bo/D41_oracle_twist_buckle.py`, `bo/D41_oracle_twist_buckle_locked.py` (866 lines) + 6 supporting scripts
(6339 lines), all built fresh this run, committed so the next run touching either family doesn't
rebuild from scratch.

DEDUP POLICY (keep-first vs. keep-last): raised to the a3dasm maintainer. Initial take here was
that keep-last "strictly dominates" (fixes the corrected-re-run case, no-ops elsewhere) — wrong,
per the maintainer's correction: this study's Riks solves are not guaranteed deterministic (contact
+ stabilization + adaptive arc-length stepping), so a "last" call can just as easily be a flaky
partial re-solve as a genuine fix. Under non-determinism, no *implicit* default-overwrite policy
is safe in either direction — which is exactly why `supersede()` already exists as an explicit,
audit-logged action instead of an automatic one. Not fixed here; a3dasm's write invariants are
the maintainer's call, correctly.

COST RECONCILIATION. telemetry/summary.json recorded $46.71 total, with an EMPTY strategizer
entry in by_role (this run's strategizer transcript cost is entirely absent from that file, not
merely undercounted). Summing directly from debug/transcripts/strategizer/*.jsonl gives $1.96.
Actual: $46.71 + $1.96 = $48.67.
-->

---
layout: two-cols-header
class: idea-slide
---

# D41 &middot; <u>Chiral twist-buckling mast</u>

::left::

<div class="text-sm leading-snug">

- **What:** 6 rods set at an ANGLE to the mast's axis (not straight/axial), deliberately
  thickened past this study's usual cross-section, so rod-level TORSIONAL buckling competes with
  the bending-dominated coiling every straight-longeron family inherits — the question is whether
  each ROD twists about its OWN axis, independent of the rings' own relative rotation.
- **Origin:** Fang et al. (2025), *Nature* 639 — torsional strain energy scales ~8&times; more
  favorably with stress than bending, decoupling load capacity from every family's curvature cap.
  Thickened deliberately: a slender rod buckles in bending first, so torsion can't compete unless
  the bending threshold rises faster than the torsional one.
- **Stats:** n=20 &rarr; 8 coil &rarr; 6 riks &rarr; 0 good
  p50/p90/p100 — &sigma;_crit: 2.72/11.15/12.19 · mcs: .164/.221/.225 · mls: .053/.079/.080
  cleared: 6 of 6 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes
  best good: none (0/20 passed every criterion)
- **Verdict:** UNDERPOWERED · FERTILE-PARAMETRIC · joint decoupling<br>
  Bounded negative, not absence: twist_energy_fraction (rod TWIST share of strain energy) peaked
  at 1.13e-4 — 4400&times; below the 50% a twist-dominated design needs — and got WORSE toward
  Fang's preferred aspect ratio. Cause: the joint ties each rod's twist rigidly to the ring's
  bulk rotation, so every design is an ordinary bending collapse wearing a thickened, angled rod.
  mls sits 3-4&times; the usual ceiling: these rods are the thickest tested.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 430px">
  <div class="flex items-center justify-center" style="height: 150px">
    <img src="/gifs/D41_twist_buckle_mini.png" style="max-height: 150px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D41_twist_buckle_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">twist_angle=30&deg;: still an ordinary bending collapse, not twist-dominated.</div>
</div>

<!--
**Input space:** twist_angle&isin;[.035,1.05] rad (2&deg;-60&deg;, chirality pre-rotation angle
&alpha;&#8320;). ratio_pitch&isin;[.5,1.5]. ratio_a, ratio_b&isin;[.021,.075] — rod cross-section
(elliptical/RectangularProfile substitute for Abaqus's missing native ellipse). Fixed for this
diagnostic: n_longerons=6, ratio_top_diameter=0 (R1&asymp;R2, matching Fang et al.'s own stated
preference), ratio_shear_modulus=.3677, young_modulus=3500 MPa.

**Seed:** FERTILE — the identified confound (rod torsional DOF wrongly coupled to bulk ring
rotation) is a specific, named, untried fix, not a vague "try more parameters": decouple the
joint so each rod can genuinely twist independently of the ring's own rigid-body rotation, then
re-test whether twist_energy_fraction actually rises toward the paper's own regime.

**Deferred:** This is explicitly a BOUNDED diagnostic screening (21 evals total), not
the pre-registered ~60&ndash;100-eval falsification campaign — NOT a budget shortfall (this
study's runs carry no fixed per-hypothesis eval-count budget; only a whole-run WALL-CLOCK cap,
and this run closed with budget still unspent elsewhere). The strategizer's own judgment call:
the effect was WORSENING, not plateauing, as the aspect ratio moved toward the mechanism's own
preferred regime — a clean, converging bounded negative, decisive enough not to spend more evals
re-testing the same confounded joint-coupling realization rather than fixing the joint itself.

**Timeline:** This is H3 (free rotation, the true mechanism) + H4 (rotation-locked
control) of run `20260825T012642`, delegations D003 (oracle build) + D004 (12-point
grid: ratio_pitch&isin;{0.5,0.8}, slenderness=12, twist 2&ndash;60&deg;) + D005
(8-point grid at ratio_pitch=1.50, the domain's max and the low end of Fang et al.'s
own preferred h0/R=3&ndash;6 regime) + D006 (H4's single diagnostic sample + the
literature check that closed it). H4 was briefly FALSIFIED, then corrected to
INCONCLUSIVE per a Duhem-Quine confound: the legacy coilability gate checks exactly
the top-RP ur3 DOF H4 locked to zero, so it reads 0 by construction regardless of
whether rod-local twist buckling occurs, and Stage 2 (where twist_energy_fraction is
actually measured) was never reached on H4's own single sample. The independent
literature argument stands regardless: Fang et al.'s Extended Data Fig. 7/10
explicitly labels the locked/non-rotatable BC their own "nonchiral" comparison case,
producing ordinary bending, not more twist.

**Infra:** GIF: native Abaqus/CAE Viewer export, standard pipeline. The design shown
(twist_energy_fraction=1.13e-4, this campaign's own ceiling) is the closest any tested
point came to the hypothesized mode — visibly an ordinary coiling collapse, not
visibly "twisting," consistent with the numeric finding.
-->

---
class: idea-slide
layout: two-cols-header
---

# D24-2 &middot; Rank-3, reconfirmed under contact

::left::
<div class="text-sm leading-snug">

- **What:** D24's splice re-migrated to ground+top-disc contact; optimum reconfirmed, and a
  refined search found a new candidate ("Rank-3"), imperfection-tested (Bessa's own
  lognormal(4&deg;,1.2&deg;), 3 seeds).
- **Origin:** D24's own slide flagged its headline as never re-measured under contact — this
  closes that gap.
- **Stats:** n=1 candidate (Rank-3), imperfection-sampled (19 draws). Fine-mesh re-solve
  (250&times; tighter, job 5410570): the draw behind the cited 1.6487 kPa median does NOT
  converge; the default draw resolves instead to &sigma;=0.5039 kPa at mcs=5.46% (Rank-1
  companion check reproduces the pattern: 3.775&rarr;0.597 kPa).<br>
  cleared: coarse draw invalid; fine-res draw (0.5039) clears 2&times; Bessa but sits below
  the incumbent's real peak (0.6071) &middot; novel: yes, new position — see Verdict.
- **Verdict:** POWERED &middot; FERTILE-PARAMETRIC &middot; Q&ge;2.31 targeting<br>
  The cited 1.6487 kPa spike is a numerical artifact — re-solved 250&times; finer, it does
  not converge; the default draw resolves to 0.5039 kPa, below the incumbent's real peak.
  Existence claim stands; the splice doesn't help, and per Seed below not even a genuine
  snap is confirmed anywhere in this family — full revision history in notes.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 430px">
  <div class="flex items-center justify-center" style="height: 150px">
    <img src="/gifs/D24-2_rank3_coarse_vs_fine_full_mini.png" style="max-height: 150px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D24-2_bistable_arch_rank3_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Coarse vs fine-grid overlay; converged design below.</div>
</div>

<!--
**Input space:** Rank-3 candidate geometry: ratio_a=.009179, ratio_b=.029742,
arch_rise_ratio=.021174, arch_length_ratio=.400188, ratio_pitch=.669962,
ratio_top_diameter=.041530. Imperfection sampled from Bessa's lognormal(4&deg;,1.2&deg;)
distribution, seeds 0/1/2 across D010/D013/D014.

**Result, full revision history (trimmed from the visible bullet 2026-08-28 to fix a confirmed
134px render clip, headless-measured):** median &sigma;_peak=1.6487 kPa across 9 independent
draws (7.35&times; the floor) clears every criterion — but this number is the
imperfection-sensitive snap-through spike at mcs&asymp;0.1&ndash;0.5% of compression, not a
sustained load. **Revised 2026-08-25 (see PROBLEM_STATEMENT.md &sect;6):** the design's own
sustained post-snap capacity (&asymp;0.51&ndash;0.52 kPa, stable across draws) sits below the
plain rectangle incumbent's own real peak (0.6071 kPa) — the splice actively hurts once the
spike is set aside. **Revised 2026-08-27 (advisor request, a real finer-resolution re-solve, not
a re-read):** the 1.6487 kPa spike itself is a NUMERICAL ARTIFACT — re-solved 250&times; finer,
the exact draw behind it does not even converge, and Rank-3's own default-imperfection draw
resolves to a smooth 0.5039 kPa peak, not a spike, right at the sustained-plateau value already
cited above. Existence claim stands; the mechanism does not help; the headline number was never
real to begin with.

**Comparability argument in full (trimmed from the visible Result bullet):** same E, same
beam/contact physics as the incumbent; stab_ratio&asymp;0.002 rules out an artificial-damping or
prestress confound; the metric's own "max over the whole compression window" rule is applied
identically to every family in this study, not specially loosened here. **Corrected 2026-08-27:**
the claim that follows this sentence historically said "the raw 1.6487 kPa number is real and not
an artifact" — that is now known WRONG, superseded by the 2026-08-27 finegrid re-solve below: the
number is specifically a numerical (increment-size) artifact. The comparability argument itself
(same E, same physics, same windowing rule) still holds; it just isn't evidence the SPIKE was
real, only that the metric wasn't being applied unfairly to this family.

**RESOLVED 2026-08-25 (advisor session, direct ODB re-extraction):** the early-transient-snap
caveat above is no longer an open question. Plotting the design's own real sigma-vs-mcs Riks
history (windowed_metrics(), not a paraphrase) across the D010/D013/D014 imperfection draws shows
the 1.6487 kPa figure is a 1-2 sample spike at mcs&asymp;0.13%, and the *sustained* post-snap
plateau (&asymp;0.51&ndash;0.52 kPa, stable across independent draws) is below run17_rectangle's own
confirmed real peak (0.6071 kPa, `bo/confirmed_anchors.json`). So: does splicing pull its weight
here? No — the design clears the numeric bar only because of the spike, and the spliced arch's
own sustained contribution is *negative* relative to the unmodified host. This is the worked
example behind PROBLEM_STATEMENT.md's Lessons-learned &sect;6 ("a strong baseline in disguise").
The existence claim (a 5-criteria-feasible design was found) still stands; the "genuinely
interesting new mechanism" claim does not.

**RESOLVED 2026-08-27 (advisor session — "is the peak truly physical or a numerical
artifact?", answered with a REAL finer-resolution re-solve, not a re-read of prior
output):** the spike is a NUMERICAL ARTIFACT, not a real transient. Root cause: this
family always solves Stage 2 as a general static step with automatic stabilization
(`bo/oracle_bistable_arch.py` sets `stabilization=True` unconditionally), and the
pre-processor's `initialInc=5e-3` sizes the FIRST increment of the whole step at 0.5%
of the compression stroke — the same order of magnitude as the entire reported spike
window (mcs&asymp;0.1&ndash;0.5%). Re-solved Rank-1 and Rank-3 on a separate sbatch
allocation (job 5410570, `mbessa-condo`) with a one-line fork of the pre-processor
(`initialInc` tightened 250&times;, 5e-3&rarr;2e-5), same designs, same imperfection
draws already on record. Three results, all real Abaqus output:
  1. The EXACT draw behind the cited 1.6487 kPa figure (D014 "rank3_fresh_draw6",
     imperfection=0.05920295568871166 rad) DOES NOT CONVERGE at fine resolution —
     Abaqus's own `.msg`: "TOO MANY ATTEMPTS MADE FOR THIS INCREMENT." The original
     coarse solve's "successful" 1.6487 kPa reading came from an increment large enough
     to step past a region the solver cannot actually resolve.
  2. Rank-3's own default-imperfection draw (0.067 rad, on-record 1.592 kPa "spike")
     DOES converge once resolved: sigma_peak drops to **0.5039 kPa at mcs=5.46%** (not
     0.125%) — 34 real per-increment points inside mcs&le;2% trace a smooth,
     monotonically RISING curve with no local peak anywhere; the resolved value lands
     almost exactly on the sustained 0.51&ndash;0.52 kPa plateau already reported above.
  3. Rank-1 (same D011 campaign, its own #1 candidate) reproduces the identical pattern
     at its own default imperfection: the reported 3.775 kPa spike at mcs=0.25%
     collapses to a genuine, monotonic **0.597 kPa peak at mcs=5.35%** once resolved.
  **SUPERSEDED 2026-08-27 (same day, consolidated per advisor review):** this originally
  pointed at a separate early-region-only zoom chart, stacked as a 3rd panel above the
  slide's own pre-existing full-range plot. Both prior images
  (`/gifs/D24-2_rank3_sigma_mcs_mini.png`, `/gifs/D24-2_rank3_finegrid_earlyregion_mini.png`) are kept
  on disk, unreferenced, not deleted — replaced by one consolidated full-range chart,
  `/gifs/D24-2_rank3_coarse_vs_fine_full_mini.png`, coarse (dashed) vs fine-grid (solid)
  overlaid across the ENTIRE compression history (0-100%+ mcs), same
  design+imperfection pair, same data sources as below. The full-range view makes the
  finding visually undeniable in a way the zoom-only chart couldn't: the coarse curve's
  one high point near mcs=0 is a single, isolated outlier — every other point on both
  curves, across the rest of the entire solve, tracks together almost exactly.
  **Raw files, preserved off `/oscar/scratch` per the advisor's explicit request** (full
  ODB/.inp/.dat/.msg/.sta/results.pkl for every re-solve, each directory with its own
  `PROVENANCE.txt`): `data/idea_odbs/20260827_D24revisited_finegrid_rank3_draw6_
  nonconvergent/` (the non-convergent case), `.../20260827_D24revisited_finegrid_rank3_
  default_0.067rad/`, `.../20260827_D24revisited_finegrid_rank1_default_0.067rad/`,
  `.../20260827_D24revisited_finegrid_rank1_zero_imperfection/` (secondary check only —
  stab_ratio=0.100 fails the family's own 0.05 gate, not read as evidence on the 1.6487
  kPa question, see its own PROVENANCE.txt). The two ORIGINAL coarse ODBs (still on
  scratch, archived here before they could be purged) that this finding is measured
  against: `.../20260825_D24revisited_rank3_draw6_1.6487kpa_ORIGINAL_COARSE/`,
  `.../20260825_D24revisited_rank3_default_0.067rad_ORIGINAL_COARSE/` (plus Rank-1's own,
  `.../20260825_D24revisited_rank1_default_0.067rad_ORIGINAL_COARSE/`). Finegrid
  pre-processor: `scripts/supercompressible_riks_bistable_arch_contact_finegrid.py` (a
  one-line fork of the gold `..._contact.py`, NOT promoted to gold — a diagnostic, not
  an infra change). Driver script, full per-increment curves (JSON), and the chart
  script: `data/idea_odbs/SUMMARY_20260827_finegrid_investigation.json` /
  `..._driver.py` / `..._earlyregion_chart_script.py`.
  **This sharpens the slide's own claim, not just this note's caveat**: the "Revised
  2026-08-25" text above (median 1.6487 kPa across 9 draws) should now be read as "that
  9-draw median is itself built from spike readings a properly-resolved solve does not
  reproduce" — the honest number for this design was always close to the
  already-flagged 0.51&ndash;0.52 kPa sustained plateau, not 1.6487 kPa. Per the deck's
  append-only rule (3(d)/7(d)) the original 1.6487 kPa figure and its 2026-08-25 caveat
  are NOT deleted above; this note supersedes their reliability, not their text.

**Seed:** FERTILE, and more fundamentally than previously stated (strengthened 2026-08-27, advisor
review: "the proposed design did not achieve bistability, thus we can't say bistability itself is
uninteresting"). Checked directly against the 2026-08-27 finegrid re-solve's own `arch_snap_reversal`
field — the diagnostic this family's own oracle uses to detect a genuine two-equilibrium snap:
**both Rank-3 and Rank-1's properly-resolved solves read `arch_snap_reversal=0`** (no snap
detected at all). The ORIGINAL coarse Rank-3 solve had read `arch_snap_reversal=1` — a FALSE
POSITIVE, the same numerical artifact that produced the fake 1.6487 kPa spike also spuriously
registered a "snap" that the properly-resolved curve shows never happened. Combined with D24's
own H5 (`arch_snap_reversal_top=0`, already on that slide) and D23's explicitly sub-bistable
(Q&lt;2.31, deliberately NOT true bistable) framing, NO design tested anywhere in this family's
history has ever demonstrated a genuine two-equilibrium snap in a properly-resolved solve — so
whether bistability itself (as opposed to these specific splice/rank-optimization attempts) is an
interesting mechanism for this problem remains genuinely OPEN, not falsified. A future test would
need to deliberately target the true-bistable regime (Q&ge;2.31, per D24's own original H2/H3
framing) with a resolution tight enough to trust the snap-detection field, not just the stress
reading. H5 (D24's own original exact point) separately never reached a clean close because its
own registered wording became ambiguous mid-campaign, not because the physics ran out; a fresh
hypothesis re-registering that exact original point with unambiguous wording (and the tightened
initialInc this session's re-solve validated) would settle it without guessing at settings again.

Full campaign detail:

- D008 (namespace migration + D24 base-point reconfirm): re-migrated the bistable-arch
  pre-processor to ground+top-disc contact (never committed to gold after the family's original
  build in an earlier run — this run had to rebuild it from scratch); the original D24 optimum
  reconfirmed feasible at &sigma;_peak=1.0495 kPa (4.68&times; target).
- D011 (46-eval BO campaign, ledger-traced throughout — `cei_core.run_cei_bo` used specifically
  because the study's usual `SlurmAsyncPool` path calls the oracle off-ledger): found the Rank-3
  candidate.
- D010/D012/D013/D014 (imperfection-robustness sampling, 3 independent seeds): D010 (seed=0,
  13 draws) and D013 (seed=1, 12 draws) both hit the dedup-on-write ledger gap documented in
  `docs/TRAPS.md` #9 (root-caused this run — see that file's 2026-08-25 update). D014 (seed=2,
  10 fresh draws) avoided the gap by self-reporting the true invocation count (28 real solves,
  11 ledgered) rather than trusting the ledger. Median computed from the 11 ledgered
  Rank-3-geometry rows, de-duplicated to 9 genuinely independent draws (2 bit-identical pairs
  removed — D011/D012 both re-solved the exact default-imperfection point, and D014 logged one
  draw twice).
- Gate history: 8 review rounds, every one finding a real, checkable defect (never a false
  positive) — a duplicate-row/median miscount (1.5921&rarr;1.6487 kPa once both pairs were
  correctly excluded), an overstated "every one of 32 sits at 95%+" strain claim contradicted by
  rows inside that same 32, an 8/10-vs-7/10-feasible overclaim off by the exact ring-passthrough
  row the same paragraph flags, and a stale gate-pass audit note that lagged 3 edit rounds before
  catching up. None touched the headline number itself.
- Infra not yet promoted to gold: `bo/oracle_bistable_arch.py`, `bo/D41_oracle_twist_buckle.py`,
  `bo/D41_oracle_twist_buckle_locked.py` + 6 supporting scripts, built fresh this run. Recommend
  committing so the next run testing either family doesn't rebuild working,
  adversarially-verified infrastructure from scratch.
- GIF: native Abaqus/CAE Viewer export, standard pipeline. The Rank-3 candidate at its own
  median-draw imperfection realization, matching the headline number exactly, not a cherry-picked
  best-of-9.
-->

---
class: summary-slide
---

# Run `20260823T161229` — summary

<div class="text-sm leading-snug">

Four continuous-shell/ring mechanisms died to local buckling beating global coiling, before
the run pivoted to a discrete-member idea that didn't.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Self-contact jamming escapes the depth cap | re-tread | already attempted twice (D31, D33) | — |
| H2 | Staged two-storey mast (upper bears on landed lower) | re-tread | attempted 5+ times before (D34 + H2/H12/H4) | — |
| H3 | Kirigami-cut shell wall distributes rotation over many ligaments | **&#8253;** | 0/51 Stage-1 coilable, two draws; top designs cluster at range edges | D36 &rarr; |
| H4 | Compliant kirigami-cut top ring lets ring radius grow favorably | **&#10007;** | shrinking dominates growing 14:3; near-miss has an essentially flat radius | D37 &rarr; |
| H5 | Helically-graded shell thickness reshapes the strain integral | **&#8253;** | 0/24 coilable; twist phase moves rotation non-monotonically | D38 &rarr; |
| H6 | Nested double-wall with engaging backing collar raises stiffness | **&#10007;** | 0/5 coilable; more engagement doesn't even help monotonically | D39 &rarr; |
| H7 | Crosslinked beam bundle generates bundle-level torque coupling | **&#8253;** | preserves global coiling (unlike all 4 shells); 22&times; buckling-capacity gain; best mcs=0.7191 | D40 &rarr; |

**No mechanism cleared the incumbent (0.6077 kPa); H7 is the strongest near-miss** — the only
one preserving global coiling, within 9 pts of the bar.
&nbsp;·&nbsp; **22 delegations, 227 evals, 5 namespaces, 10.8/12 h, GATED**
&nbsp;&middot;&nbsp; **Cost: $86.10**
</div>

<!--
THE GATE HISTORY. Call 1: REJECT -- closing on a negative result with real wall-clock budget
still unspent, a CRITICAL finding per PROBLEM_STATEMENT.md's own explicit critic instruction
(independent of an otherwise-clean reproducibility gate). Call 2: REJECT again -- same charter
defect in fact pattern even though the specific H7 sub-question flagged last time had since been
properly, severely tested; told to either run the two named untested H7 axes or open a fresh
mechanism with the ~1.6h remaining. Call 3: PASS -- both defects resolved with real, checkable
ledger evidence (D021/D022), and the remaining budget (~10%) was correctly judged insufficient to
responsibly ground and test a fresh mechanism from scratch.

THE H7 INVESTIGATION, IN FULL (D014-D022, by far the largest share of this run's budget). D014
validated the mechanism on one sample + its N=0 (uncoupled) control: crosslinking 3 unbraced,
slender sub-beams recovers a 22x eigenvalue increase over uncoupled (rigid) / 19x (soft), reaching
~76% of an equivalent solid single-beam's own eigenvalue at matched envelope -- and critically,
the LOWEST vibration mode stayed the coherent global coiling mode in every configuration, unlike
every shell family this run tried. D015 (34-design campaign) found Stage-2 converged for only a
minority, with a genuine "hard local instability" signature at higher crosslink counts. D016-D018
isolated the cause via two independently-different crosslink realizations (a meshed beam-link
batten vs. a genuine rigid kinematic *CONNECTOR with no meshed geometry) and a soft-vs-rigid
stiffness sweep -- both point to the SAME instability, ruling out a meshing artifact. D019
(27-design campaign restricted to n_crosslinks in {0,1}, re-examining D015's own data) found the
hard-instability pattern does NOT afflict low-crosslink-count designs, and reached mcs=0.7173 --
a genuine Riks snap-through plateau, not a wall-clock artifact (confirmed via an extended
solve-budget check), with max_local_strain never binding (best 0.003 against the 0.02 cap). D020
(10-point local refinement) confirmed this is a real local optimum (mcs=0.7191) and flagged two
untested directions. D021 (14-point decisive grid probe) found pushing FURTHER in both flagged
directions makes it WORSE, falsifying the "push further" hypothesis rather than confirming it.
D022 closed the two remaining named axes (soft connector stiffness at n_crosslinks=1; n_sub_beams=3)
-- both collapse catastrophically via early Riks divergence, a qualitatively different failure mode
than D020's near-0.72 salvages, confirming n_sub_beams=2/rigid is not merely a local optimum on
that axis but structurally the winning configuration.

WHY H4's NEAR-MISS DOESN'T RESCUE H4. D007's idx=15 design (mcs=0.7885, mls=0.01976, both just
under their bars) is numerically the closest ANY design got to feasibility this run -- closer than
H7's own 0.7191. But its ring radius barely moved (+0.0026%), the opposite of what H4 predicts
(a favorably GROWING ring radius). It is a good geometry point on the compliant_ring family's own
parameter space, not evidence for the hypothesized mechanism -- H4 is correctly FALSIFIED as a
mechanism even though it produced the run's numerically-closest single design.

TWO REAL INFRA BUGS SURFACED, NEITHER FIXED HERE (both in the vendored a3dasm harness, not this
repo). `bo/campaign_summary.py`'s `decided_key` default reads a definitive Stage-1 "not coilable"
verdict as "no verdict reached" for two-stage families, producing a false "nothing to summarise"
on a fully-decided campaign (D006). `InstrumentedDataGenerator`'s dedup-on-write can silently drop
a corrected re-run under the same delegation ID (D018) -- same class of danger as the
`SlurmAsyncPool` discard-on-timeout bug already in `docs/TRAPS.md` #8; now also #9 there.

A PRE-EXISTING DOC/CODE MISMATCH, ALSO NOT FIXED HERE. `bo/prefilter.py`'s `THINNESS_FLOOR=10.0`
does not match several of these new families' own generator docstrings, which assert/document a
>=20 thin-shell-validity floor (D008's retrospective). Which value is scientifically correct is a
physics-validity judgment call, not picked here.
-->

---
class: idea-slide
layout: two-cols-header
---

# D36 &middot; Kirigami-cut continuous shell wall

::left::
<div class="text-sm leading-snug">

- **What:** discrete straight longerons replaced by ONE continuous, periodically-cut PLA shell
  wall — cut length `l`, ligament width `delta`, shell thickness `t_shell` free; ring radii fixed
  to the study's standard envelope.
- **Origin:** kirigami-cut shell metamaterials literature (cut networks that buckle/snap
  out-of-plane at each ligament) — the idea being that many independent ligament rotations absorb
  the ring's rotation-descent demand instead of one beam's curvature.
- **Stats:** n=51 &rarr; 0 coil &rarr; 0 riks &rarr; 0 good
  quartiles unavailable — zero designs this run reached Stage-1 coilability, under two
  independent draws (D006 Sobol screen + D008 packing-fix top-up)
  cleared: none (0 decided) &middot; novel: untested — the mechanism never got to demonstrate
  anything
  best good: none (0/51 passed every criterion)
- **Verdict:** POWERED &middot; UNKNOWN-NO-EVIDENCE &middot; panel-vs-global mode competition<br>
  Every design's lowest vibration mode is a local ligament/panel buckling mode, not the global
  ring-driven coiling mode the study needs — a qualitatively different failure from the earlier
  smooth chiral-shell family's uniform lateral sway, but the same outcome: the cuts avoided one
  failure mode and fell into another. **Corrected (2026-08-31, verdict audit): this previously
  read FERTILE-PARAMETRIC, contradicting this slide's own Seed — every direction tried so far
  made the failure worse, not better, so a wider box is untested, not promising.**

</div>

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/gifs/D36_kirigami_shell_negative_native.gif" class="max-h-72 rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-2 px-4 text-center">Stage-1 lowest mode; no Stage 2 ran.</div>
</div>

<!--
**Input space:** l&isin;[1,300] — cut length (mm) of each kirigami slit. delta&isin;[1,50] —
ligament width between adjacent cuts. t_shell&isin;[.3,3.5] — shell wall thickness.
helical_twist_total&isin;[0,2&pi;] — total helical twist applied across the shell's height.
ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.6] — usual per-storey pitch/taper
meaning from every other family. Fixed: ring radii held at the study's standard envelope.

**Seed:** BARREN as tested — top designs cluster at the sampled box's own edges, so a wider box
is FERTILE in principle, but every direction tried so far makes local buckling worse, not
better, giving no reason to expect it reverses just outside the tested range.

**Timeline:**
- D004: single-sample validation — mechanism builds and solves cleanly, 14-25s/solve.
- D006 (36 drawn, 24 valid Stage-1 verdicts): Sobol screen.
- D008 (30 drawn, 27 valid): packing-fix top-up, meeting H3's registered ~40-80 campaign scale.

**Infra:** bo/prefilter.py:passes_kirigami_ligament (r0_min/t_shell&ge;10, delta/t_shell&ge;3,
l/delta&ge;2). scripts/supercompressible_{lin_buckle,riks}_kirigami_shell.py.
-->

---
class: idea-slide
layout: two-cols-header
---

# D37 &middot; Compliant kirigami-cut top ring

::left::
<div class="text-sm leading-snug">

- **What:** Bessa's rigid 0-D top ring replaced by an elastically-buckling, kirigami-cut annular
  shell — ring cut length, ligament width, thickness, and radial width free; longeron geometry
  unchanged from the matched circular-family control.
- **Origin:** same kirigami-cut shell grounding as D36, applied to the ring rather than the
  longerons — letting the effective ring radius evolve during compression instead of staying
  fixed.
- **Stats:** n=36 &rarr; 28 coil &rarr; 1 riks &rarr; 0 good
  quartiles unavailable — only 1/28 reached strict full convergence (LPF=1.0), but 22/28 MORE
  stopped early with enough real, usable data to read a ring-radius trajectory from (23 usable
  total feeding the Verdict below) — 5/28 produced nothing usable at all
  cleared: none (0 decided) &middot; novel: untested — the one converged design didn't test the
  hypothesized direction
  best good: none (0/36 passed every criterion; closest was mcs=0.7885, mls=0.01976, disqualified
  on mcs)
- **Verdict:** POWERED &middot; REFUTED &middot; ring-radius growth<br>
  Ring radius shrinks in 14 of 23 usable trajectories vs. 3 that grow — the unfavorable,
  strain-tightening direction dominates 3:1. The one dramatic growing outlier (+163%) is a real
  ring self-buckling event, but it happens at only 5.3% compression — an early failure, not a
  pathway to more. No design's &sigma;_peak exceeds its matched rigid-ring control.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D37_compliant_ring_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 265px">
    <img src="/gifs/D37_compliant_ring_landscape.gif" class="rounded shadow-lg" style="max-height: 265px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Best design (mcs=0.7885); real kirigami ring shown, not schematic.</div>
</div>

<!--
**Input space:** t_ring&isin;[.3,1.5] — ring shell thickness. w_ring&isin;[8,25] — ring radial
width. delta_ring&isin;[1.5,5] — ligament width between ring cuts. l_ring&isin;[3,15] — ring cut
length. margin_frac_ring&isin;[.10,.25] — safety margin fraction on the ring's own geometric
limits. ratio_d&isin;[.004,.073], ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] —
usual longeron/pitch/taper meaning, matched to the circular-family control. Fixed:
n_longerons&isin;{3,4,5,6} (categorical, searched).

**Seed:** BARREN as a ring-radius-growth mechanism — the direction the hypothesis needs is a
3:1 minority outcome that itself fails early when it does occur. The one near-feasible design
found (mcs=0.7885) had a flat radius, not a growing one — worth reusing as a starting geometry
for a *different* hypothesis, not evidence this one works.

**Timeline:**
- D005: single-sample validation — Stage 1 sigma_eig=0.1238 kPa vs. the matched bessa_point
  rigid-ring control's 0.1306 kPa (-5.2%), a modest, physically-expected compliance cost.
- D007 (36 designs, 28 coilable, all auto-escalated to Stage 2): the campaign referenced in Stats.

**Infra:** bo/prefilter.py:passes_compliant_ring (adds w_ring/t_ring&ge;10 to D36's own three
gates, so the annulus doesn't degenerate into a 1-D ring/wire).
scripts/supercompressible_{lin_buckle,riks}_compliant_ring.py. ODB:
/oscar/scratch/eaguerov/supercompressible_compliant_ring_oracle/riks_cring_8aaa945e46684ffdaa8ce1bf37a8b2a6/
(the only one of 28 with a persisted results.pkl -- the rest are salvage-only reads). Rendered
2026-08-26 with SHOW_INSTANCES=RING_TOP (a real, separately-meshed 960-element shell instance,
distinct from the 0-D-point rings every other family in this study has) -- the actual kirigami-cut
ring geometry, not the schematic dashed-circle placeholder used where no ring mesh exists.
-->

---
class: idea-slide
layout: two-cols-header
---

# D38 &middot; Helically-graded shell thickness

::left::
<div class="text-sm leading-snug">

- **What:** a mass-neutral, helically-graded thickness field t(&theta;,z) over an otherwise
  UNCUT, smooth conical shell wall (a=0 collapses to the study's own uniform-shell control) —
  grading contrast `a`, rotational order `n_eff`, helical twist, phase, pitch/taper free.
- **Origin:** graded/hierarchical architected-metamaterial literature — the idea being that
  reshaping the strain-vs-compression integral via a spatially-varying wall thickness could let
  a design reach mcs&ge;0.80 within the 2% strain budget at a higher &sigma;_peak than a uniform
  wall permits.
- **Stats:** n=22 &rarr; 0 coil &rarr; 0 riks &rarr; 0 good
  quartiles unavailable — 0/22 Stage-1 coilable, so Stage 2 never auto-escalated for any design
  cleared: none (0 decided) &middot; novel: untested
  best good: none (0/22 passed every criterion)
- **Verdict:** POWERED &middot; REFUTED &middot; twist-phase magnitude<br>
  Twist phase and magnitude move the rotation signal (ur3_ratio) non-monotonically and
  asymmetrically by sign — a real, non-trivial effect (-60&deg; reaches 28&times; the plain
  reference; +60&deg; only 40&times; *below* it) — but the ceiling found (1.25e-4) sits ~400&times;
  below the 0.05 coilability threshold. The lever is real; the magnitude is nowhere close.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/gifs/D38_graded_shell_negative_native.gif" class="max-h-72 rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-2 px-4 text-center">Stage-1 lowest mode; no Stage 2 ran.</div>
</div>

<!--
**Input space:** a&isin;[.3,.5] — grading contrast (0 = uniform-shell control). n_eff&isin;[3,8]
— rotational order of the thickness field. t0&isin;[.5,3] — nominal (unmgraded) wall thickness.
helical_twist_total&isin;[-4&pi;,4&pi;] — including small-angle probes. helical_phase0&isin;[0,2&pi;]
— twist phase offset. ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.6] — usual
per-storey pitch/taper meaning.

**Seed:** BARREN in the searched box — but the twist-phase asymmetry is a genuinely
under-explored signal (only sparsely probed here) rather than a flat null; FERTILE if a future
campaign specifically maps the twist-phase/magnitude surface near its own steepest gradient
instead of the broad Sobol-style screen used here.

**Timeline:**
- D010: single-sample validation — set up the shell/grading-field construction (reusing D004's
  kirigami_shell shell-element scripting at a=0).
- D011 (22-point sweep): the campaign referenced in Stats.

**Infra:** bo/prefilter.py:passes_graded_shell (thin-shell validity evaluated at the THINNEST
nominal wall t0*(1-a), not the mean/nominal t0, plus a &ge;4-elements-per-grading-wavelength
mesh-convergence floor). scripts/supercompressible_{lin_buckle,riks}_graded_shell.py.
-->

---
class: idea-slide
layout: two-cols-header
---

# D39 &middot; Nested double-wall with engaging backing collar

::left::
<div class="text-sm leading-snug">

- **What:** an outer continuous shell wall backed by an inner collar/panel that closes a gap and
  engages via self-contact partway through compression, meant to raise effective stiffness only
  after engagement — gap `g0`, collar thickness `t_in`, engagement height/preload free.
- **Origin:** direct follow-up to D36/D38's shared failure mode — instead of cutting or grading
  the wall itself, add a second wall that only helps once contact closes, hoping to avoid the
  local-buckling competition both prior shell attempts hit.
- **Stats:** n=5 &rarr; 0 coil &rarr; 0 riks &rarr; 0 good
  quartiles unavailable — a bounded Stage-1-only diagnostic (5 configurations spanning the
  mechanism's full engagement range), not a full campaign
  cleared: none (0 decided) &middot; novel: untested
  best good: none (0/5 passed every criterion)
- **Verdict:** UNDERPOWERED &middot; REFUTED &middot; backing-panel engagement<br>
  0/5 configurations coilable; the rotation signal (ur3_ratio) stays 5-8 orders of magnitude
  below the 0.05 threshold in every case, and more backing engagement does not even
  monotonically help it — a much stronger backing panel gave a LOWER signal than a weaker one.
  The mechanism does not show up at all, let alone favorably.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/gifs/D39_nested_double_wall_negative_native.gif" class="max-h-72 rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-2 px-4 text-center">Stage-1 lowest mode; never escalated to Stage 2.</div>
</div>

<!--
**Input space:** g0&isin;[0,1] — radial gap between outer shell and inner collar before
engagement. t_in&isin;[.2,5] — collar thickness. with_backing&isin;{0,1} — control switch (0 =
D38's uncut-shell control, bit-for-bit). backing_axial_extent&isin;[.05,1] — collar height as a
fraction of the mast. preload_fraction&isin;[0,1] — optional preload feeding the *BUCKLE step.
gap_taper_frac&isin;[0,.49], soft_contact&isin;{0,1} — contact-formulation controls, not searched
this diagnostic. ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.6] — usual per-storey
pitch/taper meaning. Only 5 hand-picked configurations were run (not a DOE sweep of this box) —
see Timeline.

**Seed:** BARREN — the diagnostic deliberately bracketed the mechanism's entire viable
engagement range (collar-only through idealized-fully-engaged through a stronger idealized
case), not a sparse sample of an unbounded space, so there is no un-probed direction left to
call FERTILE.

**Timeline:**
- D012, full diagnostic table: (a) outer shell alone (sigma_eig=1372.4, reproduces D38's a=0
  control bit-for-bit) &rarr; (b1) collar-only, g0=0.05, t_in=1.0, no preload (+18.8%, ur3_ratio
  DOWN) &rarr; (c) idealised fully-engaged, g0=0.0, t_in=1.0 (+21.0%) &rarr; (e) stronger
  idealised, g0=0.0, t_in=3.0, 90% height (+204.6% eigenvalue, but ur3_ratio DOWN vs (c)) &rarr;
  (d) preload infra check, g0=0.05, preload=0.3&times;lambda_a (ur3_ratio=2.90e-7, still far
  below threshold).

**Infra:** single orphan-mesh part with a welded-edge backing panel, general self-contact
(softened, allowSeparation=ON, frictionless), general-STATIC preload feeding a *BUCKLE linear
perturbation — all ran without errors, 22-152s/job.
scripts/supercompressible_{lin_buckle,riks}_nested_double_wall.py.
-->

---
class: idea-slide
layout: two-cols-header
---

# D40 &middot; Crosslinked beam bundle

::left::
<div class="text-sm leading-snug">

- **What:** each longeron replaced by 2-3 slender B31 sub-beams on the same envelope circle, tied
  at discrete axial crosslink points.
- **Origin:** Rathore &amp; Grason 2011 — a crosslinked bundle of slender filaments carries an
  intrinsic torque an equivalent single member doesn't, because the crosslinks resist relative
  bending/twisting between sub-beams; the hope was this extra coupling raises the mast's coiling
  stiffness beyond a solid-longeron control at the same envelope diameter.
- **Stats:** n=113 &rarr; 34+27+10+14+5 (D015/D019/D020/D021/D022) &rarr; mostly Stage-1-coilable
  &rarr; 0 good
  quartiles unavailable — 0/113 Riks-converged (near-plateau reads in Verdict instead) &middot;
  cleared: 0/113 (mcs&ge;0.80) &middot; novel: **yes** — distinct from every prior family
  best good: none — best overall: mcs=0.7191 (D020) (geometry in notes' Timeline)
- **Verdict:** POWERED &middot; FERTILE-REWORK &middot; Riks convergence<br>
  Preserves genuine global coiling as the lowest mode in every configuration — unlike every
  shell/ring family this run — with a real 22&times; buckling-capacity gain over uncoupled
  sub-beams. **Corrected (2026-08-31, verdict audit): the 71.9% reading was never a real
  snap-through plateau — D40-2's two independent re-solves confirm a genuine arc-length
  divergence instead. No design in this family is confirmed to reach even that point.**

</div>

::right::

<div class="flex flex-col gap-1" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D40_crosslinked_bundle_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 265px">
    <img src="/gifs/D40_crosslinked_bundle_landscape.gif" class="rounded shadow-lg" style="max-height: 265px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Best design (D020): real stopping point 71.9% — see notes.</div>
</div>

<!--
**Animation caveat (moved from the visible caption to stay within the caption-brevity
budget):** the family's own best design (D020) stalls at 71.9% compression (mcs=0.7191),
where the solve's progress on the mode this study measures effectively ends. The animation
itself may still show the solver continuing to move past that point — frames are only
capped at a global 95% compression safety limit, not stopped at each design's own reported
number — so that later motion is not what mcs=0.7191 describes. "Converged" in this deck
means reaching the FULL compression target, which this design never does. **Corrected
(2026-08-31, verdict audit): this note previously called 71.9% "a real, physical
snap-through" and "a real, physical stopping point" — D40-2's two independent, agreeing
re-solves (job D012, 9&times; time budget) show it is a genuine arc-length divergence, a
solver wall, not a physical snap. The stall is real; the claimed mechanism behind it was
not.**

**Input space:** ratio_d&isin;[.004,.073] — sub-beam diameter relative to the envelope.
ratio_r_sub_frac&isin;[.05,.48] — how far off the main envelope circle each sub-beam sits (0 = on
the circle, larger = more spread within the local bundle footprint). ratio_pitch&isin;[.25,1.5],
ratio_top_diameter&isin;[0,.8] — usual per-storey-pitch/taper meaning from every other family.
n_sub_beams&isin;{2,3} — discrete topology choice, not a continuous dial. n_crosslinks&isin;{0,1,3,5}
— number of discrete axial tie points. crosslink_stiffness_ratio&isin;[0,1] — interpolates rigid
(1) to soft (0) connector coupling. crosslink_spacing_bias&isin;[-.9,.9] — shifts whether
crosslinks cluster toward the top/bottom of the mast or sit evenly spaced. twist_angle&isin;[0,&pi;]
— optional pretwist, same convention as D1. Fixed: n_longerons&isin;{3,4,5,6} (categorical,
searched, held constant within any one design).

**Seed:** BARREN at n_sub_beams&isin;{2,3} with this crosslink topology — both the soft
connector-stiffness axis and n_sub_beams=3 were closed decisively (catastrophic early collapse,
not a tuning shortfall). **Superseded (2026-08-31, verdict audit): the rest of this Seed
originally said "FERTILE if the snap-through itself is targeted directly" — there is no
snap-through to target (see D40-2). The real open question, per D40-2's own Seed, is
whether a different crosslink placement/spacing entirely — outside the neighborhood
re-tested there — avoids the Riks-convergence wall altogether; that, not snap-through
targeting, is this family's actual untried next step.**

**Deferred:** InstrumentedDataGenerator's dedup-on-write can silently drop a corrected re-run
under the same delegation ID (hit at D018) — same danger class as docs/TRAPS.md #8; documented
here as #9, not fixed in the vendored a3dasm harness.

**Timeline:**
- D014 (1 sample + N=0 control): validated the mechanism and the global-coiling-mode preservation.
- D015 (34 designs): found a "hard local instability" at higher crosslink counts.
- D016 (6 designs): follow-up.
- D017 (2 designs, decisive): a rigid kinematic *CONNECTOR with no meshed geometry reproduces the
  SAME instability as D014/D015's meshed beam-link batten — rules out a meshing artifact.
- D018 (3 designs, soft stiffness at n_crosslinks=3): hit the dedup-on-write bug (see Deferred).
- D019 (27 designs, n_crosslinks&isin;{0,1}): instability does NOT afflict low-crosslink-count
  designs; reached mcs=0.7173, confirmed a real Riks snap-through via an extended-solve-budget
  check ruling out a wall-clock artifact.
- D020 (10-point local refinement): confirmed mcs=0.7191 is a real local optimum (ratio_d=0.046729,
  ratio_r_sub_frac=0.152878, ratio_pitch=0.856914, ratio_top_diameter=0.363713, n_sub_beams=2,
  n_crosslinks=1, crosslink_stiffness_ratio=0.055981, n_longerons=4); flagged two untested
  directions. (ratio_top_diameter corrected 2026-08-26 -- re-verified against this exact ODB's own
  sim_info.pkl, 6 of 7 other parameters already matched to full precision; the prior 0.436454 was
  a transcription error, not a different design.)
- D021 (14-point decisive grid probe): falsified "push further" in both flagged directions.
- D022: closed soft-stiffness-at-n=1 and n_sub_beams=3 — both collapse catastrophically.

**Infra:** bo/prefilter.py:passes_crosslinked_bundle -- gates on the SUB-BEAM's own slenderness
(never the envelope's), plus a neighbouring-sub-beam envelope-fit/no-touch check. Oracle at
bo/D40_oracle_crosslinked_bundle.py (namespace='crosslinked_bundle'); connector construction in
bo/crosslinked_bundle_mpc.py. GIF rendered from D020's own Riks ODB:
/oscar/scratch/eaguerov/sc_oracle_crosslinked_bundle/riks_516824ed2260409398982f7735bfdc0d/
SUPERCOMPRESSIBLE_RIKS.odb (340-frame history, 30 rendered).
-->

---
class: idea-slide
layout: two-cols-header
---

# D25-3 &middot; Chirality on the tape-spring section

::left::
<div class="text-sm leading-snug">

- **What:** `twist_angle` — a helical PRE-twist baked into the tape-spring cross-section along
  the member's length (D1's convention), promoted to a real 7th parameter (&plusmn;90&deg;).
  Verified to bit-exactly reproduce the untwisted record first.
- **Origin:** chirality/twist is established on other families (D1, D27); closes an ambiguity
  where the deck's own prior Seed tags disagreed on whether it had been tried here — it hadn't.
- **Stats:** n=105 (70 broad-Sobol + 35 directed) &rarr; 20/105 coilable &rarr; 15/105 decided
  &rarr; 0 good.<br>
  median mcs=0.0273, best 0.1133 (near-zero twist), vs the twist=0 baseline's 0.022/0.21
  (n=28) — no correlation with either the objective or the binding constraint (full stats in
  notes).<br>
  best good: none &middot; cleared: none &middot; novel: positional/parametric (rule 2b).
- **Verdict:** POWERED &middot; REFUTED &middot; twist_angle on the tape-spring section<br>
  0/105 feasible, same shortfall signature as the untwisted family. Twist's correlation with
  the objective and the binding constraint is indistinguishable from zero — not weak, none.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/gifs/D25-3_tape_spring_twist_negative_native.gif" class="max-h-72 rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-2 px-4 text-center">Deepest real solve of 105: fails strain budget early.</div>
</div>

<!--
**Input space:** twist_angle &isin;[-90&deg;,90&deg;] — the 7th free parameter, newly added
this pass; the other 6 are the tape-spring family's existing bounds (see D25's own slide).

**Seed:** BARREN — twist does not move this family's ceiling at all, let alone enough to
matter. The original D25 slide and D25-2 (contact)'s own Seed tags disagreed on whether
twist had already been tried (it hadn't); this closes that ambiguity with a real result.

NOT part of run 20260822T025309 -- a separate, later, ad-hoc worktree-isolated investigation.
Committed 2026-08-23T12:28 UTC (git log -S), which sits between run 20260822T025309's close
(2026-08-22T14:06 UTC) and run 20260823T161229's start (2026-08-23T16:12 UTC) -- placed here,
between those two runs' sections, per the deck's anti-chronological ordering rule. Corrected
2026-08-25: an earlier version of this note placed the slide ABOVE run 20260823T161229 on the
mistaken belief that "one day after 20260822T025309 closed" made it newer than everything below
it -- it never checked against 20260823T161229's own start time, which is later still. Do not
read this slide as one of either run's own hypotheses.

Full campaign: 70 broad-Sobol + 35 twist-sign-directed refinement, contact on, 20/105 coilable,
15/105 reached a verdict. Best decided design: mcs=0.1133 (need 0.80, short 7.1x) at
twist_angle=+5.8deg -- near zero, not at a large twist -- t_tape=0.5660, R_tape=27.805,
alpha_tape=0.4682, beta_tape=1.1473, ratio_pitch=1.3343, ratio_top_diameter=0.7267,
twist_angle=0.1018 rad. Vs. the twist=0 baseline (n=28, median mcs=0.022, best=0.21): this
campaign's median (0.0273) is marginally higher but uninterpretable given the null correlation;
its best is worse than the untwisted campaign's own best.

Caveat disclosed by the investigating agent: phase-2's directional refinement (toward positive
twist) was chosen from a phase-1 sub-sample contaminated by 2 sentinel-zero salvage rows in the
negative-twist bucket. The pooled 105-eval correlation (the headline null finding) is unaffected,
but a follow-up giving negative twist equal weight would close this residual gap.

Documentation finding, reported not fixed here (append-only convention): the original D25 slide
and D25-2 (contact) disagree on this Seed tag (BARREN vs FERTILE). Traced via
`git log -S` to commit 6ac0244, which misread an ambiguous sentence on the original slide as
saying twist itself had been tested -- it hadn't; that 330-design campaign held twist_angle=0.0
throughout. Left as a discrepancy on those two slides for the user's own correction.

Infra: bo/oracle_tape_spring.py (PARAM_NAMES/BOUNDS grow a 7th entry),
scripts/supercompressible_{lin_buckle,riks}_tape_spring.py, bo/campaign_tape_spring_twist.py,
bo/_twist_stage1_scan.py, bo/_twist_kill_signal.py. Not committed to gold as of this slide --
left in an isolated worktree pending review.

Verified 2026-08-26 (deck audit, item 1): independently recomputed n/coilable/decided counts,
the best design (mcs=0.1133 @ twist=+5.8&deg;), and both Spearman correlations (&rho;=-0.0036 vs
sigma_peak, &rho;=+0.0071 vs riks_strain, n=15) directly from the raw campaign JSON (commit
13cc7c5, branch worktree-agent-a66caf1865bb9b16f, not on main) -- all reproduce to the cited
precision.
-->

---
class: summary-slide
---

# Run `20260822T025309` — summary

<div class="text-sm leading-snug">

Built and hardened a fourth self-contact family from scratch, then used it to find the
strongest mechanistic evidence yet against local bend-twist/rib coupling as a lever — and closed
out kissing-pair's own last open gap the same way.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | The bend-twist self-locking scale-longeron mechanism (Dharmavaram et al. 2021) escapes the kinematic-depth-cap wall | **&#8253;** | 64 evals, 0% Stage-2 convergence; a causal-isolation control on the SAME base geometry with the scale panels removed converges cleanly to 89.5% compression at 1.75% strain, while the ribbed version crosses the 2% strain ceiling at only 33&ndash;45% — the coupling itself hurts, not helps | D35 |
| H2 | The scale-lock mechanism's load rise (if any) is genuine elastic response, not a kinematic artifact | **&#8253;** | Moot — H1 never produced a feasible design to test H2 against | — |
| H3 | Kissing-pair's stiffness multiplier has an unmapped sweet spot between 3&times; (converged, 48.6%) and 15&times; (collapsed, 5.1%) | **&#8253;** | 6-point sweep across the full committed range: no multiplier beats the 3&times; baseline; the apparent high-multiplier "wins" on raw peak stress are a first-contact force spike at 0.08% compression, not real capacity | D33 |

**No new mechanism cleared the incumbent (0.6077 kPa) — but two families closed with real
mechanistic understanding, not ambiguity.** Real infra debt paid down: two Stage-2 bugs fixed in
scale_lock (a t=0 contact-geometry defect, then a silent `max_local_strain=0.0` sentinel), a
missing `tape_spring` oracle registration, and kissing_pair's stiffness multiplier promoted into
a real design parameter.
&nbsp;·&nbsp; **15 delegations, 69 evals, 4 namespaces, 11.23/12 h, GATED (2 attempts)**
&nbsp;&middot;&nbsp; **Cost: $38.57**
</div>

<!--
THE GATE HISTORY. Call 1 (90% budget used, 10.84h/12h per the authoritative snapshot): REJECT —
the strategizer's closing prose claimed "~11.7h/12.00h... exhausted", which contradicted every
actually-logged figure in the run (the injected constraint snapshot and the last delegation's own
self-report both said 10.8h/90%, ~70 minutes genuinely left). PROBLEM_STATEMENT.md's "REJECT a run
you know has not used its time allocation" gave the critic no discretion. The critic also flagged,
correctly, that H3's own registered falsification_criterion (a stiffness-multiplier sweep across
3x-15x) had an identified, actionable, affordable next step sitting undone: the multiplier was
read once from os.environ at import time, invisible to the design vector. Call 2 (93% used):
PASS — the strategizer promoted the multiplier into a real 9th PARAM_NAMES/BOUNDS parameter,
ran the committed sweep, and corrected its own initial "FALSIFIED" read to INCONCLUSIVE once a
validator noted 3 of 6 points were inadmissible or missing (a stabilization-gate failure, a
divergence, and two timeouts), leaving the 5x-9x zone genuinely under-characterized.

WHY H1 WENT FALSIFIED -> INCONCLUSIVE, NOT A RETRACTION. The strategizer's first read of the
64-eval scale_lock evidence was FALSIFIED (posterior 0.04). A validator note pointed out the
registered falsification_criterion had committed to an 80-120-eval 3-phase shrinking-zoom BO
campaign; what actually ran was ~64 evals scattered across a literature-centre sweep, a deliberately
softer sub-region, and two stabilization-magnitude escalations -- informative, but short of the
severity bar the registered criterion demanded. Corrected to INCONCLUSIVE (0.08), "bounded
negative, not proof of absence" -- and the family was deprioritized for the rest of the run's
budget given the causal mechanism found (below) makes further search in this exact parameter
family implausible to succeed, not because the clock ran out.

THE TWO BUGS SCALE_LOCK SURFACED, IN THE ORDER THEY WERE FOUND. (1) The ground/top-disc rigid
surface's construction rotated the sketch about the wrong axis (X instead of Y, a copy-paste drift
from a different family's convention) and placed it at zero clearance with the wrong free-side
normal on the top disc -- three compounding t=0 defects that failed all 25 of D004's
geometrically-diverse LHS designs identically, before increment 1, independent of the sampled
geometry. Root-caused via an isolated Abaqus/CAE geometry probe plus direct .msg-file overclosure
evidence (job riks_04347d..., "LONGERONS.13 IS OVERCLOSED BY 47.9886" against a 50mm mast radius).
(2) Once fixed, the resulting sigma_peak values were 30-55x the target with max_local_strain
reading exactly 0.0 on every point -- a second delegation sanity-checked this BEFORE trusting it,
via read-only ODB field-output probing (0 of 595 sampled frames carried an E/LE field at all).
Root cause: the beam section (GeneralizedProfile + BeamSection(BEFORE_ANALYSIS), no *SECTION
POINTS) never wrote strain fields to the ODB -- every scale_lock max_local_strain reading to date,
~30 rows, was a false 0.0 sentinel, not a measurement. Fixed by switching to a native
RectangularProfile (matching this study's own working run17_rectangle anchor); confirmed via a
bit-for-bit-identical reproduction of the run17_rectangle anchor through the unmodified `default`
oracle path.

THE ARTIFACT THAT ALMOST READ AS A WIN. Kissing-pair's stiffness sweep at 12x/15x multiplier
reported sigma_peak = 0.59/0.71 kPa -- nominally beating even the study's best confirmed design
(0.6077 kPa). But mcs_at_peak (the compression fraction where that peak occurs) was 0.00078 at
15x: the "peak" happens at 0.08% compression, essentially the instant contact registers, not after
any meaningful load history. Real compression achieved (riks_strain) DECREASES with multiplier
(48.6% at 3x -> 10.2% at 12x -> 5.1% at 15x) -- a stiffer contact spring produces a bigger
first-contact force spike and locks the mechanism up faster, not a bigger real capacity. The run's
own final synthesis correctly used compression achieved, not the inflated peak force, as the
deciding metric.

A REAL DEFECT NOT FIXED THIS RUN, FLAGGED FOR THE HARNESS MAINTAINERS. D015's own sweep found only
1 of 7 successful `get_evaluator(namespace='kissing_pair')` calls persisted to the canonical
store -- consistent with a lost-update race when multiple concurrent OS processes call
get_evaluator() against the SAME namespace store without serializing the read-modify-write. Lives
in the vendored a3dasm harness package, not this repo's code; not headline-relevant this run
(the headline is ledgered via a different namespace) but a generalizable risk for ANY family using
concurrent same-namespace dispatch.

Infra promoted to gold this run: scripts/supercompressible_{lin_buckle,riks}_scale_lock.py,
scripts/supercompressible_riks_pp.py, bo/D35_oracle_scale_lock.py (the two bug fixes above);
bo/oracle_tape_spring.py (missing DataGenerator adapter); bo/D33_oracle_kissing_pair.py,
bo/kissing_pair_connector_stop.py (stiffness-multiplier promotion + connector-force output).

EVAL-COUNT DISCLOSURE (2026-08-26, deck audit item 1): the visible "69 ledgered evals" figure could
not be independently reconciled. run_status.json's own evals_used=64; a naive sum of every
delegation_log.jsonl entry's own "evals" field gives 60 (undercounts even 64, so per-delegation
self-reports are themselves incomplete -- consistent with this study's known ledger-undercounting
pattern elsewhere, see D42's own run summary). Unlike the cost figure on this slide (which has an
explicit reconciliation), no clean accounting was found for 69 vs. 64 vs. 60 within the audit's
time budget. Left as-is rather than replaced with an equally-unverified number.
-->

---
class: idea-slide
layout: two-cols-header
---

# D33-2 &middot; Kissing-pair stiffness-multiplier sweep

::left::
<div class="text-sm leading-snug">

- **What:** promotes the connector-stop law's contact-stiffness multiplier from a fixed
  module constant to a real 9th design parameter (3&times;&ndash;15&times;). Adds
  connector-force (CTF) output, making load-bearing directly measurable. Swept 6 points,
  reference design fixed.
- **Origin:** D33's own slide left "does the multiplier matter, is contact actually
  interfering" open; this sweep answers both.
- **Stats:** n=6 (full range): 3&times; converges (baseline, 48.6% compression); 5&times;
  gate-fails; 7&times; diverges; 9&times; times out twice (6&times;&ndash;10.5&times; is a
  pathological zone, confirmed by a separate long-budget follow-up); 12&times;/15&times;
  converge but only reach 10.2%/5.1% (full per-point table in notes).<br>
  cleared: 3&times; is the only non-disqualified converged point &middot; novel: no — sweep,
  not a new mechanism.
- **Verdict:** POWERED &middot; REFUTED &middot; stiffness-multiplier as a lever on
  kissing-pair's own ceiling<br>
  No multiplier beats 3&times;'s 48.6%. Compression falls monotonically with stiffness — a
  stiffer spring produces a bigger first-contact force spike, not more real capacity.
  Contact is confirmed load-bearing at 3&times;; no setting improves on it.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D33_kissing_pair_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 265px">
    <img src="/gifs/D33_kissing_pair_landscape.gif" class="rounded shadow-lg" style="max-height: 265px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Same as D33 (3&times;) — still the family's best.</div>
</div>

<!--
**Input space:** stiffness_multiplier &isin;[3,15] (&times;) — the 9th free parameter,
newly promoted this pass from a fixed environment-variable constant; other 8 unchanged from
D33's own bounds.

**Seed:** BARREN, fully — the 6&times;&ndash;10.5&times; gap was closed with a long-budget
follow-up (5h/point, no timeouts): every point decided cleanly, real compression falls
monotonically with stiffness (50.8%&rarr;17.9%), and the best of the zone (6&times;) is separately
disqualified by ring passthrough. A longer budget does not help — this is a mechanistic ceiling
(earlier 2% strain crossing at higher stiffness), not a truncation artifact. The multiplier range
is now fully characterized end to end; 3&times;'s 48.6% remains the family's best.

Full per-point table (stiffness_multiplier: converged / riks_strain / sigma_peak / mls):
3.0: 1 / 0.486 / 0.129 / 0.0194 (baseline, archived)
5.0: 0 (gate-fail, stab_ratio too high) / 0.503 / 0.196 / 0.0199
7.0: 0 (diverged near increment 1) / 0.00008 / 0.135 / 0.0026
9.0: no result — timed out twice (SLURM wall-clock cap), neighbours 6.0/7.5/10.5 in an earlier
     finer-grid attempt failed the same way; this ~6-10x zone looks genuinely numerically
     pathological, not a fluke of one job.
12.0: 1 / 0.102 / 0.594 / 0.0199
15.0: 1 / 0.051 / 0.707 / 0.0187

Provenance: D013 (real get_evaluator(namespace='kissing_pair') Abaqus calls, both the initial
sweep and the finer-grid retry) + D015 (promoted the multiplier to a real parameter, validated the
domain change, reused D013's real results rather than re-solving under wall-clock pressure).
Ledger-integrity note: only the 3.0x row survived into the canonical store; the other 5 are
recovered from delegation-local JSON logs — see the run summary's own speaker notes for the
lost-update race this surfaced in the shared harness.
-->

---
class: idea-slide
layout: two-cols-header
---

# D35 &middot; Bend-twist self-locking scale longeron

::left::
<div class="text-sm leading-snug">

- **What:** small rigid, plate-like "scale" panels textured onto the longeron's own surface at
  each of n_ribs stations, angled and spaced so consecutive scales overlap and lock against each
  other as the beam bends — a substrate that transitions from soft (bare beam) to stiff (locked
  scales) past some curvature.
- **Origin:** Dharmavaram, Ebrahimi &amp; Ghosh 2021 (arXiv:2108.10976) — overlapping rigid
  scales lock past a curvature threshold, decoupling strain from bending depth the way
  biological scale substrates do; independently top-ranked for novelty by 3 separate literature
  reviews (2026-08-16/19/20) before this run resourced it.
- **Stats:** n=64 &rarr; 54 coil &rarr; 0 riks &rarr; 0 good (0% Stage-2 convergence)
  p50/p90/p100 — &sigma;_eig (coilable only): 1.04/2.61/4.59 &middot; mcs: 0.00/0.45/0.64 &middot;
  mls: 0.00/0.019/0.020
  best good: none (0/64 passed every criterion) &middot; cleared: none
- **Verdict:** POWERED &middot; FERTILE-REWORK &middot; rigid interlocking-panel embodiment<br>
  A causal-isolation control removed the scale panels from the best-performing geometry: the
  identical base beam converges cleanly to 89.5% compression at 1.75% strain, matching this
  study's confirmed incumbent. The SAME geometry WITH the scale-lock ribs crosses the 2% strain
  ceiling at only 33&ndash;45% compression — the rigid panel-to-panel coupling at each rib
  station is itself what concentrates strain and destroys the design, the opposite of the
  mechanism's own premise.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 425px">
  <div class="flex items-center justify-center" style="height: 145px">
    <img src="/gifs/D35_scale_lock_mini.png" style="max-height: 145px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D35_scale_lock_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">D007's idx=0 (mcs=45.0%): scale panels visibly rotate/overlap per rib.</div>
</div>

<!--
**Chart provenance:** strain rises smoothly 0.0&rarr;0.0197 over 1315 real frames before the
stall — a real, gradual response, not a numerical artifact.

**Input space:** ratio_a&isin;[.006,.02] — radial half-thickness. ratio_b&isin;[.01,.05] —
tangential half-width. ratio_pitch&isin;[.15,1.2], ratio_top_diameter&isin;[0,.6] — usual
per-storey pitch/taper meaning. n_ribs&isin;[3,10] — scale-station count.
rib_length_ratio/eta&isin;[1,6] (paper's own centre ~3) — scale overlap length.
rib_width_ratio/beta&isin;[.4,3] (paper's own centre ~1.25) — scale overlap width.
rib_embed_angle_deg/alpha0&isin;[0,60] (paper's own value 30) — angle each scale is set into the
beam surface. rib_rest_angle_deg/theta0&isin;[0,20] (paper's own value 5) — rest angle before
locking engages. t_scale&isin;[.1,1.0] mm — scale panel thickness. Fixed: n_longerons=3.

**Scale-geometry vs. outcome, real data (2026-08-28, Spearman rank correlation, n=54
coilable designs, `runs/20260822T025309/experiment_data/scale_lock/`):**
rib_length_ratio vs mcs_windowed: &rho;=&minus;0.26 (p=.054); vs &sigma;_eig: &rho;=+0.44 (p=.001).
t_scale vs mcs_windowed: &rho;=&minus;0.29 (p=.035); vs &sigma;_eig: &rho;=+0.54 (p&lt;.001).
n_ribs vs mcs_windowed: &rho;=&minus;0.21 (p=.13); vs &sigma;_eig: &rho;=+0.42 (p=.002).
rib_embed_angle_deg vs mcs_windowed: &rho;=&minus;0.01 (p=.97); vs &sigma;_eig: &rho;=+0.48 (p&lt;.001).
rib_width_ratio vs mcs_windowed: &rho;=+0.26 (p=.056); vs &sigma;_eig: &rho;=+0.07 (p=.62).
rib_rest_angle_deg vs mcs_windowed: &rho;=+0.39 (p=.003); vs &sigma;_eig: &rho;=&minus;0.44 (p=.001).

**Seed:** BARREN as realized here (rigid panels rigidly coupled to fixed beam stations) — the
coupling mechanism itself is the problem, not the region of the 10D space searched. A compliant/
flexible scale realization (closer to a soft biological substrate than a rigid interlocking
panel) is a genuinely different idea, untried.

**Deferred:** any future literature review re-surfacing this exact mechanism should be pointed at
this slide and its causal-isolation control, not re-derive the geometry from the paper a fifth
time — the open question is now narrower than "does the infra exist": does ANY realization
decouple the rib-station strain concentration from the base beam's own bending strain, since a
rigid-panel realization does not. A separate question, raised post-run by the advisor (is the
0/64 Stage-2 non-convergence itself a numerics/wall-clock artifact, the way part of D43/
grain-beam's own population turned out to be?), is now closed as of 2026-08-27 (see Timeline):
it is not — every design forensically examined (idx=0/10/23, 3 of 3) shows the same
settings-independent physical wall.

**Timeline:**
- D002 (single smoke eval) + D004 (24-pt LHS, paper-centre sub-region): both failed Stage 2
  identically pre-fix.
- D005: root-caused and fixed the t=0 geometry defect, re-tested 5 points, cut mcs_windowed from
  0.0 to 0.35-0.64 — but max_local_strain still read 0.0 on all five despite raw sigma_peak
  30-55&times; the target.
- D006: root-caused the max_local_strain=0.0 sentinel to a missing *SECTION POINTS beam-section
  spec via read-only ODB field-output probing.
- D007: fixed it (native RectangularProfile) and reproduced run17_rectangle bit-for-bit through
  the unmodified `default` oracle, proving the fix cannot regress any family whose strain field
  already resolved.
- D008: two stabilization-magnitude escalations (1e-3, 5e-3) on the late-stage solver stall this
  left exposed — neither resolved it (still 0% Stage-2 convergence); one setting (idx=23 at 5e-3)
  actively failed the stabilization-energy validity gate.
- D009 (20-point diagnostic sweep, deliberately softer sub-region): tested whether
  strain_crossing_mcs could be pushed later, toward run17_rectangle's own ~0.91 benchmark — best
  achieved was 0.40, barely past the already-tested region's 0.33-0.45 midpoint.
- D010: ran the decisive causal-isolation control described in Verdict.
- 2026-08-27 post-run diagnostic (PI-requested, outside this run's own D-numbering): scale_lock's
  Stage-2 step is a general STATIC+stabilization, never Riks (self_contact_spec.md Lesson 2 —
  HARD contact+Riks measured a 7&times; convergence collapse, 9.5% vs 64%), so D43/grain-beam's
  own Riks arc-length tightening doesn't transfer directly here; the equivalent lever
  (minInc/wall-clock) had never actually been touched for this family, only
  stabilization_magnitude (D008: 2e-4/1e-3/5e-3). Re-solved idx=0 (the pictured design) at
  stabilization=5e-3, minInc=1e-12 (was 1e-10), wall-clock=10800s (3.6&times; D008's 3000s):
  step_time advanced only 0.850&rarr;0.859 — 3.6&times; the time bought +0.9 points of progress,
  burning 558 increment cutbacks down to ~1&micro;s increments with 33 negative-eigenvalue
  warnings and repeated "SOLUTION APPEARS TO BE DIVERGING" notes en route — the same
  genuine-instability signature D006 found for idx=23 (escalating 2&rarr;10 negative eigenvalues
  before its own stall). 3/3 forensically-examined designs (idx=0, 10, 23) show a
  settings-independent physical wall, unlike D43/grain-beam's own MIXED population (part
  genuinely settings-starved, part genuine dead end) — this family did not give up early;
  diagnostic script/results kept out-of-repo (non-canonical, no ledger write, same precedent as
  D43's own D007 diagnostic).

**Infra:** two real infra bugs found and fixed getting this family to a trustworthy read (full
detail in the run summary slide's own speaker notes): the t=0 ground/top-disc geometry defect,
then the missing *SECTION POINTS beam-section spec. Namespace 'scale_lock'; oracle at
bo/D35_oracle_scale_lock.py; scripts/supercompressible_{lin_buckle,riks}_scale_lock.py.
-->

---
class: summary-slide
---

# Run `20260819T022742` — summary

<div class="text-sm leading-tight">

The run that reran this week's Kresling falsification from scratch, then went one step
further — the fillet meant to save it doesn't either.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Oracle wiring reproduces the confirmed anchor | &#10003; | sigma_crit=0.770352 vs anchor 0.7704 (0.006% deviation) | — |
| H2&ndash;H4 | Three new rigid-contact geometries (coaxial mandrel, shaped cone disc, eccentric capstan pins) create a genuine second, contact-mediated load path above the incumbent | **&#8253;** | H2 already closed. H3/H4 escalated to Explicit: non-quasi-static (ALLKE/ALLIE up to 0.6, 10&times; over threshold) at every rate — a numerical wall, not force amplification | — |
| **H5&ndash;H8** | The Kresling local-zoom design (&sigma;_peak=1.0723 kPa, ~10&times; Bessa) is a real, mesh-converged, imperfection-robust result | **&#10007;** | Reproduced exactly (H5), then falsified: kink strain moves -13&ndash;28% under 2&times; refinement, jump ratio GROWS with refinement (H6); only 3/7 imperfection draws converge (H7); 2&times; mesh gives +197%, 4&times; fails to solve (H8) | D17-3 &rarr; |
| **H9&ndash;H10** | Filleting the sharp kink removes the mesh-artifact, and the design still coils | **&#8253; / &#10007;** | H9: every fillet radius &times; mesh non-converged (NaN) — inconclusive. H10: forced via valid Explicit — reaches only 3.7% compression, far short of 80% | D17-3 &rarr; |
| H11 | A laced (two-parallel-chord) longeron beats the incumbent via distributed load-sharing | **&#8253;** | 6/6 stuck at 1.3&ndash;3.4% compression, early non-convergence; mild trend with ratio_h, never close to feasible | — |
| H12 | A strongly-graded two-storey mast stages sequential coiling and beats the incumbent | **&#8253;** | Underpowered (2&ndash;3 pts vs 5D+ registered) — but its own Explicit-vs-Standard check shows only a 1pp gap, ruling out a Kresling-style mesh artifact | — |

**No new mechanism cleared the incumbent (0.6071 kPa)** — the real contribution is closing the
Kresling question two independent ways, not opening a new lead.
&nbsp;·&nbsp; **26 delegations, 35 evals, 9 namespaces, 11.33/12 h, GATED (4 attempts)**
&nbsp;&middot;&nbsp; **Cost: $71.06**
</div>

<!--
THE GATE HISTORY, IN FULL. Call 1 (79% budget used): REJECT — the notebook's own analysis cell
was written in the past tense as a concluded negative result ("no further avenue remained
tractable") while 21% of wall-clock and an unbounded eval budget remained; PROBLEM_STATEMENT.md's
"CRITIC: REJECT a run you know has not used its time allocation... regardless of how many
attempts have failed" is unambiguous, and the critic applied it. Call 2 (84% used): REJECT again
— TWO fresh CRITICAL findings, not a re-litigation of call 1: the notebook's own cells
contradicted each other on delegation/eval counts (H12 entirely missing from the analysis cell's
per-hypothesis verdict list, despite being closed two delegations earlier), and the deliverable
was still framed as a final close with budget left. Call 3 (93% used): REVISE — no CRITICAL
finding this time (the headline is properly ledgered, the negative conclusion well-evidenced),
but two MAJOR notebook-hygiene defects (stale summary counts across cells; H12's own cell not
re-synced to its final D026 update). Call 4 (94% used): PASS — the two REVISE items were fixed,
the remaining findings dropped to MINOR (a `doe`-cell presentational gap; one contact-augmentation
hypothesis, H2, closed on a prior run's data without this run's own Explicit-escalation check).
This is the sharpest illustration in the deck yet of the critic doing exactly its job: two REJECTs
were forced entirely by "you have budget left, keep going" and "your own notebook disagrees with
itself" — not by the science being wrong — and the run's actual scientific content (H5-H10)
never needed correcting once it was reported.

INDEPENDENT CONVERGENCE WITH THIS WEEK'S MANUAL INVESTIGATION. D012 (this run) reran the exact
mesh-refinement test on the exact local-zoom Kresling design (splitting the simulated beam into
more, smaller pieces — a "finer mesh" — and checking whether the computed stress changes; a
trustworthy simulation result should stop changing, i.e. converge, as the mesh gets finer) —
globally 2x finer beam mesh (seed divisor 300->600), then 4x — without being told the answer in
advance, and got **+197% at 2x, non-convergence at 4x**: bit-for-bit the same finding as the
manual investigation earlier this session (and as the paper-referee subagent's independent read
of the same evidence). Three
independent lines of reasoning — one manual, one adversarial-referee, one a fresh 12h agentic run
with its own falsification charter — landed on the identical number. That is about as strong as
corroboration gets for a negative result.

THE FILLET EXPERIMENT, WHAT IT ACTUALLY SHOWS — read H9 and H10 as two separate questions, not
one. H9 asked "does rounding the kink fix the mesh-convergence artifact?" and the honest answer is
**we don't know** — D014/D015 tried 4 fillet radii (0.5, 1.0, 3.0, 6.0mm) and 3 mesh/numerics
variants at the smallest radius, and every single refined-mesh attempt produced NaN (non-
convergence), never a comparable baseline-vs-refined pair. The science-monitor correctly
downgraded this from FALSIFIED to INCONCLUSIVE per Charter Sec.4: a quantified test that never
produces a number cannot falsify anything. H10 then asked a DIFFERENT, sharper question: forget
mesh convergence, does the r=0.5mm filleted design actually coil, resolved with a technique that
sidesteps the convergence question entirely — Abaqus/Explicit, a dynamic, time-stepping solver
used here as a numerically robust stand-in for the usual static one, run at a loading rate slow
enough to be "quasi-static-valid": the simulated part's kinetic energy (ALLKE, the energy of
motion) stays a small fraction of its internal strain energy (ALLIE, the energy stored by
deforming) — here ALLKE/ALLIE=0.0273, comfortably under the usual 0.05-0.10 cutoff for "this is
behaving like a slow, static compression, not a dynamic impact". That resolve is clean and unambiguous:
**3.7% global compression**, twenty times short of the 80% required. So the honest picture is not
"we don't know if a rounded joint would work" — it's "the one radius we could get a trustworthy
answer for doesn't work, and it isn't close."

WHY H2-H4 ALL CLOSED THE SAME WAY, AND THE ONE GAP THE FINAL REVIEW FLAGGED. All three
contact-augmentation genera (mandrel, shaped disc, capstan pins) hit non-quasi-static (violent,
dynamic-feeling, not slow-and-static) "walls" under Standard/Riks (Abaqus's usual static solver,
which traces out the force-vs-compression curve step by step using the arc-length/Riks method) and
stayed non-quasi-static under Explicit escalation too — the same diagnostic
signature as the Kresling kink, but a geometrically unrelated cause (all three share one contact
recipe: rigid surface vs. deformable beam). Call 4's own MINOR finding is worth keeping visible:
H3 and H4 got their own fresh Explicit re-solve this run (confirming genuine dynamic violence,
ALLKE/ALLIE >> 0.05 at every rate); H2 (mandrel) did not — it was closed entirely on a **prior
run's** decisive campaign (20260812T014026, zero contact events across 9 evaluations at 4 radii),
cited via literature review rather than re-tested here. Correctly labelled INCONCLUSIVE at a low
posterior (0.08), not FALSIFIED, so this doesn't change the verdict — but a shared numerical
setting (contact stiffness/penalty defaults) rather than three independent instances of "genuine
physics" remains a live, unruled-out alternative for the family as a whole.

THE SELF-CORRECTION PATTERN, NAMED HONESTLY BY THE STRATEGIZER ITSELF. Four hypotheses this run
(H2, H3, H9, H12) were initially marked FALSIFIED by the strategizer and each time corrected to
INCONCLUSIVE by a science-monitor note citing Charter Sec.2/3 ("a test narrower than the
registered criterion routes to INCONCLUSIVE, not FALSIFIED"). The closing retrospective is
explicit that this took "several corrective cycles... rather than repeating the same over-claim
pattern once caught" — the charter worked, but it had to work four times in one run, which is
itself worth watching in future runs rather than treating as fully resolved.

INFRA LEFT BEHIND, not yet classified for promotion. D008 fixed a real gap: `bo/oracle_kresling.py`
existed with two out-of-band result JSONs already in the repo, but no run_config.json had ever
pointed `get_evaluator(namespace='kresling')` at it — so neither the near-miss nor the local-zoom
result had ever gone through the canonical, ledgered evaluation path before this run. That fix
(29 lines, additive, `KreslingOracleDataGenerator`) is a clean promotion candidate. Separately, this
run also built four entirely new oracle/script families for its own falsification campaigns
(capstan_pins, graded_storey, kresling_fillet, kresling_imperfection, plus Explicit-solver variants
of each) — real, working infrastructure behind now-closed negative/inconclusive hypotheses, left
as untracked files. Worth keeping for any future re-opening of these genera; not yet reviewed for
gold promotion.

WHAT'S STILL FLAGGED OPEN. Call 1's alternative-hypothesis note, never fully answered this run:
varying `n_storeys` on Bessa's own native multi-storey backbone, and a smooth continuously-curved
bistable/snap-through element (the literature's own top-ranked, highest-novelty candidate,
previously shelved for needing shell/solid elements) — both remain untried mechanisms for a future
run, not ruled out by anything found here.

Literature review was rate-limited for the entire session (arXiv + OpenAlex only, per the
rate-limit-handling instruction) — noted as a real gap, not fatal: three dedicated fresh-mechanism
reviews (D013, D016, D022) still ran and found nothing further tractable within what was
searchable.
-->

---
class: idea-slide
layout: two-cols-header
---

# D17-3 &middot; From a 10&times; Bessa near-miss to a resolved falsification

::left::
<div class="text-sm leading-snug">

- **What:** a dedicated oracle with `ring_passthrough` wired as a LIVE constraint. Three
  campaigns, 380 evals total, plus mesh-refinement (2&times;/4&times;) and fillet variants
  on the resulting near-miss, cross-checked by an independent referee.
- **Origin:** the base D17 slide left the hinge's mesh-convergence status open after a
  coarse-mesh scan suggested a &gt;10&times; Bessa design; tests whether that headline holds.
- **Stats:** n=380 across 3 campaigns (150+80+150) + mesh/fillet variants.<br>
  Broad search: &sigma;<sub>peak</sub>=3.27 kPa "win" — zero contact pressure throughout, an
  early-transient artifact. Local zoom: a genuinely contact-engaged 1.0723 kPa design
  diverges under mesh refinement (2&times;: 3.187 kPa, +197%; 4&times;: fails) — a real
  reentrant-corner singularity, not a meshing problem (per-frame strain confirms).<br>
  cleared: both apparent 2&times; Bessa clears are disqualified &middot; novel: n/a —
  re-verification.
- **Verdict:** POWERED · REFUTED · Kresling/TCO hinge's own reentrant-corner
  singularity<br>
  Found, and retracted, twice — a contact artifact, then a genuine but mesh-divergent
  design. A real reentrant-corner singularity in the hinge's kink, not a mechanical joint;
  filleting doesn't rescue it. Full ledger in notes.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 415px">
  <div class="flex items-center justify-center" style="height: 140px">
    <img src="/gifs/D17-3_kresling_sigma_history_mini.png" style="max-height: 140px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 240px">
    <img src="/gifs/D17-3_kresling_contact_winner_native.gif" class="rounded shadow-lg" style="max-height: 240px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Above: both meshes overlaid, late divergence. Below: local-zoom design.</div>
</div>

<!--
**Input space:** same design vector as D17's own base slide, plus `ring_passthrough` newly
wired as a live constraint (not a new free parameter — a search-time gate).

**Seed:** BARREN — the singularity is intrinsic to modeling the hinge as one continuous,
rigidly-connected beam with a geometric kink; mesh refinement, fillets, and an independent
referee all confirm this is real, not a numerical artifact. Consistent with D17-2
closing this same family (its own Seed cites this exact finding). A genuinely
different hinge REALIZATION — an actual pin/flexure joint, not a geometric kink in one
continuous member — would be a different idea, not a perturbation of this one, and would need
its own slide rather than a continuation here.

FULL CAMPAIGN LEDGER: bo/run_kresling_contact_search.py (150 evals, 3-phase zoom BO, SEED=0,
TARGET_SIGMA_PEAK=0.2244, no_ring_passthrough + stab_ratio as live constraints alongside
mcs/mls/slenderness); bo/run_kresling_local_zoom.py (80 evals, 2-phase, SEED=1, centered on the
near-miss); bo/run_kresling_broad_search.py (150 evals, 3-phase, SEED=2, psi widened to 60deg,
ratio_top_diameter widened to 0.80).

THE BROAD-SEARCH ARTIFACT, DEBUNKED IN DETAIL: 3.27 kPa sounded like a 5.4x-incumbent-beating
headline. CPRESS/COPEN extraction from the solved ODB (the ODB is Abaqus's output file holding the
full solved simulation; CPRESS/COPEN are its per-point contact readouts — CPRESS is contact
pressure, how hard two surfaces are actually pressing on each other; COPEN is the contact gap, how
far apart they still are) showed zero contact pressure (ground_cpress_max, top_cpress_max) throughout
the reported window — the "win" was measured before the ground plane and the mast were ever
actually touching, an early-transient sampling artifact, not a real structural response. Caught
before it reached this deck.

THE LOCAL-ZOOM DESIGN LOOKED GENUINELY DIFFERENT: CPRESS (contact pressure) was non-zero and
consistent with real engagement, which is exactly why it needed a referee rather than a quick
accept. The referee
subagent (deliberately given the hardest version of the question -- "is this provably printable,
don't make it easy") converged on mesh non-convergence as the decisive issue independently.

WHY THE HINGE IS A REAL SINGULARITY, NOT JUST AN FE (finite-element, i.e. simulation-model)
ARTIFACT. `scripts/supercompressible_lin_buckle_kresling.py` builds one continuous `WirePolyLine`
per longeron with a geometric vertex inserted at `ratio_hinge_height`, rotated by `psi_kresling`
before insertion -- meshed as ordinary beam elements with full moment continuity straight through
the kink (i.e. modeled as one unbroken, rigidly-connected member, not as two pieces joined by a
hinge). No connector element, no MPC (multi-point constraint — the modeling tools Abaqus offers for
an actual pin/hinge joint that CAN rotate or flex independently), no rotational release anywhere in
the script. That means the sharp angle change in the FE model corresponds to a real sharp bend in
the part's own centerline geometry, not a solver bookkeeping choice that vanishes on a real print.
A continuous PLA rod bent to a sharp interior angle concentrates stress there for the same reason
the idealized beam model does — a "singularity" here means the model predicts stress that grows
without bound the closer you look at that exact point, rather than settling on one finite number
— and the mesh divergence goes the WRONG way to be reassuring (finer mesh reports HIGHER stress,
consistent with an unresolved singularity, not slow convergence to a finite value).

CONTROLS, WITH JOB NUMBERS. run17_rectangle (job 5081026): divisor 300 -> sigma_peak=0.60713
(exact match to the confirmed anchor); divisor 600, 1200 -> Stage 2 fails to converge ("TOO MANY
ATTEMPTS"), cleanly, without producing a wrong answer. The actual 1x Bessa point (job 5081207,
circular cross-section, ratio_d=0.02005/ratio_pitch=0.25/ratio_top_diameter=0.25053): divisor 300
-> sigma_peak=0.112199; divisor 600 -> 0.112198 (-0.0004%); divisor 1200 fails to solve. Genuinely
converged. Neither control shows Kresling's signature (a fully-converged answer at 2x that is 197%
different from baseline) -- both either match or simply fail to run.

BESSA'S OWN VALIDATION DOESN'T RESCUE THIS EITHER. Bessa et al. 2019 never ran a mesh-refinement
study (checked: zero "mesh" hits in the paper text); their validation is empirical -- print,
compare against FEA with a 95% CI from material-property uncertainty (Fig. 3C, Table S3), plus
five more printed designs to check the classification boundary (Fig. S17/S18). That's real, and
arguably stronger evidence than a numerical convergence study for the geometry they actually built
-- straight longerons pinned into rings, no interior beam-to-beam kink. It has never been asked to
validate a joint topology like Kresling's, because their own design doesn't have one.

WHERE THE GIF CAME FROM: presentation/render/render_odb.py gained two additive, backward-compatible
env-var hooks (FORCE_FRAMES, FORCE_READOUT_JSON) because the existing motion-progress-based frame
sampler (`_frame_indices`, a deliberate 2026-08-06 fix for stalled solves) silently under-samples
any event with high force change but near-zero displacement change -- exactly what a late contact
engagement against a near-frozen structure looks like. Not yet committed to gold as of this slide;
flagged for promotion.

Verified 2026-08-26 (deck audit, item 1): the SLURM job artifacts (5081026/5081207) backing the
mesh-refinement divisor table no longer exist on scratch (expected -- this predates the study's
git-committed-JSON convention this audit relied on elsewhere), so those specific numbers were not
independently re-derived. Instead, confirmed the claimed cross-run reproduction is real: read
`runs/20260819T022742/debug/strategizer_notes/hypotheses.json` directly -- H6 FALSIFIED (strain
reading not mesh-converged), H8 FALSIFIED (sigma_peak=1.0723 not mesh-converged), H9 INCONCLUSIVE
(fillet did not cleanly rescue it), H10 FALSIFIED (even a quasi-static-validated Explicit solve
fails to reach coilability) -- all four match this slide's narrative exactly.

WHERE THE MINI PLOT CAME FROM (added 2026-08-27, format-conformance pass): unlike the job-number
divisor table above, this data DID survive on disk and was verified directly, not re-typed from
prose. `D17-3_kresling_meshconv_mini.png` plots sigma_peak straight from
`runs/20260819T022742/debug/delegations/D012/mesh_convergence_results.json` (divisor 300 ->
1.072340266344733 kPa, converged; divisor 600 -> 3.186755229060794 kPa, converged; divisor 1200 ->
solver exception, "TOO MANY ATTEMPTS MADE FOR THIS INCREMENT", no sigma_peak value exists) --
the +197.18% figure comes straight from that same delegation's own `mesh_convergence_summary.json`.
Deliberately NOT a sigma-vs-compression curve (which would visually read as "clean, trustworthy
result") -- this panel is the falsification evidence itself: two converged points diverging, a
third that produced no answer at all, marked as a solver failure rather than interpolated or
omitted silently. Generated by a fresh, uncommitted ad hoc script (no committed generation script
exists for this deck's mini plots, per the same convention as `D24-2_rank3_sigma_mcs_mini.png` --
04ace0a); style matched to the deck's other mini plots (firebrick #B2182B markers/line, white
background, light gridlines) but the axes differ (mesh divisor vs sigma_peak in kPa, not
sigma-vs-mcs normalized to Bessa) because the finding itself is about mesh sensitivity, not a
compression-history shape. Saved as `D17-3_kresling_meshconv_mini.png`, NOT `D17_kresling_mini.png` --
that filename is already taken by D17's own idea-slide mini plot (`/gifs/D17_kresling_mini.png`,
line ~5474); overwriting it would have silently broken that earlier slide. **SUPERSEDED as the
visible panel 2026-08-27** (see below) -- the file is kept on disk, just no longer referenced by
this slide, per the user's own instruction not to delete it.

WHERE THE CURRENT (STRAIN-HISTORY) MINI PLOT CAME FROM (added 2026-08-27, replacing the divisor
bar chart above per advisor review -- "I rather we have the strain history plot than that
refinement plot which can be easily read in prose"). Both mesh divisors' raw solved ODBs still
existed on scratch (`/oscar/scratch/eaguerov/sc_meshcheck_kresling/riks_baseline_300_79100c7e/` and
`riks_finer_2x_600_0fe3ffb7/SUPERCOMPRESSIBLE_RIKS.odb`) -- opened read-only
(`session.openOdb(readOnly=True)`, `abaqus python`, no re-solve). The kink-adjacent element pair
(`elem_before_kink`/`elem_after_kink`, one B31 element on each side of the chain-walked kink node)
is reused VERBATIM from D012's own single-frame `kink_probe.py` output
(`<label>_kink_probe.json`) -- not re-derived -- extended to walk EVERY frame of the Riks step
(152 frames at divisor 300, 294 at divisor 600) instead of one, reading the "E" field's peak
|component| at those two elements per frame plus the ZTOP_REF_POINT reference point's U3 HISTORY
output (interpolated onto the field-output frame grid by step time, same alignment convention as
`bo/response_metrics.py`) to get compression (mcs) at that same frame. Script:
`kink_strain_history.py` (ad hoc, not committed -- same not-yet-promoted-to-gold status as the
GIF env-var hooks noted above).

REAL FINDING FROM THE FULL HISTORY, not anticipated going in: the local strain at the kink itself
does NOT diverge between meshes the way sigma_peak does. At matched compression the two curves
track within ~1% of each other for the ENTIRE Riks history (e.g. mcs=80%: 1.685% vs 1.684%;
mcs=95%: 3.58% vs 3.62%; final frame, mcs=100%: 6.187% vs 6.190%) -- consistent with
`mesh_convergence_summary.json`'s own already-recorded `mls` comparison (0.019500 vs 0.019419,
-0.42%) and even the single-frame `kink_strain_before`/`kink_strain_after` numbers (-13%/-28%,
i.e. LOWER on the finer mesh, the opposite direction from amplification). So the +197% divergence
that falsifies this design lives specifically in the GLOBAL sigma_peak reading (nominal stress
from the total reaction force at ZTOP_REF_POINT) -- not in the local strain-component readout at
the kink's own adjacent elements. This does not change the verdict (sigma_peak is the study's own
reported headline metric, and it demonstrably fails to converge under refinement -- that alone is
disqualifying) but it sharpens WHERE the singularity's numerical symptom actually shows up: in the
equilibrium/reaction-force computation near the kink, not in the elemental strain output at that
same location. Annotated directly on the chart (both meshes' own windowed sigma_peak is read at
essentially the same compression, mcs&asymp;81%, where the two curves are still overlapping) rather
than left as a caption-only claim. **SUPERSEDED as the visible panel 2026-08-27** (same day,
same review pass -- see below): the advisor asked for &sigma; vs compression instead of local
strain, since the local-strain finding above, while real, is not what the family's own
falsification is measured on. `D17-3_kresling_strain_history_mini.png` is kept on disk, unreferenced,
same not-delete convention as `D17-3_kresling_meshconv_mini.png` above -- this is now the SECOND
superseded panel on this slide, in order: divisor bar chart -> local-strain history -> sigma
history (current).

WHERE THE CURRENT (SIGMA-HISTORY) MINI PLOT CAME FROM (added 2026-08-27, replacing the local-
strain panel per advisor review -- "why local strain? i wanted sigma as a function of
compression... same red/grey color coding[,] and solid/dashed for mesh resolution"). Reused the
SAME two `results.pkl` files the local-strain chart read (no new ODB access needed -- U/RF
reference-point histories were already loaded there): &sigma;(t) = |RF3(t)| &times; 1000 /
(&pi;&middot;D1&sup2;/4&middot;n_longerons), mcs(t) = clip(-U3(t), 0, &infin;) / mast_height,
IDENTICAL formula to `bo/response_metrics.py:windowed_metrics` (called directly, not
reimplemented, to guarantee the sigma_peak values plotted match the ones already cited on this
slide to the digit: 1.072340266344733 / 3.186755229060794 kPa). Each curve is TRUNCATED at its
own `window_n` (the frame where that mesh's own local strain first crosses the 2% cap,
82.8%/83.2% mcs respectively, per `windowed_metrics`'s own windowing rule) -- plotting the full
raw history past that point was tried first and is actively misleading: both meshes' raw RF3
histories climb back up together to within 0.6% of each other by mcs=100% (4.474 vs 4.448 kPa),
which would visually erase the divergence the family was actually falsified on. The color
gradient (grey&rarr;red, `LinearSegmentedColormap` over `#9a9a9a`/`#d94f3a`/`#8c1a12`) encodes
each point's own &sigma; magnitude via a `LineCollection`, shared min/max across both curves so
"how red" is comparable between them; line style (solid/dashed) encodes mesh resolution,
independent of color. Script: `kresling_sigma_history.py` (ad hoc, uncommitted, same convention
as this slide's other mini-plot scripts).
-->

---
class: summary-slide
---

# Run `20260816T013744` — summary

<div class="text-sm leading-tight">

The run that used 95% of its budget on two contact-mediated tracks, produced the first
non-zero **kissing-pair** result, and never formally closed — a harness bug, not the science.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H3 | Self-contacting divergent-convergent longeron pairs beat 2&times; Bessa via a soften-then-contact-stiffen load path (Liu/Ennis/Coulais 2024) | **?** | Hard `*CONNECTOR STOP` failed under 3 solvers (~0%); a soft `*Connector Elasticity` law reached **48.6% compression** (D018) — the family's first non-zero result — but a stiffness/self-clearance check (D019) couldn't confirm contact is doing real work | D33 |
| H4 | A graded, contact-decoupled two-storey mast beats 2&times; Bessa by presenting storey 2 undamaged after storey 1 lands (Liu/Ennis/Coulais 2024) | **?** | 8 delegations, 3 contact laws, 2 solvers. Explicit dynamics reaches 76% raw compression, but **storey 1's own strain crosses Bessa's 2% limit almost immediately** — a design limit, not a solver limit | D34 |
| H5 | A smoothly graded (non-uniform) longeron cross-section, no contact, beats a uniform member | &#10007; | Predicted to fail (no literature basis for grading alone adding capacity); confirmed: 0/10 feasible, &sigma;_peak 0.79&ndash;1.01&times; the uniform baseline, never exceeding it | D18 |
| H1/H2 | Oracle wiring unchanged &middot; literature has an untried mechanism | &#10003; | Anchor reproduced to 4 s.f. &middot; 14 papers surveyed, 3 candidates ranked, grounding H3/H4 above | — |

**The critic caught the run trying to close early, twice** — at 80% budget (candidate 3 still
unexplored) and again at 87% (claiming "every lever exhausted" while an untried lever was on
record). Both REJECTed; the run then produced its only positive result (D018) in response. The
third review found nothing wrong, but `Done()` then crashed 21 times on a harness bug (`sorted()`
comparing a float to a string), closing **UNGATED** at 17h10m of 18h.
&nbsp;·&nbsp; **Cost: $192.82**, 79 evals, 17.2/18 h, UNGATED (harness bug, not science/budget)

</div>

<!--
TWO PARALLEL TRACKS, BOTH CONTACT-MEDIATED. D002 (literature_reviewer) surveyed 14 papers
and grounded a real, recurring mechanism -- a two-phase "soften, then self-contact stiffens"
load path (Liu, Ennis & Coulais 2024 arXiv:2410.16452; Dharmavaram, Ebrahimi & Ghosh 2021
arXiv:2108.10976; Hima, Bigoni & Dal Corso 2022 arXiv:2205.02034) -- and ranked THREE
candidates: (1) kissing-pair self-contact [highest confidence, pursued as H3/D33], (2)
staged storey [second, pursued as H4/D34], (3) a bend-twist self-locking ribbed cross-section
[highest novelty, lowest confidence, needs shell/solid elements not yet wired up -- SHELVED,
and its shelving is exactly what the first REJECT below caught].

WHAT ACTUALLY BLOCKED EACH TRACK, IN PLAIN TERMS. A sudden/rigid contact force breaks an
IMPLICIT solver's iteration (Abaqus/Standard's usual step-by-step approach, which must find a
converged answer at every single step -- contrasted with Explicit below, a different, slower but
more robust time-marching approach that never has to "converge" at a step, only advance) regardless
of whether the underlying idea is any good -- that is a NUMERICAL problem, fixed by changing the
math (a softer contact law, a different time-stepping solver), not the design. D33/H3 hit exactly
this (a hard *CONNECTOR STOP -- a modeling element that enforces a rigid mechanical limit directly,
rather than through ordinary surface-to-surface contact -- failed under Riks, Static+stabilization
(the same static solver with a small artificial damping term added, a common trick to help it
push through a rough patch), AND Explicit -- three solver regimes, one contact law, ~0% every
time), then fixed it numerically (D018's soft law) and got real signal for the first
time. D34/H4 hit the SAME numerical wall at first (D007-D010: every design stalls at
1.5-2.5% compression regardless of contact law), fixed it numerically too (D011/D013's
switch to Explicit dynamics, reaching 76% RAW compression, no more crashing) -- and THEN hit
a completely different kind of wall: a genuine DESIGN limit that no solver change touches.
Storey 1's own material strain crosses Bessa's 2% ceiling almost immediately, independent of
solver or contact law (D013's finding). That is why H4 is the cleaner negative: the
diagnosis is design-specific, not a tooling gap.

H5, THE NEGATIVE CONTROL (not a new D-slide -- see below). D016 tested whether a smoothly
graded single-member cross-section (no contact, no discrete storeys) beats a uniform member
-- predicted to FAIL, since nothing in the literature says continuous grading alone (absent a
contact-triggered stiffness jump) adds load capacity rather than just relocating where
buckling starts. Confirmed cleanly: 8/10 designs converged (2 stalled), 0/10 feasible,
sigma_peak ranged 0.0883-0.1136 kPa = 0.79-1.01x the Bessa point (0.1122 kPa, the CURRENT
sigma_peak-metric anchor -- NOT the 0.1306 kPa retired-eigenvalue figure), never exceeding
the uniform baseline. This is genuinely the SAME idea as D18 "Smoothly radially-tapered
('waisted') longeron" -- a longeron whose own cross-section varies along its arc-length,
thick at the ends and thin (or vice versa) in the middle -- so per rule 1 this does NOT earn
a new D-slide; it folds into this summary instead, with the Idea column pointing back to D18
rather than a dash (this IS a specific idea being re-tested, not "the whole design space").
D18's own headline was later invalidated by a slenderness-formula bug (see D18's own speaker
notes); H5 is effectively a clean, corrected-infrastructure re-confirmation of the same
prediction, useful precisely because it is cheap (one 30-minute delegation) and because it
rules out an entire class of cheaper ideas before anyone spends a contact-engineering
campaign on a variant of it.

THE TWO REJECTS, VERBATIM ENOUGH TO MATTER. Call 1 (80% budget, 14.4/18h): the deliverable
wrote up both tracks as OPEN and moved to close with 3.64h unspent; the objection didn't need
to invent anything -- candidate 3 (the bend-twist ribbed cross-section) was still sitting on
the shelf, unmentioned in the plan for the remaining time. Call 2 (87%, 15.58h): ONE
delegation happened in between (D017, porting Explicit dynamics to kissing_pair), and the
deliverable now claimed "every lever exhausted" -- but D017's OWN closing sentence named an
untried lever (a soft/ramped connector instead of the hard stop), and the run had spent its
one intervening delegation re-testing the old formulation under a new solver instead of
pursuing it. REJECTed again, and pointedly NOT softened to REVISE -- the critic's own
reasoning: re-testing instead of trying the named alternative isn't a good-faith response,
it's a resubmission. This is the exact failure mode the study was burned by in run
20260814T015148 below, which PASSED its gate at only 32% of budget spent -- the rule written
in response ("CRITIC: REJECT a run you know has not used its time allocation") is what fired
here, twice, and it produced the run's only positive result as a direct consequence (D018/
D019, in response to call 2).

THE THIRD REVIEW AND THE WALL. Call 3 (95% spent) found nothing wrong -- it re-verified
every disputed number (0.486, 0.051, both self-clearance figures) against the raw delegation
logs to the decimal, and returned NOTED (zero findings). It would have become PASS/GATED on
the next attempt. Instead, `Done()` -- the formal gate-mode close -- started throwing
`TypeError('<' not supported between instances of 'float' and 'str')` 21 times over about 30
minutes. Root cause: a3dasm's `_ledger_snapshot` (src/a3dasm/_src/nodes/strategizer.py:868)
calls `sorted(all_rows)` to build a content hash over every experiment row across every
namespace, and this run's two new oracle namespaces (kissing_pair, staged_storey) carry
free-text diagnostic `note` columns alongside numeric ones -- a mix Python's `sorted()`
cannot compare. CONFIRMED PRE-EXISTING, not introduced by the automatic a3dasm upgrade that
ran at launch (2b5f12de -> fbd292d6): none of the three commits in that range touch
strategizer.py. A latent bug, triggered by this run's column shape, not introduced by it --
still open, in a3dasm's own repository, as of this writing.

COST RECONCILIATION (rule 7ter). telemetry/summary.json recorded $192.07 total, including a
strategizer entry of $25.23 from only 4 of its 8 real turns; summing all events directly from
debug/transcripts/strategizer/*.jsonl gives $25.98 -- a $0.75 correction, smaller than the
20260809 run's (where the strategizer was entirely unrecorded) but the same underlying gap.
Actual: $192.07 - $25.23 + $25.98 = $192.82.

INFRA PROMOTED TO GOLD FROM THIS RUN (not itself part of the science, noted for
completeness): scripts/supercompressible_riks_pp.py gained ALLKE/ALLIE energy-ratio
extraction (needed for the Explicit-dynamics quasi-static-validity check used by both
tracks); scripts/supercompressible_{riks,lin_buckle}_pretwist.py gained a new opt-in
`cross_section == "circular_graded"` mode (for H5/D18's re-test); and
presentation/render/render_odb.py's ring-schematic overlay crashed (IndexError on an empty
`rings_3d`) rendering D34's gif -- a pre-existing gap this run's two-storey topology was the
first to expose, fixed by guarding the one-time ring-label block on `rings_3d` being
non-empty. All three are purely additive/defensive; every pre-existing family's code path is
untouched.
-->

---
class: idea-slide
layout: two-cols-header
---

# D33 &middot; Self-contacting divergent-convergent longeron pairs

::left::

<div class="text-sm leading-snug">

- **What:** Replace each longeron with a **pair** of independently-anchored beams, pre-bowed
  to close a small gap and make frictionless surface contact partway through the coil — no
  shared node with the ring, unlike the closed `secondary_stop` family. Single validation
  point; only the contact law/solver varied (see Input space).
- **Origin:** Liu, Ennis &amp; Coulais 2024&sup1; (measured stroke-triggered self-contact
  stiffening), Dharmavaram, Ebrahimi &amp; Ghosh 2021&sup2; (soft-to-stiff contact-locking in
  a bending filament), Hima, Bigoni &amp; Dal Corso 2022&sup3; (rigorous non-artefactual
  stiffness discontinuity at a unilateral-constraint threshold).
- **Stats:** n=6 &rarr; 6 coil &rarr; 2 riks &rarr; 0 good
  p50/p90/p100 (n=2 decided) — &sigma;_eig: .158/.158/.158 &middot; mcs: .268/.442/.486 &middot; mls: .0191/.0194/.0194
  cleared: **1 of 2 decided &ge; 2&times; Bessa** — but that design (&sigma;=.707) never coiled
  past 5.1% (mcs=.051), so it isn't feasible either &middot; novel: **untested** — contact-on
  vs contact-off self-clearance nearly identical (&minus;1.999 vs &minus;2.000mm)
  best good: none (0/2 decided passed every criterion)
- **Verdict:** BLOCKED &middot; UNKNOWN-NO-EVIDENCE &middot; self-contact load-bearing<br>
  A hard `*CONNECTOR STOP` failed under 3 solvers (~0% every time — the sudden contact force
  breaks the solver, not the physics). A soft, ramped connector law reached **48.6%
  compression**, far past every hard-stop attempt — but whether the contact is doing real
  load-bearing work, or merely not interfering, was never confirmed.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 430px">
  <div class="flex items-center justify-center" style="height: 150px">
    <img src="/gifs/D33_kissing_pair_mini.png" style="max-height: 150px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 245px">
    <img src="/gifs/D33_kissing_pair_landscape.gif" class="rounded shadow-lg" style="max-height: 245px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Family's best (D018): converges at 48.6% — see notes.</div>
</div>

<!--
**Input space:** none free — a single validation point (n_corners=3, ratio_d=.02, pitch=.75,
top_d=.30, leg_offset=.05, gap0=.015); only the contact law/solver varied across delegations.

**Render-cap caveat, full text (trimmed from the visible caption 2026-08-28 to fix a confirmed
27px render clip, headless-measured):** Abaqus reports this Riks solve as converged at 48.6%
compression (mcs=0.486) — that is the reported/citable number. If the animation appears to keep
compressing past that, it's the render pipeline's global 95% safety cap (which only blocks
physically meaningless Riks overshoot), not evidence of more real compression than 48.6% — this
deck does not treat a solver's own "completed successfully" flag as proof it reached its actual
load target without checking the load path (see D21-revisited's own finding on this exact trap).

**Seed:** FERTILE — sweep the connector's stiffness multiplier as a free search dimension
around 3&times; (which converged) rather than point-probing 3&times;/15&times;; the
load-bearing range in between is unmapped.

Run 20260816T013744, delegations D003/D004/D006/D008 (hard stop, 3 solvers, all ~0%), D017
(Explicit port, named the untried soft-connector lever), D018 (soft connector, 3x stiffness,
48.6% -- ARCHIVED here, data/idea_odbs/20260816T013744_D33_kissing_pair/), D019 (soft
connector, 15x stiffness, collapsed to 5.1%, self-clearance check). H3.

FOOTNOTES: [1] Liu, Ennis & Coulais (2024), "Tuning the buckling sequences of metamaterials
using plasticity," arXiv:2410.16452. [2] Dharmavaram, Ebrahimi & Ghosh (2021), "Coupled
Bend-Twist Mechanics of Biomimetic Scale Substrate," arXiv:2108.10976. [3] Hima, Bigoni &
Dal Corso (2022), "Buckling vs unilateral constraint for a multistable metamaterial element,"
Phil. Trans. R. Soc. A, arXiv:2205.02034.

WHY THIS IS THE FIRST NON-ZERO RESULT IN THE FAMILY'S HISTORY: every prior attempt (D003,
D004, D006, D008, D017 -- five delegations, one hard *CONNECTOR STOP formulation, three
different solvers) produced ~0% compression because a sudden/rigid contact force breaks an
implicit solver's Newton iteration the instant the stop engages -- a NUMERICAL failure, not
evidence the mechanism is bad. D017's own closing lines named the fix nobody had tried: not
another solver, a different constitutive law for the stop. D018 did exactly that.

WHY THE RESULT IS STILL UNCONFIRMED, NOT A WIN: D019 raised the stiffness 5x (to 15x beam
bending stiffness) specifically to check whether a stiffer contact behaves differently from a
softer one, the way a genuinely load-bearing contact should. It didn't -- Tier-1 self-
clearance was within 0.01mm either way, and compression COLLAPSED to 5.1% rather than staying
high or improving. That is consistent with the soft law being nearly inert at these
stiffnesses (not really constraining anything, just failing to crash), which would mean 48.6%
is closer to "what a slightly-regularized no-contact solve reaches" than "what self-contact
stiffening buys." The honest state: real numerical progress, unconfirmed physics. H3 stays
OPEN.

sigma_peak is normalised by n_longerons_effective=6 (2 x n_corners), per this hypothesis's own
comparability requirement (each corner replaced by 2 independently-anchored beams) -- verified
directly against the ledger's own n_longerons_effective column, not assumed.
-->

---
class: idea-slide
layout: two-cols-header
---

# D34 &middot; Graded, contact-decoupled two-storey mast

::left::

<div class="text-sm leading-snug">

- **What:** A two-storey mast where storey 1 (deliberately weaker: shorter pitch/thinner
  section) is physically separated from storey 2 by a gap that only closes by CONTACT — storey 2
  carries zero load until storey 1 fully collapses, then absorbs compression fresh, like a second
  spring engaging once the first bottoms out. Contact-decoupled, unlike the closed `asym_storey`
  family, which rigidly ties both storeys' motion from t=0.
- **Origin:** Liu, Ennis &amp; Coulais 2024&sup1; — the same layer-by-layer programmed
  buckling sequence grounding D33, applied here as discrete storeys rather than a single
  member's self-contact.
- **Stats:** n=62 &rarr; 22 coil &rarr; 0 riks &rarr; 0 good
  quartiles unavailable — **zero designs reached formal Riks convergence**, under 3 contact
  laws / 2 solvers
  cleared: **none** (0 decided) &middot; novel: **untested** — never got to demonstrate a
  second rise
  best good: none (0/62 passed every criterion)
- **Verdict:** POWERED &middot; REFUTED &middot; this 2-storey architecture<br>
  Two numbers, one reason: the raw solver runs to 76% compression with no crashes, but this
  study only counts compression BEFORE the first criterion violation — storey 1's own material
  strain crosses Bessa's 2% limit almost immediately, capping the CITABLE compression at 3.9%,
  long before storey 1 could land and hand off to storey 2. The staged mechanism never
  demonstrates anything: storey 1 fails first, under every solver/contact law — a design limit,
  not a numerical one.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 415px">
  <div class="flex items-center justify-center" style="height: 140px">
    <img src="/gifs/D34_staged_storey_mini.png" style="max-height: 140px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 240px">
    <img src="/gifs/D34_staged_storey_native.gif" class="rounded shadow-lg" style="max-height: 240px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-60 text-center">storey2_growth_ratio=31.7&times;: staging works, mcs only 1.5%.</div>
</div>

<!--
**Input space:** ratio_d1&isin;[.01,.04], ratio_pitch1&isin;[.13,1.04] — storey 1 (deliberately
weaker) section/pitch. ratio_d2&isin;[.023,.073], ratio_pitch2&isin;[.30,1.20] — storey 2
section/pitch. twist_angle1, twist_angle2&isin;[0,&pi;/2] — per-storey pretwist.
ratio_top_diameter&isin;[0,.8] — whole-mast taper, same range every family uses.
stop_engagement_fraction&isin;[.05,.85] — solid-height at which storey 1 lands and storey 2
begins carrying load. Fixed: n_longerons&isin;{3,4,5,6} (categorical), ratio_shear_modulus=.3677.

**Seed:** BARREN, fully — widening storey 1 closed first (105 evals, mcs stuck at 35.6%). A
follow-up gave the *thinner*-storey-1 signal proper statistical power (120 more evals, same
unrestricted box): the effect is real and holds up under scrutiny, but every slenderness-linked
dimension on BOTH storeys moves the same way — it's the study's own already-closed
kinematic-depth-cap wall reasserting itself, not a storey-1-specific escape. Best achieved
(20.5%) is worse than the wide-direction campaign's own best. `staged_storey` (this slide's own
oracle) was not re-run — same root cause, independently confirmed twice now via a different
oracle.

Run 20260816T013744, delegations D005/D007/D009/D010/D011/D013/D014/D015. H4.

FOOTNOTES: [1] Liu, Ennis & Coulais (2024), "Tuning the buckling sequences of metamaterials
using plasticity," arXiv:2410.16452.

EIGHT DELEGATIONS, ONE DESIGN-LIMIT DIAGNOSIS. D005 confirmed genuine staging is achievable
(storey2_growth_ratio up to 82.68x). D007's 32-point pilot converged nothing (0/9
Stage-2-attempted, all stalling 1.5-2.5% compression). D009 ruled out an easy fix
(stabilization already on). D010 tried linear/exponential soft-penalty contact -- still
nothing (0/4). D011/D013 escalated to Abaqus/Explicit dynamics, a materially different solver
built for exactly this class of contact-chattering problem, and it worked NUMERICALLY: 76%
raw compression, no more crashing. Then D013 found the real answer: the citable (windowed)
compression metric never moves because storey 1's own local strain crosses the 2% limit
almost immediately, independent of solver or contact law. D014's targeted 20-design sweep
found a narrow escape (extreme storey-1 slenderness flips the ordering in 2/5 designs);
D015's Explicit re-test showed the flip didn't survive the solver change. Registered
120-180-eval adaptive BO campaign never ran -- blocked at every stage by this same
design-specific issue, not by search budget.

THE GIF'S DESIGN (storey2_growth_ratio=31.65, ring_passthrough=False, riks_odb archived at
data/idea_odbs/20260816T013744_D34_staged_storey/) is a clean, Standard-solver demonstration
of staging actually happening -- storey 2 visibly far less deformed than storey 1 -- chosen
over the family's more dramatic Explicit-engine points (up to 82.68x growth) specifically
because render_odb.py could not render an Explicit-dynamics ODB from this family at all (see
this run's summary-slide notes): its per-frame displacement field is keyed differently, and a
separate ring-schematic-overlay bug (fixed as part of this update) crashed on this topology's
node layout regardless of engine. Not a cherry-picked "best" number -- per the deck's
no-winner convention, a typical, cleanly-renderable member of the search. It is still NOT
feasible: mcs_windowed=0.015 (1.5%), far short of the 0.80 floor, for the same storey-1-strain
reason as every other point in this family.

sigma_eigenvalue/mcs_windowed/mls_windowed quartiles cannot be reported over the Riks-
converged population per contract rule 3(c) because that population is empty (riks_converged
== 0 for all 62 rows in this run's ledger) -- stating a quartile line anyway would fabricate
data from zero observations.

WIDEN/THIN STOREY-1 FOLLOW-UP (2026-08-23, ad-hoc worktree-isolated investigations, not a
registered run -- ran against H12's own `graded_storey` oracle, a distinct but mechanistically
identical family, NOT this slide's own `staged_storey`). Widening storey 1's strain-relevant
bounds: 105 evals, mcs stuck at 35.6% (2.2x short), unanimous single-criterion failure. A
follow-up gave the *opposite* (thin storey-1) direction proper statistical power: 120 more
evals over the same unrestricted box, pooled with the first campaign via Fisher-z
meta-analysis -- rank correlation of ratio_d1 against mcs_windowed: pooled rho=-0.30,
combined p=0.0009 (Holm-significant). But `ratio_pitch1` (+0.385), `ratio_pitch2` (+0.278),
`ratio_d2` (-0.238), and `n_longerons` (+0.312) all move mcs_windowed the same direction at
similar significance -- the signature of the study's own slenderness-driven kinematic-depth-cap
relationship applying identically to both storeys, not a storey-1-specific mechanism. Best
achieved at the thin extreme: mcs=20.5%, worse than the wide campaign's own 35.6%.
-->

---
class: summary-slide
---

# Run `20260814T015148` — summary

<div class="text-sm leading-snug">

The run that found out **contact has never engaged.** Two contact-exploiting mechanisms, 33 evals,
and **every one of the 21 finite &sigma;_peak values is the same number** — `0.6071319332676687`,
the incumbent, bit-identical. Because nothing ever touched, every converged design *was* the
baseline rectangle wearing a new pre-processor.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1/H2 | A secondary elastic **"stop"** engaging after the primary hits its strain limit adds a second load path (Florijn 2014) | **?** | 6 delegations, 20 solves, two FE constructions. When one finally engaged, salvage showed the design was already decided: **the primary crosses 2% strain at 5.9% compression** (mcs .910&rarr;.054), ~600 increments *before* the stop engages | D31 |
| H3/H4 | A shallow **conical disc** changes where the coil bears and raises &sigma;_peak | **?** | Below the geometric onset 18/18 converge with **zero engagement**; at or past it **7 of 8 diverge** on overclosure chatter. No design both converges *and* engages | D32 |
| **H5** | Ground/disc contact **never engages inside the evaluation window** for this study's feasible designs | **?**<span class="opacity-60">*</span> | **CPRESS = 0 at every frame** for BOTH confirmed anchors — `run17_rectangle` (rectangular) and `bessa_point` (circular), structurally unrelated — with COPEN pinned at each design's fabrication standoff throughout | — |

**\*narrow verdict only.** H5 was self-corrected down from a whole-paradigm absence claim: two
anchors are not search power over a continuous space (Charter §2). The mechanism behind it —
`ground_offset` scaling with the same size that bounds the coiling bow — is stated, not tested.
**And the study's standing position, stated plainly: the 2&times;-Bessa bar has been cleared many
times over; the novelty gate has never been cleared once.** That, not the size of &sigma;_peak, is
the blocker.
&nbsp;·&nbsp; **Cost: $35.83** (33 evals, 13 delegations, 5.8 h of 18 h), GATED on the 4th attempt

</div>

<!--
READ THE HEADLINE CORRECTLY, BECAUSE IT IS EASY TO UNDERSELL: this run produced no new design and
no supported mechanism, and it is still the most consequential run in a fortnight -- because
contact has been NOMINALLY ON since 2026-08-06 while being INERT for every feasible design. Every
"contact-era" number this study has quoted for a feasible design is contact-free in substance. The
2x2 recorded in docs/FLAKY_DESIGNS.md ("contact costs 1.54x wallclock and zero convergence") is
consistent with that and now reads differently: of course it cost nothing, it never happened.

WHY ALL FIVE VERDICTS ARE INCONCLUSIVE AND WHY THAT IS CORRECT. The strategizer self-corrected
three of them DOWN from SUPPORTED/FALSIFIED under the validator, explicitly on Duhem-Quine
grounds: a design that fails to converge has not measured the absence of an effect, it has failed
to run the test. Its own words on H3: "that is a test failure (Duhem-Quine), not a measured
absence of effect, and an untested gap remains at 0.16." That is the best epistemic behaviour in
the series, and it is why the negative is trustworthy.

THE DETAIL THAT DECIDES BOTH MECHANISMS. In the secondary-stop family the only FEASIBLE rows are
n_stops = 0 -- the control. In the shaped-disc family the best feasible row is cone_rise_ratio =
0.0 -- the flat disc, also the control. In both cases the mechanism-bearing designs either did not
converge or did not engage. A family whose only feasible member is its own control has not been
tested; it has been outlined.

THE COUPLING FINDING, which is the one to act on: any additional beam member coupled to the ring
reference points collapses the primary's strain margin almost immediately. That is the
over-constraint docs/FLAKY_DESIGNS.md flags as UNCHECKED for element-based families ("their top
rings descend onto the same floor, so the exposure exists. This row is here to say nobody has
looked"). Somebody has now looked, and it bites.

COST SHAPE TELLS THE STORY WITHOUT READING A WORD OF SCIENCE: datagenerator $28.47 across 11
calls (79%) on build debugging; implementer $0.25, one call. No campaign ran. The strategizer's
retrospective names the open question honestly -- it allowed 6 debugging delegations on one
mechanism and says it has "no clean signal for where the 'stop debugging, it's a build wall not a
science question' line should sit versus PREMATURE CONVERGENCE's instruction not to abandon a
search too early."

AND IT CLOSED WITH 12.2 h UNSPENT. Not from ignorance: D014's report ended "wall budget remaining:
12.49h of 18.00h". But the transcript contains ZERO reasoning about the clock -- the agent's loop
terminates when the deliverable passes the gate, and 1h40m of the run's tail was notebook
write-up and four gate attempts. The 2026-08-13 PS line telling it to spend the budget was read
and changed nothing, because prose cannot beat a terminal state.
-->

---
class: idea-slide
layout: two-cols-header
---

# D32 &middot; Shaped (conical) ground-disc contact surface

::left::

<div class="text-sm leading-snug">

- **What:** Replace the flat rigid ground disc with a shallow axisymmetric **cone**, so the coil
  bears on a slope and the bearing point migrates as it descends.
- **Origin:** analogy from shell-buckling and origami-confinement literature — and the *cheap*
  half of the run's contact program: it changes only the rigid surface, leaving the primary member
  and its coupling scheme exactly as validated.
- **Stats:** n=26 &rarr; 26 coil &rarr; 19 riks &rarr; 19 good (5.41&times; Bessa)
  p50/p90/p100 — &sigma;_crit: .77/.77/.77 &middot; mcs: .91/.91/.91 &middot; mls: .0198/1/1
  cleared: **19 of 19 &ge; 2&times; Bessa — all 19 the incumbent's &sigma;_peak to 16 s.f.**
  &middot; novel: **no** — reshapes the rigid *fixture*, not the design
  best good: **cone_rise_ratio = 0.0**, the flat disc — the family's own control
- **Verdict:** BLOCKED &middot; UNKNOWN-NO-EVIDENCE &middot; cone engagement<br>
  Below the onset (rise &le; 0.15) 18/18 converge with **CPRESS = 0** — the cone is there, never
  touched. At or past it (0.17–0.30) **7 of 8 diverge** on overclosure chatter. Nothing in this
  parameterisation both converges *and* engages: a **test failure, not a measured null**.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D32_shaped_disc_cone_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 265px">
    <img src="/gifs/D32_shaped_disc_cone_landscape.gif" class="rounded shadow-lg" style="max-height: 265px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-60 text-center">rise 0.15 (largest that converges); CPRESS never leaves zero.</div>
</div>

<!--
**Input space:** cone_rise_ratio&isin;[0,.30] — cone height as a fraction of its base radius (0 =
flat disc, the family's own control). Fixed: everything else at the incumbent (a=.00921,
b=.03324, pitch=.68128, rtd=.04444, n_long=3).

**Seed:** BARREN, now settled — this week's Explicit-dynamics escalation (H3, run
`20260819T022742`, D019) resolved the conditioning blocker: at every tested loading rate the
event is genuinely non-quasi-static (ALLKE/ALLIE far above threshold), not a solver artifact
masking real force amplification. No further evaluation warranted without a different way of
engaging contact.

Run 20260814T015148, delegations D008-D011 and D014, H3/H4. scripts/supercompressible_riks_shaped_disc.py.

WHY THIS SLIDE MATTERS MORE THAN ITS OWN VERDICT: this family is what surfaced H5. Chasing why a
cone never gets touched is what made somebody finally read CPRESS on the ANCHORS -- and find zero
there too. The idea failed and produced the run's one durable finding.

THE SHAPE OF THE WALL, worth internalising before proposing any contact mechanism here: the
converging region and the engaging region appear to be DISJOINT in this parameterisation. Below
onset the geometry guarantees no touch; at onset the solver meets a hard first-contact overclosure
and quits. That is not "the cone does nothing" -- it is "the cone cannot be evaluated". D014 was
specifically the severe re-test after the critic rejected the first, safety-margined sweep as
inadequate, and it is the reason the verdict reads a test-failure call (now BLOCKED ·
UNKNOWN-NO-EVIDENCE under the current taxonomy; this paragraph originally justified the
pre-migration INCONCLUSIVE tag -- corrected 2026-08-31, verdict audit -- the same "cannot be
evaluated, not falsified" reasoning still applies).

The one converged point at rise 0.15 is genuinely useful as a null control: it proves the shaped
disc is correctly built and inert, so the divergence at 0.17 is about contact conditioning and not
about a broken model.
-->

---
class: idea-slide
layout: two-cols-header
---

# D31 &middot; Secondary elastic "stop" member

::left::

<div class="text-sm leading-snug">

- **What:** Short stocky members carrying nothing at first, **engaging only once the primary
  longerons near their 2%-strain limit** — a contact-triggered stiffness jump.
- **Origin:** Florijn, Coulais &amp; van Hecke 2014, *Programmable Mechanical Metamaterials*. It
  attacks the kinematic law head-on: a *separate* member escapes the ring-rotation curvature
  compatibility (&kappa;_max &asymp; 1/R_mean) that caps one continuous longeron.
- **Stats:** n=6 &rarr; 6 coil &rarr; 2 riks &rarr; 2 good (5.41&times; Bessa)
  p50/p90/p100 — &sigma;_crit: .77/.77/.77 &middot; mcs: 0/.91/.91 &middot; mls: unmeasured
  cleared: **2 of 2 decided &ge; 2&times; Bessa — but both are `n_stops = 0`**, the control
  &middot; novel: **untested** — the stop never carried load
  best good: `n_stops = 0` &rarr; &sigma;=.6071 mcs=.91 — the run-17 rectangle again
- **Verdict:** BLOCKED &middot; UNKNOWN-NO-EVIDENCE &middot; stop engagement<br>
  20 solves, 6 delegations, two independent FE constructions (separate Part+Instance, then wire
  edges on the *same* Part). The one solve whose stop engaged was **already decided against**: the
  *primary's* strain crosses 2% at **5.9% compression**, mcs .910 &rarr; **.054**, ~600 increments early.

</div>

::right::

<div class="flex flex-col items-center justify-center gap-1" style="height: 440px">
  <img src="/gifs/D31_secondary_stop_sigma_mini.png" style="max-height: 150px; max-width: 100%" />
  <div class="text-xs opacity-60 text-center">n_stops=0 (solid, run-17 rectangle) vs n_stops=1 (dashed).</div>
  <img src="/gifs/D31_secondary_stop_native.gif" style="max-height: 200px; max-width: 100%" class="rounded shadow-lg" />
  <div class="text-xs opacity-60 text-center">n_stops=1, the only build whose stop engaged.</div>
</div>

<!--
**Input space:** ratio_stop_d&isin;[.02,.03] — stop member diameter. stop_engagement_fraction
&isin;[.5,.8] — compression fraction at which the stop is meant to contact. stop_radial_ratio
&isin;[.4,.6] — stop's radial placement between the mast axis and the primary longerons.
n_stops&isin;{0,1,3} — discrete count, not a continuous dial. Fixed: primary longeron at the
incumbent.

**REAL CHART ADDED 2026-08-28 (same gap as D28/D38 -- a coiling GIF with no companion stress
chart).** n_stops=1's real ODB
(`/oscar/scratch/eaguerov/sc_oracle_secondary_stop/riks_459047fed9ee43a48e7ce61ec6784c12/`, 102
frames, no `results.pkl` -- extracted directly via read-only Abaqus field-output access, U/RF at
`ZTOP_REF_POINT` and `E` across all elements) does not have a corresponding entry in this
family's own `experiment_data` ledger (6 rows, all n_stops=1/3 unconverged with no `riks_odb`) --
it is a separate render-job re-solve (job 4961555), not one of the 6 ledgered points. Corrects
the previous caption's "46.5% by the end": that number was the raw 46.53mm descent divided
incorrectly -- the real value is mcs=68.3% raw (unwindowed), with strain crossing 2% at
mcs=6.46%, independently confirming the 5.9%/mcs=.054 figure already in the Verdict to within
this extraction's own precision (a cruder max-principal-or-component strain measure than the
study's own beam-section-point convention).

**Seed:** BARREN *as coupled here* — any added beam member tied to the ring reference points
destroys the primary's strain margin. Untested until that is fixed.

**2026-08-29 update (run 20260829T005522, D007/D017):** the fix named above WAS tried. D017
attached the stop to a genuine FE node on the primary longeron's own mesh instead of any ring
reference point or driven surface -- zero shared equations with ZTOP_REF_POINT -- and it still
diverges at the identical mcs~0.51 with the identical residual signature every other
construction has shown since D003. This conclusively rules out "shared ring-RP DOF set" as the
cause across five independent attachment/base variants now (D004 x4, D007's contact, D017's
primary-node coupling); the standing explanation is that ANY new Part+Instance perturbs
Abaqus's own internal equation numbering, independent of what it connects to. One combination
remains untried: `stop_construction="same_part"` combined with this longeron-midspan
attachment (each tested individually, never together) -- flagged as the most promising
untried lead, not attempted (outside that delegation's authorized scope).

Run 20260814T015148, delegations D003-D006 and D012-D013, H1/H2. 6 datagenerator delegations,
$28.47 of the run's $35.83.

THE FINDING IS THE COUPLING, NOT THE STOP. D012 refuted "separate-instance-ness" as the cause --
n_stops=3 built as wire edges on the SAME Part still diverged, at an even earlier LPF 0.257, with
the same causal fingerprint tied to the primary's own Kinematic-coupling hinge-release scheme. So
the defect is not how the stop was attached but that ANY additional beam member coupled to those
ring reference points collapses the primary's strain margin. docs/FLAKY_DESIGNS.md predicted
exactly this exposure and recorded that nobody had checked it ("Element-based families + coupling
-- the same over-constraint has NOT been checked... This row is here to say nobody has looked").
Somebody has now looked. That row needs updating to n=1 with this run's evidence.

WHY IT IS "UNTESTABLE" AND NOT "FALSIFIED": the mechanism's own prediction was never reached. The
stop was supposed to engage AFTER the primary neared its strain limit; instead the primary blew
its limit at 5.9% compression, which is a broken model, not a tested idea. D013's salvage is what
established that -- and it was free, following docs/TRAPS.md's own "a stalled solve can still
decide a design" logic on a partial solve nobody had planned to read.

ON THE SIX DELEGATIONS. Each successive attempt was required to test a genuinely DIFFERENT cause
(contact settings -> base DOF -> shared property -> arc-length control -> construction strategy),
and the strategizer stopped only when two fundamentally different constructions both failed. That
is a defensible discipline. It is also $28 and most of a run, and its own retrospective flags the
missing signal: where the line sits between "keep debugging" and "this is a build wall, escalate
it out of the run".
-->

---
class: summary-slide
---

# Run `20260812T222030` — summary

<div class="text-sm leading-snug">

The run that **reversed yesterday's lead and then disqualified it** — and stopped at 3.3 h of an
18 h budget because its own novelty hypothesis said the mechanism could not count.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Flare + pre-coil together contain a feasible design clearing 2&times; Bessa | **&#8253;** | *Self-corrected to INCONCLUSIVE under the critic:* the campaign was **anchor-seeded**, so a point satisfying H1 existed before it ran. A test that cannot fail is not a test (Charter §2) | D30 |
| **H2** | **Flare** is the dominant lever; pre-coil contributes little | &#10007; | **Reversed.** &rho;(helix_wrap, &sigma;_peak) = **&minus;0.392** vs &rho;(taper) = +0.287, Holm-corrected over 5 dims, n=36. Pre-coil is the *larger* effect — and its sign is **negative** | D30 |
| **H3** | Neither lever clears the study's **originality** bar, even if it clears 2&times; Bessa | &#10003; | Pre-coil = intrinsic-curvature strain relief, **settled Kirchhoff-rod theory** (Drozdov &amp; Rabin 2000; Gomez &amp; Lauga 2024) transplanted into this host. Flaring = a **sign extension** of Bessa's own `ratio_top_diameter` on unchanged topology | — |
| **H4** | Nothing in the *decided* flare+pre-coil region beats the incumbent | &#10003; | 22 feasible of 216, 20 with wrap&ne;0, **8 clear 2&times; Bessa**, best **0.5007 kPa = 4.46&times; Bessa** at wrap &minus;1.10 — but 82% of the 0.6077 incumbent. Rescoped: deep wrap is *excluded*, not counted | — |

**The deep-wrap region (\|wrap\| 2–5) is numerically inaccessible, not bad:** of 107 rows, **zero**
reached a coiling mode and 19/19 Stage-2 solves crashed before any finite &sigma;_peak. Reported OPEN.
&nbsp;·&nbsp; **Cost: $14.59** (216 evals, 5 delegations, **3.3 h of 18 h**), GATED on the 4th attempt

</div>

<!--
THE FINDING IS ABOUT THE CONTRACT, NOT THE DESIGNS. This run did the science well and then
stopped early on purpose. The strategizer's own words on the least-certain call: it judged one
25-point probe was right, "not so much that I was chasing a mechanism already independently
disqualified on novelty (H3)". So the binding constraint on this study is no longer the search,
the oracle, or the budget -- it is the objective. Two levers now have real evidence behind them
and NEITHER can be rewarded as written. That is the reconciliation question, arriving as a
measurement rather than an opinion.

H2's reversal is the substantive scientific news and it CONTRADICTS the D30 slide written from
the previous run. Yesterday pre-coil looked like the study's top lead on a ~5x strain-relief
measurement. Measured against sigma_peak over 36 decided designs, more pre-coil means LESS load
(rho = -0.392) -- which is exactly the trade the previous run flagged as unmeasured (sigma_eig
falling 2.36 -> 0.245 kPa) and could not close before it ended. The strain relief is real; it
just does not buy load. Note neither correlation survives Holm at p<0.05 (0.069 and 0.268), so
this is a reversal of the PREDICTED ORDERING, not a confirmed strong driver.

WHY H1 SELF-CORRECTED, and why it is a good sign: the strategizer first marked it SUPPORTED with
a "degenerate but supported" caveat. The AskForFeedback critic called that a Charter §2/§3
violation -- the search was seeded with the already-feasible anchor, so H1's existence claim was
guaranteed before any solve. It reversed itself to INCONCLUSIVE and routed the substantive
question to H4. Three AskForFeedback rounds each caught distinct real issues.

THE BUG WORTH KEEPING. D004's worker computed feasibility with `rpt is False` against a ledger
column stored as 0.0/1.0, so `feasible_recomputed` was False for every row and the analysis JSON
reported 0 feasible designs where the true count was 21. Caught only because the delegation
re-derived the predicate through QueryStore instead of trusting its own script's output. A
post-hoc analysis script reading ledger data is not itself ledger-authoritative.

Cost composition is the mirror image of the last run: implementer $7.29, critic $4.42,
datagenerator $1.63, literature $1.25. Opus sat on the datagenerator, which was the cheapest
substantive node here -- a $1.63 slot. The strategizer's own transcript cost is again absent from
telemetry, so $14.59 remains a floor.
-->

---
class: summary-slide
---

# Run `20260812T014026` — summary

<div class="text-sm leading-snug">

The run that **explained the study**: it falsified its own opening idea, then extracted from the
failure a law accounting for all 28 backlogged families — and showed the incumbent is not a lucky
design but the one that reached the ceiling.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1/H2 | A coaxial rigid **mandrel** the longerons wind onto creates a load-bearing second branch | &#10007; | The coiling mode is **radius-preserving** (envelope 47.79–50.00 mm), so internal confinement is unreachable *in principle*. Contact force **0.0 at all 70 samples** | D29 |
| **H5** | &kappa;_max is a **kinematic invariant** of the ring geometry, not of the member | &#10003; | `mls_full/c` = .021600/.021658/.021641/.021714 across a **2&times; depth change**; &plusmn;15% over a 24-pt LHS, residual tracks taper (Spearman .786) as &kappa;&asymp;1/R_mean predicts | — |
| **H7** | That depth cap is **binding**, not descriptive | &#10003; | No straight-longeron design with c &ge; 1.00 mm reaches 80% inside the 2% budget — whatever is done with width, storey height or taper | — |
| **H9** | The cap is 0.02/&kappa;_max, and **flaring moves it** | &#10003; | A depth infeasible at zero flare becomes feasible at taper &minus;0.45, purely because the cap moved. The run's only severe confirmation | — |
| H4/H6 | **Pre-coiling** relieves the strain wall (strain is c &times; curvature *change*) | **?** | Corrected 2026-08-26: wrap 4.5 reached 61.5% compression at 0.445% strain (a mast_height arithmetic error, not a ~5&times; relief). Also retracted within-run: wrap&ge;3 designs self-interpenetrate from mcs&asymp;0.39 on — full detail on D30's own slide | D30 |

**&sigma;_peak &prop; E·w·c³/L², c capped kinematically and w by slenderness&ge;10; `run17_rectangle`
sits at 99.7% of the cap.**
&nbsp;·&nbsp; Best new design **0.3451 kPa = 3.08&times; Bessa** (clears; not novel) &nbsp;·&nbsp; **Cost: $79.55**, 125 evals, 10.4 h of 18 h

</div>

<!--
GATED on the 3rd critic attempt (NOTED -> NOTED -> PASS), 0 ERROR_RETURN across 14 diagnostics
events. First run with a mixed roster where Opus 5 drove the strategizer and Sonnet 5 the workers.

READ THE BAR CORRECTLY. Five NEW feasible designs cleared 2x Bessa this run -- 0.3451 (3.08x),
0.2931, 0.2664, 0.2549, 0.2545 -- so the numeric half of the objective was met repeatedly. None is
novel: the best sits at mcs_at_peak = 0.0645 (the same pre-buckling peak as everything else) with
mandrel_engaged = 0, and D29_oracle_mandrel's own docstring notes mandrel_ratio=0 reduces exactly to
the rectangular family. Reporting this run as "nothing beat 0.6077" is the wrong yardstick -- the
incumbent is context, not the bar -- but the novelty half failed for the third run running.

WHY THE MANDREL FALSIFICATION IS WORTH MORE THAN THE DESIGNS. It is not "we tried and it didn't
help": the coil never moves inward, so there is no radius for an internal body to govern. Nine
confined evaluations, four mandrel radii up to the geometric limit, four cross-sections, and the
contact force is identically zero in every history sample. That closes the whole class of
internal-confinement ideas, not one design.

THE COROLLARY NOBODY HAD STATED. Curvature is distributed, not localised: peak/mean strain along
the member = 1.10, peak at arc ~0.35, never at a ring joint, and joint strain is 66-89% of peak.
So there is no joint-compliance lever either -- the strain really is c*kappa, everywhere.

WHY IT CLOSED WITH 7.6 h UNSPENT, in the strategizer's own words: "whether to keep spending budget
on the flare thread after H8 stalled. It was clearly *not* the novel mechanism the problem
statement demands... I continued because the run's own measured law made a sharp, falsifiable,
out-of-sample prediction there... It produced the run's only genuinely severe confirmation (H9) and
its best new design -- but it also spent ~3 h on a direction I knew in advance could not satisfy
the novelty half of the objective, and I remain unsure that was the trade the system wanted."
That is a real tension in the contract, not a defect in the run: the highest-value science
available was testing a risky consequence of its own law inside a non-novel parameter range. The
objective does not currently say whether that is worth doing. Until it does, the study's
best-evidenced lever is unrewardable.

INFRASTRUCTURE THE RUN LEFT BEHIND, now promoted to gold (commit 16c7e84): bo/D29_oracle_mandrel.py and
bo/oracle_helical.py with four scripts/ pre/post-processors -- ~$35 of build cost that the next
fresh run would have deleted, and the only implementation of the pre-coil family. The agent added
a MandrelOracle factory to bo/datagen.py in exactly the adapter's intended shape, and
oracle_helical.evaluate takes max_solve_seconds -- both pieces of 2026-08-10 infrastructure used
as designed by the first run that saw them.
-->

---
class: idea-slide
layout: two-cols-header
---

# D30 &middot; Pre-coiled (helical) longeron

::left::

<div class="text-sm leading-snug">

- **What:** Build the longeron already wound as a helix of `helix_wrap` turns, so coiling
  supplies only the *remaining* curvature.
- **Origin:** this run's own law. Strain is c &times; curvature **change**, not curvature — a member
  born at &kappa;&#8320; travels only &kappa;_max &minus; &kappa;&#8320;, so the cap 0.02/&Delta;&kappa; relaxes.
- **Stats:** pre-coiled (wrap&gt;0): n=30 &rarr; 3 coil &rarr; 2 riks &rarr; 0 good — **both riks solves hit the 600 s cap**
  p50/p90/p100 — &sigma;_crit: .97/4.55/6.57 &middot; mcs: 0/0/.339 &middot; mls: unmeasured
  cleared: none here — the next run cleared 8 with wrap&ne;0, best 0.5007 = 4.46&times; Bessa
  &middot; novel: **no** (Kirchhoff-rod theory, H3)
  best good: none. wrap 4.5 reached 61.5% compression at 0.445% strain before its loading point
  reversed (strain never crosses 2%) — corrected 2026-08-26 for a mast_height arithmetic error;
  full audit trail in notes.
- **Verdict:** POWERED &middot; REFUTED &middot; wrap-vs-load (accessible depths)<br>
  <span class="opacity-60">(revised 2026-08-26)</span> The relief is real — **0.445% strain at 61.5% compression**, where the matched straight control
  had blown 2% by 26.2% — but it buys no load (&rho;(wrap, &sigma;_peak) = **&minus;0.392** over 36
  decided designs), it is not novel, and the family never approached 80%.

</div>

::right::

<div class="flex flex-col items-center justify-center" style="height: 420px">
  <img src="/gifs/D30_precoil_wrap45_native.gif" style="max-height: 340px; max-width: 100%" class="rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-1 px-4 text-center">wrap 4.5, stopping at the reversal (frame 156/785).</div>
</div>

<!--
**Input space:** helix_wrap&isin;[-0.3,6.0] — pre-coiled turns built into the longeron before any
compression is applied. a&isin;[.004,.014], b&isin;[.01,.045] — cross-section semi-axes.
ratio_pitch&isin;[.25,1.5]. Fixed: n_longerons=3, ratio_top_diameter=0, n_storeys=1,
imperfection=.067.

**Stats correction, full audit trail (trimmed from the visible bullet 2026-08-28 to fix a
confirmed 88px render clip, headless-measured):** **CORRECTED 2026-08-26 (deck audit):** wrap
4.5, c = 2 mm reached 61.5% compression at 0.445% strain, then its loading point reversed and
travelled all the way back past its own start (net +63.5mm ascent by the end of the 785-frame
history); strain never crosses 2% anywhere in that history. The 2026-08-14 correction's own
arithmetic used mast_height=100mm; the oracle's real formula
(n_storeys&times;ratio_pitch&times;bottom_diameter, confirmed against both the geometry script
and the prescribed-displacement BC) is 50mm, exactly halving the true reading to a reported
"30.8%". (The pre-2026-08-14 "61.5%" figure this replaced was independently wrong for an
unrelated reason — `|U3|` counting upward travel as compression — so this is a coincidental
numeric match, not a vindication of that reading.)

**Seed:** BARREN as a load mechanism, **disqualified on novelty** (Kirchhoff-rod theory, H3).
The deep-wrap Stage-2 crash is an open solver problem, not a design lead.

Run 20260812T014026, H4/H6. The gif is the 839-increment solve (riks_847140cc): 785 frames in
step, of which 268 fall inside the mcs<=0.95 render window.

WHY THE ORIGINAL DRAFT VERDICT WAS "INCONCLUSIVE", NOT "SUPPORTED" (corrected 2026-08-31,
verdict audit: this paragraph pre-dates the CAMPAIGN·IDEA·SCOPE migration and argued for a
tag pair that no longer appears on this slide -- the reasoning below is why the family was
never called a clean win, and still applies to why REFUTED, not VALIDATED, is the current
call): the measurement is real and large, but it is one half of
a trade. sigma_eig dropping 10x across the same sweep is exactly what a pre-curved member should
do -- it is no longer a straight column, so its Euler load is not the relevant one -- and the
question was whether the POST-buckling branch recovers what the eigenvalue lost. The
rho(wrap, sigma_peak)=-0.392 correlation on the current Verdict line answers that: it doesn't.
This study has been burned before by reading a favourable half-measurement as a result
(docs/FLAKY_DESIGNS.md keeps a list of them).

READ THE RELIEF NUMBER CORRECTLY. 5x is not the depth cap moving 5x -- it is Delta_kappa
shrinking, which relaxes the cap on c for the SAME kappa_max. The kinematic invariant (H5) is
untouched: the rings still set kappa_max. Pre-coil changes where the member STARTS, and flaring
(H9) changes where it ENDS. They are independent levers on the same product, which is why testing
both is worth more than testing either twice.

THE 61.5% FIGURE WAS THE MAST GOING UP (post-mortem, 2026-08-14). This slide originally reported
"61.5% compression at 0.45% strain" and a "~5x strain relief", and PROBLEM_STATEMENT.md carried the
same sentence. Both were wrong. bo/response_metrics.py computed mcs from np.abs(U[2]), and
magnitude cannot distinguish a loading point descending from one rising. Read directly off the ODB
(sc_oracle_helical/riks_847140cc..., 785 history points, job 4972909):

    U3 min (true max DESCENT)   -30.769 mm  -> mcs = 0.6154   frame 132, LPF 0.5783
    crosses into POSITIVE                                     history pt 229, LPF 0.5894
    U3 max (net ASCENT)         +63.485 mm  -> abs() says 0.6349
    max |E| at the true peak     0.00445    (i.e. 0.445% strain)
    max |E| at the abs() peak    0.01418    (1.42%, not 0.45%)

So the design reached 61.5% compression at 0.445% strain, and the published pair took its
compression from one frame and its strain from another. The straight control blowing 2% by 26.2%
still stands, so relief is real -- but the two were never compared at equal compression and the
factor was never measured, which is why "~5x" is gone rather than rescaled.

SECOND CORRECTION (2026-08-26, deck audit item 2): this paragraph originally reported mcs=0.3077
for the -30.769mm descent, using mast_height=100mm. That number was never sourced from either the
oracle's own metric-reduction formula or the geometry-construction script -- both independently
compute mast_height = n_storeys * ratio_pitch * bottom_diameter = 1 * 0.5 * 100 = 50mm
(bo/oracle_helical.py line 456; scripts/supercompressible_riks_pretwist_helical.py lines 158+179,
and its own prescribed-displacement BC at line 816 uses the same 50mm). At the correct mast_height,
the true reading is mcs=0.6154 (61.5%), not 30.8% -- exactly double. This is numerically close to
the ORIGINAL, pre-2026-08-14 "61.5%" figure this whole postmortem exists to debunk, but that is a
coincidence, not a vindication: the original number was wrong for an unrelated reason (abs(U3)
counting the net +63.5mm ascent as compression), while this one is the true value at the actual
point of maximum real descent. Strain never crosses 2% anywhere in the 785-frame history, so the
"relief is real" conclusion is unchanged and, if anything, stronger than previously stated.

Fixed in c79a524 (`np.clip(-U[2], 0, None)`, plus the renderer's readout and a reversal cutoff so
a gif stops where the mast stops descending). Monotonic solves are unaffected, so no other
published number moves. Found by the advisor from this slide's own gif: "mcs goes up but the
design doesnt compress, instead it decompress. Possible bug."

THE LESSON IS NOT "CHECK FOR REVERSAL" -- that is a rule fitted to one accident. The general
failure is that this figure travelled from a delegation report into a run summary, into this
slide, and into the PROBLEM_STATEMENT without one independent read off the primary artifact, and
then steered two runs. docs/FLAKY_DESIGNS.md carries it under "claims that turned out to be
false" for that reason.

WHY THIS LOOKED NOVEL, AND WHY IT IS NOT (settled by run 20260812T222030, H3): the argument here
was that helix_wrap is a new degree of freedom with a new pre-processor, so a member manufactured
curved is a different design rather than a different point. The literature review answered it
directly -- spontaneous/intrinsic-curvature strain relief is settled Kirchhoff-rod mechanics
("general considerations concerning such naturally curved rods can already be found in the work
of Kirchhoff"), i.e. a known-mechanism transplant into this host geometry. A new parameter is not
a new mechanism. Left standing as written, because the reasoning that produced it is the exact
reasoning the novelty bar has to arbitrate.

The wrap<=0 rows (-0.3, -0.15, 0, 0.15, 0.3) are the sign-convention control: wrap=0 must
reproduce the straight family exactly, and does. Built as `signcheck` before the sweep ran, which
is why the sweep's numbers can be read as a curve rather than a scatter.
-->

---
class: idea-slide
layout: two-cols-header
---

# D29 &middot; Mandrel-confined coiling mast

::left::

<div class="text-sm leading-snug">

- **What:** A coaxial rigid cylinder inside the mast for the longerons to wind onto — hoping it
  governs the coiling curvature and adds a confined second load path once members bear on it.
- **Origin:** the run's opening hypothesis (H1/H2) — once the cross-section is capped, the only
  lever left is what the member coils *against*.
- **Stats:** confined: n=9 &rarr; 9 coil &rarr; 9 riks &rarr; 4 good (5.41&times; Bessa), radii .6/.7/.78/.83 (.83 = geometric limit)
  p50/p90/p100 — &sigma;_crit: 1.98/3.25/4.65 &middot; mcs: .45/.91/.91 &middot; mls: .0198/.0198/.0198
  cleared: **4 of 9 &ge; 2&times; Bessa — each duplicating its unconfined control** &middot; novel: **no**
  best good: mandrel=.6 a=.00921 b=.03324 pitch=.68128 &rarr; &sigma;=.6071 — **the run-17
  rectangle**: nine &sigma;_peak values take **four** levels, one per control, and contact force is
  **0.0 at all 70 history samples**.
- **Verdict:** POWERED &middot; REFUTED &middot; mandrel confinement<br>
  Mechanistically, the stronger kind. The coiling mode is **radius-preserving**: the envelope stays
  at 47.79–50.00 mm over the stroke, never moving inward, so there is no radius for an internal body
  to govern. That closes the whole class.

</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D29_mandrel_confined_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D29_mandrel_confined_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** mandrel_ratio&isin;[0,.83] — mandrel radius as a fraction of the geometric limit
(.83). a&isin;[.004,.014], b&isin;[.01,.045] — cross-section semi-axes. ratio_pitch&isin;[.25,1.5].
Fixed: n_longerons=3, ratio_top_diameter=.04444, n_storeys=1.

**Seed:** BARREN — as is any *internal* confinement. Confining from outside, or moving the
envelope (D30), is a different argument.

Run 20260812T014026, delegations D002/D003/D005/D010/D013/D017, H1/H2. bo/D29_oracle_mandrel.py and
scripts/supercompressible_{lin_buckle,riks,riks_pp}_mandrel.py are promoted to gold (commit
16c7e84) -- the family is closed, the machinery is not wrong, and mandrel_ratio=0 reduces it
exactly to the contact-migrated rectangular family, which is what made the control pairs free.

WHY THE BIT-IDENTICAL RESULT IS THE FINDING. A run that reports "the mandrel didn't help" has
learned about one mandrel. A run that shows the contact force is identically zero at every
sample, for every radius up to the geometric limit, has shown the mechanism cannot engage --
which is a statement about every design of this kind, and it holds without a single further
solve. The envelope diagnostic (D006) is what turned "no effect" into "unreachable in
principle".

THE SCOPE QUALIFIER, filed by the critic and worth keeping: the envelope was measured across four
DEPTHS of one fixed cross-section family. Radius-preservation is a property of how the rocking
mode works, so it is expected to generalise -- but a shell or open-section family whose coil
collapses inward would fall outside this falsification and would have to be re-measured. The
claim is "this coiling mode is radius-preserving", not "no coil ever moves inward".

THE COROLLARY. Curvature along the member is distributed, not localised: peak/mean = 1.10, peak
at arc ~0.35 (never at a ring joint), joint strain 66-89% of peak. So there is no
joint-compliance lever hiding here either -- the strain really is c*kappa everywhere, which is
what makes H5's cap binding rather than merely typical.
-->

---
class: summary-slide
---

# Run `20260809T230403` — summary

<div class="text-sm leading-snug">

First mixed-model run (**Opus 5 strategizer, Sonnet 5 workers**) and the first to take the contact
bet seriously. It built a mechanism law for *why* the family is capped, tested four escape
mechanisms and killed all four, then closed at 6.5 h of 12 h because the one remaining escape
needed a solver regime the 600 s cap forbade. **Its own deliverable states the novelty half of the
objective was not met.**

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | The straight-longeron two-ring topology is at its ceiling: coiling curvature is pinned to the ring radius (&kappa;&asymp;2/D<sub>1</sub>), capping winding-plane member depth near 2&nbsp;mm | **?** | Every escape attempt failed, but a ceiling claim cannot be established by four failures | — |
| H2 | &sigma;_peak is **always** set by the pre-coil instability — a later contact-mediated rise cannot set the objective | &#10003; | mcs_at_peak &lt; 0.30 for every design. The 6 apparent late peaks (one at &sigma;=245.8 kPa) were **truncation artifacts**: `window_n == history_n`, peak at the last computed increment | — |
| H7 | A multi-leaf (leaf-spring) longeron decouples depth from coiling curvature | &#10007; | `n_leaves=1` reproduced run-17 rectangle to 4 s.f.; `n_leaves=3` regressed 7.7&times; (&sigma;_eig 0.770&rarr;0.100) at 482&nbsp;s vs 84&nbsp;s | D28 |
| H8/H9 | H8: coil-mode critical load rises with torsional stiffness J (exponent&asymp;1). H9: set by the **strict minimum** of J vs. bending stiffness | H8 &#10003; / H9 &#10007; | H8: fitted d(log &sigma;_eig)/d(log J) = 0.9963, R&sup2;=1.0000, n=13. H9's sharp-minimum framing FALSIFIED — real behavior is a SOFT saturation once J exceeds bending stiffness by ~20&times;, not a hard minimum at parity | — |

**Best feasible = 0.6071 kPa — the incumbent rectangle, rediscovered** as the leaf-spring
family's own *regression control*. &nbsp;·&nbsp; **Cost: $56.03** (306 evals, 6.2 h)

</div>

<!--
Run stats: GATED on the 3rd critic attempt (REJECT -> REVISE -> PASS), evals_used=306, 12
delegations, 6.5 h of a 12 h budget, 1 ERROR_RETURN (a Confer-before-wake ordering slip on D004,
recovered). Strategizer claude-opus-5 confirmed at the process level (--model in the spawned
argv); all other nodes claude-sonnet-5 from config.yaml.

WHY IT CLOSED WITH 5.7 h UNSPENT -- from the strategizer's own retrospective, because this is the
most consequential thing the run revealed and it is about US, not about it: "PREMATURE
CONVERGENCE explicitly forbids closing while an affordable experiment could move an open
criterion... I made it because the mechanism law I had just established named the *only* remaining
escape (a section whose torsional constant collapses on demand) and simultaneously showed it is
unreachable here: beam elements carry one section per element, so it needs shells with
self-contact, measured in this study at 243-5072 s per solve against a 600 s cap." And its own
distinction: "'My search stopped improving' would not have justified closing; 'the one remaining
mechanism requires a solver regime the infrastructure cannot afford' is a statement about the
space and the tooling, not about my search."

That reasoning is sound GIVEN what PROBLEM_STATEMENT.md said at the time -- which was that the cap
is "a hard property" and that a family which cannot fit inside it "is not searchable, and the
honest move is to say so". Both justifications for the cap are COST arguments; presenting one as a
property of the oracle turned a budgeting default into a boundary on the design space. The PS has
since been rewritten (the cap is a movable default, licence tokens are the hard constraint), and
solves are now watchable and revocable in flight (bo/promises.py) with only FINISHED work counting
toward budget -- so cancelling is free and a generous cap is safe. Runs 4.5-8.0 h against a 12 h
budget, six in a row, was a symptom of this, not six independent judgement calls.

DO NOT INHERIT H1 OR THE "ONLY REMAINING ESCAPE" AS A BOUNDARY. Both were derived inside the BEAM
families this run searched. "The only escape needs shells with self-contact" locates where THIS
SEARCH ran out, not where contact-mediated designs live in general -- the space of unexplored
configurations is not indexed by element type. See docs/EVALUATION_UNDER_CONTACT.md.

THE H2 ARTIFACT IS WORTH STUDYING. Six designs appeared to peak near 50% compression, one
reporting sigma_peak = 245.8 kPa -- 400x the floor, and it would have been the headline. All six
had window_n == history_n and mcs_at_peak == mcs, i.e. the "peak" was the last frame before the
solve died: a truncated response, not a load rise. The strategizer found that signature itself and
ran D007 as a targeted falsification rather than banking the number. The legitimate n=4 design
shows the contrast (window_n 70 < history_n 73). This is exactly the window_closed_before_failure
convention doing its job.

CRITIC: call_001 REJECTed on notebook-ledger sync (H8 registered at 04:16 but absent from the
notebook, so a reader of the deliverable alone would not know it existed); call_002 REVISE;
call_003 PASS. One critic slip worth noting: its provenance check cleared the headline as "a
genuinely different, independently-converged design (different n_longerons)" -- but it compared
D011 against D005's n_longerons=4 design, not against the ANCHOR, which is also n_longerons=3. It
checked the wrong pair. The notebook's prose reached the right conclusion anyway.

INFRA DRIFT, classified: the Tier-1 self-clearance diagnostic (scripts/self_clearance.py + an
opt-in hook in the Riks post-processor) was PROMOTED TO GOLD -- it catches designs whose coil
interpenetrates, the same failure class as ring_passthrough one level down, at zero solve cost and
inert unless SC_TIER1_RADII is set; validated on the Bessa anchor at 58.9 mm minimum clearance.
The two leaf-spring pre-processors were ARCHIVED to scripts/superseded/ (family settled, machinery
preserved). Also filed: the literature provider was 403 rate-limited for the whole session, so
Pellegrino/Pasini full texts were unreachable, and the critic could not Read pipeline.ipynb at any
window size and fell back to line-anchored Grep.
-->

---
class: idea-slide
layout: two-cols-header
---

# D28 &middot; Multi-leaf (leaf-spring) longeron

::left::

<div class="text-sm leading-snug">

- **What:** Split each longeron into `n_leaves` thin leaves stacked in the winding plane, free to
  slide — a leaf spring. The hope: total depth still carries load while each leaf bends at its own
  small depth.
- **Origin:** direct attack on this run's own H1 — coiling curvature is pinned to the ring radius,
  so the only free lever is the depth it acts on. Classical leaf-spring practice, not a
  metamaterial citation.
- **Stats:** n=3 &rarr; 3 coil &rarr; 2 riks &rarr; 1 good (5.41&times; Bessa)
  p50/p90/p100 — R=2, quartiles carry no information; both decided rows are below
  cleared: **1 of 2 decided &ge; 2&times; Bessa (0.2244)** &middot; novel: **no** — it is `n_leaves=1`
  best good: n_leaves=1 a=.00921 b=.03324 pitch=.68128 &rarr; &sigma;=.6071 mcs=.91 mls=.0199 — **the run-17 rectangle to 4 s.f.**
  n_leaves=3 &rarr; ledgered &sigma;_peak=NaN (non-convergent, unmeasured by policy) — real
  measured &sigma;_peak=.0870 at mcs=.02, mls=.0064; see chart
- **Verdict:** UNDERPOWERED · REFUTED · leaf splitting<br>
  `n_leaves=1` is the family's own *regression control* and reproduces the incumbent exactly. The
  one multi-leaf point's real recovered stress history — not just the &sigma;_eig proxy previously
  cited here — peaks at 0.0870 kPa, a measured 7.0&times; drop from 0.6071, at 0.64% strain
  (nowhere near the 2% ceiling): a genuine load-capacity collapse, not a strain-limited one.

</div>

::right::

<div class="flex flex-col items-center justify-center gap-1" style="height: 440px">
  <img src="/gifs/D28_leaf_spring_sigma_mini.png" style="max-height: 155px; max-width: 100%" />
  <div class="text-xs opacity-60 text-center">n_leaves=1 (solid, run-17 rectangle) vs n_leaves=3 (dashed).</div>
  <img src="/gifs/D28_leaf_spring_section.png" style="max-height: 85px; max-width: 100%" class="rounded shadow-lg bg-white" />
  <img src="/gifs/D28_leaf_spring_native.gif" style="max-height: 100px; max-width: 100%" class="rounded shadow-lg" />
  <div class="text-xs opacity-60 text-center">True-scale section (1.84mm bar vs 0.61mm leaves); n_leaves=3 coiling.</div>
</div>

<!--
**Input space:** n_leaves&isin;{1,3,5} — discrete leaf count, not a continuous dial. a&isin;[.004,.014],
b&isin;[.01,.045] — per-leaf cross-section semi-axes. ratio_pitch&isin;[.25,1]. Fixed:
ratio_shear_modulus=.3677, n_longerons=3, n_storeys=1, twist_angle=0.

**Chart provenance note:** the n_leaves=3 (dashed) curve is the raw, unwindowed solve — it runs
to mcs=51.6% before the real solve itself ends (non-convergence), past the windowed mcs=.02
citation in Stats above (which reports where strain, not the raw solve, stops being trustworthy).

**REAL CHART ADDED 2026-08-28 (user request: a coiling GIF with no companion stress chart is
the same gap D38 has, but worse here — real Stage-2 data exists and was never plotted).** The
ledger's `sigma_peak=NaN` for n_leaves=3 is not "uncomputable" -- it is the oracle's own policy
(`oracle_template.py`: an unmeasured objective is NaN whenever Stage 2 doesn't converge,
regardless of whether partial data exists) applied to a design that DID produce 76 real Riks
frames. Recomputed both curves directly from each design's own `results.pkl` (still on scratch:
n_leaves=1 `/oscar/scratch/eaguerov/supercompressible_oracle/riks_549eaf38.../`, n_leaves=3
`.../riks_220ffd56.../`) with the exact `bo/response_metrics.windowed_metrics` formula -- both
recovered values (0.6071, 0.0870 kPa) match the ledger/windowed figures exactly where the ledger
has one. The real curve shows the drop is a genuine measured load-capacity collapse at 0.64%
strain, not a strain-ceiling failure and not merely an eigenvalue proxy -- strengthens, not
changes, the REFUTED call.

**Seed:** BARREN as stated. Decoupling leaf spacing from the winding radius is a different idea,
needing a different argument than "more leaves".

Run 20260809T230403, delegation D011, H7. Pre-processors archived to
scripts/superseded/ (supercompressible_{lin_buckle,riks}_leaf_spring.py) rather than deleted:
the family is settled, the machinery is not wrong, and building a Stage-2 pre-processor is most
of the cost of testing a family -- D26 went two campaigns without one and was never testable at
all.

WHY THIS SLIDE EXISTS AT ALL, since the numbers are unflattering: the run's summary table pointed
its Idea column at "archived" because there was no slide to point at, which is how a genuinely
new family tested in a closed run ends up invisible to the next reader. The deck's rule is one
slide per genuinely new idea REGARDLESS of verdict -- a family that failed is exactly what a
future agent needs to not re-propose it. assets/lint_slides.py now blocks a summary row whose Idea cell
does not resolve to a real D-slide, so this cannot recur silently.

ON THE HEADLINE CONFUSION THIS CAUSED: n_leaves=1 topped the run's feasible ledger at 0.6071 kPa
and was briefly reported (by the assistant) as a new family's best design. It is not -- it is the
rectangle, arriving through a different generator. The critic checked whether it was a duplicate
row and cleared it as "a genuinely different, independently-converged design (different
n_longerons)", but it compared against D005's n_longerons=4 design rather than the ANCHOR, which
is also n_longerons=3. Wrong pair. The notebook's prose reached the right conclusion regardless
("the novelty half of the objective was NOT met").

n_leaves=5 was budgeted but never run -- the campaign stopped after n_leaves=3 made the direction
clear, which is the correct call and is why n=3 rather than a fuller sweep.
-->

---
layout: default
---

# Re-study under contact — what was retested, and what it settles


<div class="text-xs leading-snug">

Five designs were re-examined after ground+disc contact was restored (2026-08-06/08). **Three
now have working infrastructure but no result** — read the per-design slides that follow before
proposing any of these again.

| design | what changed | tested | result |
|---|---|---|---|
| **D25** tape spring | disc faces + cap added | **330 designs**, 2 campaigns | **Settled.** Best of 28 decided reaches **21%** compression, need 80% |
| **D21** tensegrity | node-based contact (trusses carry no surface) | 1 design, on vs off | Floor stops it; energy **+86%**, stress unchanged. Still blocked on printability |
| **D17** Kresling | migrated by `_migrate_contact.py` | 1 design | Stalls at 75–77%. **Family untested** |
| **D20** laced | migrated; verified | 1 design | Does not converge. **Family untested** |
| **D26** chiral shell | Stage-2 pre-processor **written** (never existed) | 1 design | Exceeded 600s budget. **Family untested** |

<div class="flex items-center gap-4 mt-1">
  <div class="flex-1">

**Do not read "we migrated it" as "we tested it."** One design cannot settle a family — the one
design available is usually the winner of a search run *without* contact, the worst point to
generalise from.

  </div>
  <img src="/gifs/restudy_floor_contact.gif" class="max-h-20 rounded shadow" />
</div>

</div>


<!--
Written 2026-08-08 at the advisor's request, so a future agent does not read "contact is now
available" and re-propose these five as fresh ideas.

The asymmetry in this table is deliberate and is the honest state of play. D25 is the only row
carrying real statistical weight. D21 converged but its blocker was never geometric. The other
three rows record ONLY that a code path now exists.

Per-design detail on the slides that follow. Infrastructure provenance in
docs/ORACLE_ERAS.md (which commit reproduces which oracle) and docs/self_contact_spec.md
(Part 12 on why one design cannot settle a family).

**Corrected 2026-08-27 (deck audit, item 4):** this table's own "do not read 'we migrated it' as
'we tested it'" warning covers 5 designs; it does not cover 8 MORE idea slides that carry the
identical gap for the identical reason and were never added here: D6, D7, D9, D11, D12, D13, D19,
D23 all report &sigma; from before this same 2026-08-06 contact change and have never been
re-solved under it either. None are wrong on their own terms (each has an independent,
metric-orthogonal reason its family was abandoned — see each slide's own Verdict), but none of
their &sigma; numbers may be cited against the current 0.1122 kPa floor without the same re-solve
this slide already demands for D17/D20/D21/D25/D26. D23 already flags this exact gap on its own
slide ("never independently verified... until it receives the same treatment run17_rectangle
got") — this note generalizes that one self-caveat to the other seven, which don't carry it.
-->

---
class: idea-slide
layout: two-cols-header
---

# D25-2 &middot; Tape spring under contact


::left::
<div class="text-sm leading-snug">

- **What:** migrated the tape-spring pre-processor to ground+top-disc contact (already had
  self-contact, readiest of the five families). 330 designs total (64-pilot + 256-Sobol),
  10 paired on/off, and a targeted re-solve of the closest-miss design ("Design C").
- **Origin:** ground contact was restored study-wide 2026-08-06 (v1); closes the "migrated
  &ne; tested" gap the re-study index flags for five families.
- **Stats:** n=330 &rarr; 50 coilable &rarr; 36 verdict &rarr; 28 decided (8 sentinel-zero
  removed) &rarr; 0 good.<br>
  p0/p50/p90/p100 mcs: 0.0044/0.0215/0.0533/0.2149. Binding: mcs&lt;0.80 in 28/28. Contact's
  own effect (n=4 pairs): shifts the strain crossing &minus;0.002 avg — unresolvable at n=4,
  irrelevant to the 3.7&times; gap (full breakdown in notes).<br>
  best good: none &middot; cleared: none &middot; novel: no — migration + re-verification.
- **Verdict:** POWERED · REFUTED · ground contact's effect on the tape-spring
  family's strain-floor<br>
  0 feasible, unanimous compression shortfall — best of 28 decided reaches only 21% against
  80%. Contact moves the strain-limit crossing by half a point either way, an order of
  magnitude below the gap. Design C, re-solved alone, confirms this individually.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D25-2_tape_spring_designC_contact_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 265px">
    <img src="/gifs/D25-2_restudy_tape_spring_contact.gif" class="rounded shadow-lg" style="max-height: 265px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Design C, contact off vs on; showcase clip below.</div>
</div>

<!--
**Input space:** same design vector as D25's own base slide (contact migration adds no new
free parameter).

**Seed:** BARREN (corrected 2026-08-31, verdict audit) — this tag previously read FERTILE
("twist/chirality applied to the open-arc section"), but D25-3 already tested exactly
this (twist_angle promoted to a real parameter, n=105, correlation with the objective
indistinguishable from zero) and closed it REFUTED. D25-3's own notes already flagged
this exact discrepancy ("the original D25 slide and D25-2... disagreed on whether
twist had already been tried — it hadn't; left as a discrepancy... for the user's own
correction") — this is that correction. See D25-3 for the twist result.

Jobs 4791881 (invalid sampling, superseded), 4792435 (64-design pilot), 4794837 (256-design
significance sweep, 1.01 h wall).

THE 256-DESIGN SWEEP, in full: 256 evaluable designs drawn from 752 candidates (66% of the
recorded box rejected as un-meshable or too thick) -> 50 coilable -> 36 that reached a verdict
(35 of them salvaged from incomplete solves) -> 0 feasible. mcs percentiles over the 36:
p0 0.0044, p50 0.0215, p90 0.0533, p100 0.2149. Binding criterion: mcs < 0.80 in 28 of 28,
mls > 0.02 in 0 of 28, ring_passthrough in 8.

THE JOB'S OWN PRINTOUT SAID 36 DECIDED, AND IT WAS WRONG. Eight of those 36 were EMPTY: a
salvaged ODB holding zero usable increments, so window_n = 0, which satisfies the
"window_n < history_n" test trivially and was recorded as "the window closed" on a response
containing nothing. Each reported mcs = mls = sigma_peak = 0.0 -- and it was the oracle contract
guard added the same day (bo/oracle_template.py) that flagged them, on its first run, as the
sentinel-zero pattern. Fixed in bo/oracle_tape_spring.py: a window that closed must actually
contain something. The corrected denominator is 28, and the verdict is unchanged.

WHY THIS SLIDE COUNTS 28 AND NOT 37. The pilot campaign's own 9 usable designs are NOT added in.
They predate the empty-response fix and cannot be re-audited for it, because the campaign script
wrote its results to a fixed path (bo/campaign_tape_spring_result.json) and this run overwrote
them. That is now job-stamped. 28 is the number that survives audit; 330 is the number of designs
put through the oracle under contact, which is the right denominator for "how much was spent" and
the wrong one for "how much was decided".

WHY THE HEADLINE IS mcs AND NOT mls. The campaign's own first printout said "designs under the
2% limit: 36 of 36", which sounds like every design passed and is in fact a tautology: windowed
mls is bounded above by 0.02 BY CONSTRUCTION, because the window closes at the crossing. It
carries no ranking information at all. The same script also ranked designs by min(mls) to find
the "closest miss", which picks the design that stalled SOONEST -- it printed
"closest miss: mls=0.000000 mcs=0.0000". Both are now fixed in
bo/run_campaign_tape_spring.py, and phase 1 was re-analysed on strain_crossing_mcs; the numbers
on this slide are the corrected ones. This is the same saturation trap that produced a wrong
verdict on the pilot campaign, in a second disguise, which is why it is written up in
docs/TRAPS.md section 3 rather than only fixed in code.

WHICH KNOB ACTUALLY MATTERS. bo/campaign_summary.py over the 28 decided designs: of the six free
parameters, exactly one moves the blocker -- alpha_tape, the arc angle (rho = -0.600 against
compression reached, Holm-adjusted p = 0.003 across the six; every other parameter adjusts to
p = 1.00, including thickness and R/t). Section depth, which alpha drives, correlates at
rho = -0.665. The deepest half of the designs reach 0.9% compression at the median; the flattest
half reach 3.4%.

AND THE BEST DESIGNS SIT ON THE alpha_tape LOWER BOUND (the top quarter average 14% of the
range). Normally that means "widen the bound, you have not measured this dimension". Here it
means the opposite, and it is the strongest single argument for closing the family: the search
is pushing toward the SHALLOWEST arc allowed, and the bound is already 0.05 rad. Widening it
further does not find a better tape spring, it deletes the arc -- the best design in the whole
campaign has 0.5 mm of section depth and is a flat strip, which is D6 territory and already
searched. The optimiser's preferred direction exits the family.

ON "DECIDED" VS "USABLE". Only 36 of 256 reached a verdict, and that is the honest denominator.
A design whose window closed before the solve failed is DECIDED -- the verdict lives entirely in
the completed increments. One whose solve died before the window closed is TRUNCATED DATA, and
counting it would be counting a stall as a small crossing. bo/oracle_tape_spring.py flags this
per design (window_closed_before_failure); the paired test excludes any pair where either side
is truncated, which is why n=4 and not n=6.

WHY THE FIRST CAMPAIGN WAS THROWN AWAY: a blind Sobol sample of the bounds recorded on the D25
slide put 55% of the budget into designs that crash the mesher ("Some regions cannot be
Mapped"). Each longeron is an arc of radius R_tape spanning alpha_tape, swept along the
joint-to-joint line -- a strip of width R_tape*alpha_tape. The recorded bounds allow 880 mm on a
100 mm structure; three longerons share ~105 mm of circumference each. Wider strips overlap
themselves and their neighbours, and Abaqus cannot tile a self-overlapping surface. Measured
across 77 attempts: 0/26 failed below 50 mm, 13/13 failed above 400 mm. That is now a free
geometric prefilter in bo/oracle_tape_spring.py, and it is why the original campaign sampled
four named CORRIDORS rather than the box -- a fact lost when the bounds were copied onto the
slide without it.

WHY A STALLED SOLVE STILL DECIDES A DESIGN: this family's solves stall near 80% compression, but
the reported window closes at the FIRST of 95% compression or 2% strain, and this family fails on
STRAIN. A design crossing 2% at 11% compression is DECIDED. scripts/salvage_riks_odb.py
post-processes the partial ODB; 8 of the 9 usable results came from stalled solves that would
otherwise have been discarded, and the oracle marks `window_closed_before_failure` so a
truncated response is never mistaken for a verdict.

A MEASUREMENT TRAP, recorded because it produced a wrong verdict first: the paired test was
initially run on WINDOWED mls, which is pinned just under 0.02 BY CONSTRUCTION -- the window
closes at the 2% crossing, so its maximum cannot exceed it. Comparing it measures the ceiling,
not the design. The unsaturated statistic is `strain_crossing_mcs`: at what compression does the
design cross 2%.

ON THE OLD "CLOSEST MISS" FRAMING: design C is recorded as failing only criterion 3, by 1.38x.
Under the current window it exceeds the strain limit at 20% compression -- a quarter of the way
to the requirement. Same curve, same verdict, but "1.38x over on strain" reads as a near miss and
"blows the budget a fifth of the way down" is what the data says.

Verified 2026-08-26 (deck audit, item 1): pulled the raw 256-design sweep JSON from git history
(commit 23cac27, renamed from job 4794837's original path -- not on main) and independently
recomputed the full funnel: 256 evaluable -> 50 coilable -> 36 reached a verdict
(window_closed_before_failure=1) -> 8 sentinel-zero -> 28 decided, all exact matches. mcs<0.80 in
28/28, mls>0.02 in 0/28, ring_passthrough in 8/28, best mcs=0.2149 (21%) -- all exact. alpha_tape
vs mcs: rho=-0.600 exact, raw p=0.0007 (Holm-adjusted across 6 params ~0.004, consistent with the
cited 0.003). mcs percentiles p50/p90 (0.0203/0.0546 recomputed vs 0.0215/0.0533 cited) differ by
2-6%, plausibly a different percentile-interpolation convention at n=28 -- not chased further,
non-material to any claim on this slide.

DESIGN C, EXPLICITLY RE-SOLVED (added 2026-08-27, advisor request: the showcase GIF above is from
the 330-design campaign's own Sobol sweep, a near-flat-strip design, NOT design C -- the original
D25 slide's single closest-miss point had never been solved under contact on its own, only folded
into this slide's n=4 paired-delta aggregate above). Design C = t_tape=0.419034, R_tape=19.675232,
alpha_tape=0.638683, beta_tape=1.483305, ratio_pitch=0.844812, ratio_top_diameter=0.360376 (fixed:
circular=17, n_longerons=3, n_storeys=1, twist_angle=0, ratio_shear_modulus=.3677) -- verbatim from
data/idea_odbs/20260730T020245_H2_tape_spring/sim_info.pkl. Dispatched via
bo/run_D25_designC_contact_resolve.py through the CURRENT get_evaluator(namespace='tape_spring')
adapter chain (oracle_tape_spring.evaluate, ground_contact=True, imperfection default 0.067 rad),
sbatch job 5409623 on a separate allocation, NOT the interactive node (2026-08-27, wall 302 s).

RESULT: coilable=1 (Stage 1), converged=0 -- Stage 2 stalled and was salvaged
(window_closed_before_failure=1, timed_out=0, so the salvage is a DECIDED verdict, not truncated
data). sigma_peak=0.31554 kPa (via bo/response_metrics.py:windowed_metrics, the same reduction
every number on this deck uses), sigma_eig=0.61667 kPa (Stage-1 eigenvalue estimate -- exactly
reproduces the archive's own sigma_crit=0.616672, confirming Stage-1/geometry match exactly and
that contact cannot touch a linear estimate that never engages it). mcs=0.19059, windowed
mls=0.01972 (passes the 0.02 cap only because the window closes there by construction), unwindowed
mls_full=0.02752 (matches the archive's 0.027516 to 4 decimal places -- same physical strain
ceiling, reached by a different point in the same curve). strain_crossing_mcs=0.20342 (the actual
2%-strain crossing, i.e. 20% compression). ring_passthrough=False, rt_over_t=46.95 (>=10, passes).
Feasibility: mcs>=0.80 FAILS (0.191, short 4.2x), mls<=0.02 barely passes (construction artifact
of the window, not a real margin), ring_passthrough and rt_over_t both pass -- feasible=False,
binding criterion is mcs, the SAME criterion that binds the 28-design funnel above. Bit-identical
(to the digit) to job 4794837's own phase-1 paired-ON row for "design_C_closest_miss" (still on
scratch, /oscar/scratch/eaguerov/sc_oracle_tape_spring/riks_c0d9fdf53d314b299d1b69c27410d978/) --
this design's oracle output has not changed since 2026-08-08 (git log on bo/oracle_tape_spring.py
confirms the only changes since are an imperfection-as-argument refactor, default unchanged, and
the unrelated window_n<=0 empty-salvage guard, which this design's window never hit), so this is a
genuine independent re-confirmation, not new information from the code path -- and full JSON is
saved at bo/design_C_contact_resolve_result.json.

CONTACT-OFF CROSS-CHECK, same design, same current pipeline (job 4794837's own paired-OFF row,
raw results.pkl still on scratch): sigma_peak=0.31801 kPa, mcs=0.18524, strain_crossing_mcs=0.19797
(19.8%). Essentially identical to contact-on (sigma_peak differs 0.8%, crossing differs 0.5 points
of compression) -- confirms the hypothesis this restudy was testing for design C specifically: the
strain-floor failure is intrinsic to the arc's own curvature, not something an unmodeled contact
surface was hiding. One caveat found in passing, NOT chased further (out of this delegation's
scope): the contact-OFF replay's UNWINDOWED full-history mls_full reads 10.38 (nonsensical, vs the
archive's graceful 0.0275 stall) -- ground_contact=False on the CURRENT (contact-migrated)
pre-processor is evidently not a faithful reproduction of the true pre-contact numerics for THIS
family past the reported window (oracle_tape_spring.py's own docstring already flags this
equivalence as "verified to the digit on tensegrity", never claimed for tape_spring). Does not
affect any number cited above -- every one is read from inside the window, before wherever that
divergence happens -- but is a real, distinct finding for whoever next touches this family's
ground_contact=False path.

ON THE OLD ARCHIVED FRAMING, RECONCILED: the archived sigma_crit (0.6167 kPa) and max_local_strain
(0.027516) are not directly comparable to sigma_peak/windowed-mls above -- sigma_crit is the
Stage-1 linear-buckling eigenvalue (unaffected by contact or by the 2026-08-06 windowing change by
construction), and the archive's own results.pkl (data/idea_odbs/20260730T020245_H2_tape_spring/
results.pkl, pre-dates the 2026-08-06 per-frame strain history) recorded max_local_strain=0.027516
as the peak strain reached by the SOLVE'S OWN STALL POINT (mcs=0.7877, per its
max_local_strain_mcs_at_truncation field) rather than at the first 2%-strain crossing -- so "fails
only criterion 3, by 1.38x" and "crosses 2% strain at 19-20% compression" describe the SAME curve
under two different reporting conventions, not two different physical results. This is exactly
what this slide's own "ON THE OLD CLOSEST MISS FRAMING" paragraph above already said in the
abstract; this entry supplies the concrete re-solved numbers behind it.

CHART: assets/public/gifs/D25-2_tape_spring_designC_contact_mini.png (750x270, same convention as
D17-3_kresling_sigma_history_mini.png/D21-2_tensegrity_strain_history_mini.png -- grey-to-red
LinearSegmentedColormap over #9a9a9a/#d94f3a/#8c1a12 via a LineCollection encoding each point's own
sigma magnitude, solid=contact-on/dashed=contact-off encoding the state comparison, both curves
truncated at their own windowed_metrics() window_n). Built from job 4794837's own raw
results.pkl (both still on scratch, paths above) via response_metrics.windowed_metrics, called
directly, not reimplemented -- values printed by the script match both this delegation's own fresh
JSON and the archived campaign JSON exactly. Script: ad hoc, uncommitted, same convention as this
deck's other mini-plot scripts (not persisted in bo/ -- it is a plotting utility, not part of the
oracle/campaign infrastructure those files are reserved for).
-->

---
class: idea-slide
layout: two-cols-header
---

# D21-2 &middot; Tensegrity under contact


::left::
<div class="text-sm leading-snug">

- **What:** contact added by hand, not by the migration tool — struts have no cross-section
  geometry, so the secondary side is a NODE REGION with the strut radius injected explicitly.
  1 design, on vs off; Stage 1 reproduces the archive exactly.
- **Origin:** ground contact was restored study-wide 2026-08-06 (v1); this family needed a
  hand migration since the automated tool doesn't apply to truss members.
- **Stats:** n=1 design, on/off paired. Energy absorbed +86% (18.202&rarr;33.780 kPa).
  &sigma;<sub>peak</sub> bit-identical (peak lands before contact engages). mls:
  ~0&rarr;3.4%. ring_passthrough: True (off) &rarr; False (on).<br>
  cleared: n/a — mechanism already disqualified on printability, independent of this result
  &middot; novel: no — contact migration on an already-tested family.
- **Verdict:** POWERED · REFUTED · contact rescuing tensegrity's printability
  disqualification<br>
  The floor stops it and genuine straining occurs (~0&rarr;3.4%) where before there was none.
  But the structure still reaches compression by rotating rigid struts — a linkage, per
  apples-to-apples — needing prestressed cables and pin joints contact doesn't touch.

</div>

::right::

<div class="flex flex-col gap-1" style="height: 385px">
  <div class="flex items-center justify-center" style="height: 115px">
    <img src="/gifs/D21-2_tensegrity_strain_history_mini.png" style="max-height: 115px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 225px">
    <img src="/gifs/D21-2_restudy_tensegrity_contact.gif" class="rounded shadow-lg" style="max-height: 225px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Above: strut strain, contact off vs on. Below: contact-on collapse.</div>
</div>

<!--
**Input space:** same design vector as D21's own base slide (contact migration adds no new
free parameter).

**Seed:** BARREN — the mechanism needs prestressed cables and pin joints, which cannot be
monolithically printed. Contact does not touch that.

Migrated by a subagent, commit 2979e35, jobs 4777817 / 4778543 / 4778788.

THE STRAIN NUMBER IS THE WHOLE STORY. 9e-14 is not a small strain, it is NO strain: the structure
reaches compression by rotating rigid struts about joints, which is the apples-to-apples clause's
definition of a linkage rather than a supercompressible material. Contact forces real straining
(3.4%), but a linkage that now touches the floor is still a linkage.

sigma_peak being bit-identical with and without contact is the clearest demonstration yet of why
energy_absorbed was added: the peak lands before contact engages, so a maximum cannot see what
contact does. This is the first family where contact moved any reported number.

TWO FINDINGS THAT GENERALISE BEYOND THIS FAMILY, both from the subagent:
- `THE ANALYSIS HAS COMPLETED SUCCESSFULLY` is necessary but NOT sufficient. A Riks step that
  inverted its path to LPF = -34 (the load proportionality factor -- Riks's own internal tally of
  how far along the loading path the solve has progressed; it's allowed to legitimately reverse or
  go negative, which is exactly what makes this trap easy to miss) and climbed back still reported
  success, and the first probe read it as converged with mcs = 34.2. Check the LPF path, not just
  the exit status.
- A node region (a contact-surface definition built from individual mesh nodes rather than a
  continuous surface) carries its own contact multiplier, so a node that is ALSO a
  kinematic-coupling secondary (a node whose motion is being slaved to another part's motion) is
  over-constrained by construction (zero pivot, contact force error -1.5e21) -- two different
  Abaqus rules both trying to dictate the same node's motion at once. The
  element-based families are not known to have this, but they have not been checked and their
  top rings descend onto the same floor.

Verified 2026-08-26 (deck audit, item 1): pulled the raw on/off probe JSON from git history
(commit 2979e35, debug/template_check/tensegrity_contact.json, not on main). All four headline
numbers reproduce essentially exactly: ring_passthrough detail "node 6 below bottom ring by
50.1528" (off) vs False (on); energy_absorbed 18.202->33.780 kPa = +85.6% (rounds to +86%);
sigma_peak literally bit-identical (321.78315269057293 in both runs, to every digit shown); mls
9.037e-14 (off, matches "9x10^-14" exactly) -> 0.033613 = 3.36% (rounds to 3.4%, on).

WHERE THE STRAIN-HISTORY MINI PLOT CAME FROM (added 2026-08-27, "Can we add strain history of the
tensegrity design?"). `/oscar/scratch/eaguerov/sc_tensegrity_contact_probe/` still held four solved
Riks ODBs (listed, not assumed): `riks_37a83c58...` (`ground_contact=False` explicit in its
`sim_info.pkl` -- the OFF case), `riks_53ce7b2b...` and `riks_dd06d71c...` (`ground_contact` absent
-> defaults True per `scripts/supercompressible_riks_tensegrity.py` line 520 -- both converged,
numerically IDENTICAL to each other, the ON case), and `riks_6288d6e1...` (also default-True but a
runaway/diverged extra attempt -- 48 increments vs the other three's 10, final U3=+3461&nbsp;mm,
`max_local_strain`=21.5 -- excluded as a non-physical failed solve, not used for anything here).
Matched to job numbers by exact-digit reproduction, not filename: sigma_peak/mls from
`riks_53ce7b2b.../results.pkl` reproduce 321.78315269057293 / 0.033613044768571854 to every digit
shown above, and `riks_37a83c58.../results.pkl` reproduces 9.037215420448774e-14 -- the same
numbers this slide already cited from the archived probe JSON, so this is the correct pair.
Per-frame data was READ DIRECTLY, not re-derived: `results.pkl` (written by
`scripts/supercompressible_riks_pp.py` when these jobs originally solved) already carries the full
`strain_per_frame`/`strain_frame_values` history (peak |E or LE component| at each frame, restricted
to `ALL_LONGERONS` -- struts only, see the caveat below) and the `U`/`RF` reference-point history
used to compute mcs, exactly per `bo/response_metrics.py`'s own convention. Spot-verified against
the raw ODBs directly (`abaqus python`, read-only, `session.openOdb(readOnly=True)` implicit via
`odbAccess.openOdb`) at every one of the 10 frames each solve has -- field-output peak strain and
history-output U3 both reproduce `results.pkl` to the digit. mast_height = n_storeys &times;
ratio_pitch &times; bottom_diameter = 1 &times; 1.0118551314319302 &times; 100 = 101.1855&nbsp;mm.

STRUT-ONLY, BY CONSTRUCTION -- NOT A CHOICE MADE FOR THIS CHART. Both ODBs' only field output
request (`LONGERON_STRAINS`, `scripts/supercompressible_riks_tensegrity.py` ~line 566) is scoped to
`ALL_LONGERONS` (the STRUT segments) alone; `ALL_CABLES` exists as a geometry/section set but was
never given a field output request when these jobs solved, so cable strain is not present in either
archived ODB at all -- extracting it would need a new solve, which is out of scope here. The chart
therefore shows exactly the family's own already-reported `mls` metric (strut strain only), nothing
broader, and the caption above says so.

Only 10 field-output frames exist per solve (coarse Riks increment schedule, not a subsampling
choice made here) -- both curves are real data at every plotted point, just few of them. The
divergence itself is unambiguous regardless: both curves sit at machine-zero strain (1e-12-1e-14,
floating-point noise) through mcs&asymp;56%, THEN contact-on breaks away at mcs&asymp;70% (0.357%) and
climbs to 3.36% at its final frame (mcs&asymp;106%) while contact-off never leaves zero anywhere in
its own history (max 9.04e-12) -- a genuinely late, sharp onset, not a gradual one, consistent with
the floor only being reached well into the compression stroke.
-->

---
class: idea-slide
layout: two-cols-header
---

# D17-2 &middot; D17/D20/D26 — testable now, untested still

::left::
<div class="text-sm leading-snug">

- **What:** **D17**/**D20** migrated to contact by `scripts/_migrate_contact.py`; **D26** had
  no Stage-2 pre-processor at all (its prior campaigns all failed Stage-1) — one written for
  it. One design solved per family — verifies a code path, not a family.
- **Origin:** closes the "migrated &ne; tested" gap (re-study index) for three families,
  verifying each code path runs before being cited as tested under contact.
- **Stats:** n=1 per family (3 designs), infrastructure verification only.<br>
  D17: stalls at 75&ndash;77% — the anchor tested is the design most likely to exploit
  floor-passthrough, so failure here is near-tautological (superseded by D17-3's own 380-eval
  campaign — a mesh singularity, not floor-passthrough). D20: builds, doesn't converge. D26:
  exceeds the 600s budget (~11k nodes vs ~1k) — blocked on cost, not correctness.<br>
  cleared: none tested &middot; novel: n/a — infrastructure verification.
- **Verdict:** BLOCKED · UNKNOWN-NO-EVIDENCE · D20 and D26's own families under
  contact<br>
  One design per family verifies a code path, not a family. D17's question is independently
  closed by D17-3. D20 and D26 remain genuinely untested — D20 for lack of a real search,
  D26 because it can't finish inside budget. "Migrated" &ne; "tested" for either.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/gifs/D17-2_restudy_laced_contact.gif" class="max-h-80 rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-2 px-4 text-center">D20's laced longeron, coiling — see notes.</div>
</div>

<!--
**No stress-history chart on this slide (rule 2c-VIS exception):** all three checks here are
single-design infrastructure verifications, not decided campaigns — D26 never reaches Stage 2
at all, D20 never converges, and D17's own real compression history is already charted on
D17-3.

**Input space:** same three design vectors as D17/D20/D26's own base slides; no new
parameter — a single point per family, run through the migrated/new code path.

**Seed:** BARREN (all three, superseding this bullet's own prior FERTILE tag) — each has since
been searched under contact elsewhere and closed: D17 (see D17-3 — mesh singularity,
not floor-passthrough), D20 (run `20260819T022742` H11 — 6 pts stuck 1.3&ndash;3.4%), D26 (run
`20260804T221559` — 80-pt sweep, 0/68 valid designs coilable). No perturbation left un-searched on
any of the three.

Commits 4ba6627 (D17), a235734 (D20, D25), and the D26 pre-processor.

D17 is the sharpest illustration of why one design proves nothing about a family. The design
tested is the anchor -- found by a search run against the FLOOR-FREE oracle, so it is the design
most likely to have been selected precisely for exploiting floor passthrough. Its failure under a
floor is close to tautological. Whether the Kresling family contains points that WORK under
contact -- possibly points the old oracle rejected, since bearing on a disc is load-carrying it
could not represent -- is untested.

D26 is blocked on cost, not correctness: its deck asserts pass. The mesh is the lever
(`mesh_seed_shell` is already a parameter), not the wall clock -- raising the budget does not
make a family converge, and a family that cannot produce a result inside the per-solve cap is not
searchable. See PROBLEM_STATEMENT.md's per-solve budget section.

Also unmigrated and worth knowing: ~15 further families, plus supercompressible_riks_brace.py,
which until 2026-08-08 had contact ACTIVE with allowSeparation=OFF -- the setting measured at
9/95 Stage-2 convergence. Any brace-family result predating that fix is suspect.

Verified 2026-08-26 (deck audit, item 1): D20's citation (run 20260819T022742 H11, "6 pts stuck
1.3-3.4%") reproduces exactly from that hypothesis's own status_log comment. D26's citation did
NOT: the source run's own H1 status_log records D004 as "80-pt sweep, 0/68 valid designs
coilable" -- 68 is the evaluated denominator (12 of the 80 sampled points were rejected before
dispatch), not 80. This slide read "0/80 coilable," conflating the sample size with the evaluated
count, inconsistent with this deck's own house convention elsewhere (report against the
valid/evaluated denominator, e.g. D25's "256 evaluable" phrasing). Corrected in the Seed line
above. D17's citation points to D17-3, independently verified separately on that
slide.
-->

---
class: contract-slide
---

# The contract changed here

<div class="text-xs leading-snug">


Every verdict below was decided under the rules in force that week, and the rules moved at least
twelve times — so **verdicts from different runs are not directly comparable.** Numbering starts now:
everything before 2026-08-06 is the *unversioned era*; today's contract is **v1**, the first one pinned.

| Date | What changed, and what it moved |
|---|---|
| 2026-07-16 | Reference design fixed at 0.1306 kPa (every "&times; Bessa" figure before this means something else). Contact with the ground **removed**, believed to be an artificial obstruction — it was not; see the last row |
| 2026-07-17 | Compression target corrected 90% &rarr; 80%. Strain judged only up to that point, not over the whole squash. Stage 2 made damping-free by default, damping opt-in and capped at 5% of strain energy |
| 2026-07-18 | Folding linkages ruled out — reaching 80% by rotating rigid bars, with almost no material stretch, stopped counting. Demoted tensegrity (1691&times;) |
| 2026-07-20/21 | Material passing through a ring's own footprint became a failure. Demoted Kresling (5.4&times;) and the laced design |
| 2026-07-22 | Bar lowered to 2&times; the reference design. The 5.9&times; result reframed as context, not a target to beat |
| 2026-07-23 | Strain limit became Bessa's literal wording: 2% on *any* strain component, shear included |
| 2026-07-27/28 | A joint-strain scare retracted one headline, then a convergence study reconfirmed the 5.9&times; baseline; two other designs were never re-checked |
| 2026-08-04 | Novelty must be a new *shape or arrangement*, not a resized cross-section |
| **2026-08-06 (v1)** | **Contact with the ground restored** (Bessa always had it; we lost it 2026-07-16) and the disc faces made solid. Compression stops at 95%. Load read from the squash itself, not the cheap estimate, inside a window ending at 2% strain |

A verdict tagged **(SUPERSEDED)** means the evidence was right and did count at the time, and
the rules have since changed in a way that could alter it — "re-test me", not "I was wrong".
**Everything below this slide is in the OLD rules — translate before comparing.** And **every
animation older than 2026-08-06 was made without a floor**, so longerons visibly sink through
the base — an artifact of the model of the day, not the design. Under v1 the reference design measures
**0.1122 kPa** (was 0.1306), so 2&times; = **0.2244**, and the 5.9&times; baseline becomes **0.6077 kPa = 5.42&times;**.
Every &times;Bessa figure on the slides below is in the OLD metric, consistently so.

</div>

<!--
Reconstructed 2026-08-06 from `git log -- supercompressible-material/PROBLEM_STATEMENT.md`
(~70 commits, of which these are the substantive contract changes as opposed to infra/doc
edits). Same-date entries are merged into one row for space; the underlying commits are:

- 2026-07-16: f400e27 (Bessa point reconciled to 0.1306) and 01c7e40 (NO-CONTACT oracle
  adopted -- the removal now known to be based on a misidentification of ANALYTICAL_SURF,
  see docs/self_contact_spec.md Part 7).
- 2026-07-17: 9b926e9 (mcs 0.90 -> 0.80), 71cae19 + 261998b (mls evaluated only up to the
  mcs threshold -- explicitly framed at the time as a deliberate Bessa superset departure),
  841b41e (energy-free default + stabilization opt-in + the ALLSD/ALLSE < 0.05 gate --
  ALLSD is energy dissipated by artificial numerical damping, ALLSE is real elastic strain
  energy; keeping their ratio small means the damping trick isn't doing enough work to be
  masking the true structural answer).
- 2026-07-18: 965e488 (apples-to-apples clause; tensegrity demoted to FAILED), ef82143.
- 2026-07-20/21: 7fd6ac0 (2026-07-20, ring-passthrough as criterion 5), 49ab551 (2026-07-20,
  fixing "all four criteria" references left behind), 5f8cccd (2026-07-21, second confirmed
  instance, the built-up/laced family). Corrected 2026-08-26 (deck audit, item 1): this row
  previously read "2026-07-20" for all three commits; 5f8cccd is actually dated 2026-07-21,
  verified via `git show --format=%ci` (same class of error as the 07-27/28 row above).
- 2026-07-22: dc8c3a1 + 0a48fb5 (operative target lowered to 2x Bessa), ada094c (5.9x
  reframed as context), d34573f (more conservative about what counts as a dead end).
- 2026-07-23: 8c1a4a7 (Bessa's actual max(eps_ij) criterion implemented), a811852.
- 2026-07-27/28: bf38e64 (2026-07-27, headline retracted after the continuum check), c32b6b4
  (2026-07-28, run17 rectangle reconfirmed via the cut-distance convergence study), 0bee11f +
  624970c (target restored to 2x + novelty; the Nature-caliber test made concrete). Corrected
  2026-08-26 (deck audit, item 1): this row previously read "2026-07-28" for both commits;
  bf38e64 is actually dated 2026-07-27, verified via `git show --format=%ci`.
- 2026-08-04: d4721d4 (novelty must be geometrical or topological).
- 2026-08-06: this session -- see docs/self_contact_spec.md Parts 5-9 for the evidence
  behind each of the four changes, and Part 9 for why three of them are fidelity repairs
  and only the metric change is a genuine redefinition.

Not shown, because they predate the deck's own coverage: criteria 2-5 did not exist at all
for the earliest runs (the 5-longeron result from 20260629T191754 was decided when only
criterion 1 existed), and the slenderness>=10 beam-validity floor was formalised around
2026-07-17 (e5c956e) after being applied informally earlier.

Why numbering starts now rather than retroactively labelling a "v1" and "v2": the pre-2026-08-06
record is not one contract, it is at least twelve, and inventing a single retroactive version
number for it would imply a coherence that did not exist. Calling it the unversioned era is
the honest description and carries the operative warning -- do not compare verdicts across it
without checking what the rules were at each date.
-->

---
class: summary-slide
---

# Run `20260804T221559` — summary

<div class="text-sm leading-snug">

Four literature-grounded chirality/elastic-instability candidates tested against the newly-sharpened "not a cross-section resize" bar — two brand-new topologies (chiral shell tube, chiral shell vane) failed to coil at all, and two pretwist refinements found a numerically-passing design whose performance the agent's own regression attributed to resize dimensions, not chirality.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | A genuinely novel geometry/topology (not a cross-section resize) clears 2&times; Bessa with all feasibility criteria | **?** | 4 candidates tested; best numeric hit (D010, 0.4254 kPa) explained ~91% by resize dims, chirality lever p=0.145 — not credible as genuinely novel | D26, D27, D1, D6 |
| H2 | This study's slender-beam elastic-instability space is capped near the resize ceiling (~0.77 kPa) — no genuinely novel topology clears 2&times; Bessa without breaking beam-validity or folding | **?** | Confounded test (Charter &sect;3): D010's clearing point can't cleanly separate resize-driven from chirality-driven performance; the other 3/4 candidates support H2's spirit outright | D26, D27, D1, D6 |

 &nbsp;&middot;&nbsp; **Cost: $21.13**
</div>

<!--
Run stats: all-Sonnet, GATED on 4th critic attempt (1 CRITICAL doe-cell finding
caught and fixed between calls 1-2, then clean), evals_used=301, ~8h wall of a
12h budget. H-numbering note: unlike earlier runs, this run registered only 2
top-level hypotheses (H1/H2) and tested 4 candidate families as evidence for/
against both, rather than one H per candidate — D009/D010 don't get their own
"H3"/"H4" rows here because they were run as sub-campaigns cited as evidence,
not separately pre-registered claims.

D004 (chiral_shell_tube, own slide D26): 80-pt sweep, 0/68 valid designs
coilable (12/80 rejected by the thin-shell rt_over_t&ge;20 guard before that).
Every lowest mode is a global lateral-bending/Euler-sway pair — a full
monocoque tube is too stiff against global bending for the local torsional/
coiling coupling to compete.

D007 (chiral_shell_vane, own slide D27): follow-up after D004 — reverts to n
discrete members (this study's usual sparse topology) while keeping each
member a chirally-twisted doubly-curved shell "vane". 120-pt sweep, still
0/115 coilable on the strict check; the weaker "coilable_legacy" proxy (same
threshold convention every other family uses) passes 34/115, so the two
coilability definitions disagree substantially here — worth watching if this
family or a descendant gets revisited.

D009 (circular pretwist, folds into the pretwisted-longerons idea, D1): 100%
coilable, twist_angle coefficient -0.0093 (negligible) in the OLS regression.

D010 (anisotropic-rectangle pretwist, folds into the run17-rectangle-anchor
idea, D6): twist_angle coefficient grew to +0.0781 but still not significant
(p=0.145) against ratio_a (0.9114) and ratio_b (0.3859) dominating. Found a
feasible point at sigma_crit=0.425389 kPa (mcs=1.011151, mls=0.018075,
twist_angle=0.073079) that numerically clears 2&times; Bessa — but per the
regression, this is a resize-family point with a statistically
non-contributing cosmetic twist, not evidence of a genuinely novel mechanism.
Full critic-gate history: 4 review calls, 1 CRITICAL (doe cell had no real
create/sampler branch — fixed) + 2 MAJOR (D009's regression never actually
run despite being cited; a nonlinear/near-critical-point alternative
mechanism from the cited literature never considered) at call_001, all three
resolved for real by call_002, clean PASS at call_004.
-->

---
layout: two-cols-header
class: idea-slide
---

# D26 &middot; Chiral continuous-curved-shell tube

::left::

<div class="text-sm leading-snug">

- **What:** Replaced all n discrete straight longerons with ONE continuous,
  doubly-curved, multi-lobed shell tube connecting the two rigid rings, with
  a built-in azimuthal twist of the lobe pattern from bottom to top —
  chirality breaking mirror symmetry to try to couple axial compression into
  global rotation.
- **Origin:** Liu et al. 2025 (*Nature Communications* 16:11359), "chiral
  multi-curved shell metamaterials integrating compression-torsion and
  buckling mechanisms" — every prior family in this study keeps a discrete-
  member load path; this removes the discreteness entirely.
- **Stats:** n=80 &rarr; 0 coil &rarr; 0 riks &rarr; 0 good<br>
  quartiles unavailable — 0/80 Stage-1 coilable, so Stage 2 never auto-escalated<br>
  cleared: none (0 decided) &middot; novel: untested — no design ever reached a Riks solve<br>
  best good: none (0/80 passed every criterion)
- **Verdict:** POWERED · REFUTED · monocoque chirality<br>
  The monocoque topology suppresses
  coiling entirely. Every one of 68 valid designs' lowest buckling mode is a
  global lateral-bending/sway pair (see gif), not top-ring rotation: a full
  continuous shell tube is far stiffer against global lateral bending than
  this study's successful sparse discrete-longeron families, so the local
  torsional/coiling coupling never gets to compete. 12/80 designs were
  additionally rejected by the thin-shell validity guard (rt_over_t&ge;20)
  before ever reaching this check.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/D26_chiral_shell_tube_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Mode 1, typical design — global sway, not coiling.</div>
</div>

<!--
**Input space:** n_lobes&isin;[3,6] — discrete lobe count. A_max&isin;[.05,.35] — lobe amplitude.
twist_chirality&isin;[0,3.14] — azimuthal twist of the lobe pattern bottom-to-top. t_shell&isin;
[.5,2] — shell wall thickness. ratio_pitch&isin;[.15,.8], ratio_top_diameter&isin;[0,.5] — usual
per-storey pitch/taper meaning. Fixed: ratio_shear_modulus=.3677.

**Seed:** BARREN — the failure is topological, not parametric: a continuous chiral shell surface
is stiff enough against global lateral bending to suppress coiling entirely, confirmed
independently when D27 reverted to discrete members and still failed strict coilability.
Further thinning the shell just converges toward an ordinary discrete beam cross-section,
already tested extensively elsewhere in this study.

**Deferred:** Coilability check for this family is stricter than the shared
`supercompressible_lin_buckle_pp.py` convention used by every discrete-member family:
it requires the top ring's rotation AND axial descent to be non-trivial RELATIVE TO
the shell wall's own local deformation scale (not just non-zero in absolute terms),
specifically to rule out cases where the wall's own local wrinkling dominates and a
tiny absolute rotation is just noise riding on top of it. Under the weaker,
shared-convention "legacy" threshold (rotation present AND near-zero absolute lateral
displacement), 4/68 pass — so there is a genuine, unresolved daylight between the two
coilability definitions for this family, not fully adjudicated this run. **Verdict-audit
note (2026-08-31):** REFUTED above holds either way — 4/68 is not a working family under
either convention — but the visible Stats bullet's flat "0 coil" is this family's own
stricter check, not directly comparable to another family's "coilable" count without this
qualifier.

**Timeline:** This is H1 of run `20260804T221559`, delegation D003 (build) + D004
(80-pt LHS sweep, seed=0, 20 per n_lobes&isin;&#123;3,4,5,6&#125;).

**Infra:** ODB archived at data/idea_odbs/20260804T221559_D004_chiral_shell_tube/ (a
TYPICAL member of the sweep, not a "best" point — per this deck's no-winner
convention; n_lobes=3, A_max=0.1997, twist_chirality=2.521 rad, t_shell=0.978mm,
ratio_pitch=0.4292, ratio_top_diameter=0.1733). GIF: native Abaqus/CAE Viewer export
of the LIN_BUCKLE step's Mode 1 frame, rendered 2026-08-05. This is a *BUCKLE step
(eigenvalue analysis, 21 frames = base + 20 requested modes), not a Riks history —
required a fix to `presentation/render/render_odb.py` (AUTO deformation scaling
instead of uniform x1, and restricting playback to frames [0,1] instead of
  subsampling across all 20 unrelated eigenmodes) since neither existed
  before this idea needed to render a non-coiling buckle-only result.
-->

---
layout: two-cols-header
class: idea-slide
---

# D27 &middot; Chiral shell vane longeron

::left::

<div class="text-sm leading-snug">

- **What:** Reverted to n discrete members (this study's usual sparse
  topology) after D26's monocoque tube suppressed coiling, but gave each
  discrete longeron a genuinely new, non-beam shape: a twisting,
  doubly-curved shell "vane" instead of a solid/thin-walled cross-section.
- **Origin:** direct empirical follow-up to D26 — its own finding (full
  monocoque tube too stiff against global lateral bending) predicts that
  restoring low overall bending stiffness via discrete members should let a
  coiling mode compete again, while keeping the chirality/twist mechanism.
- **Stats:** n=120 &rarr; 0 coil &rarr; 0 riks &rarr; 0 good<br>
  quartiles unavailable — 0/120 Stage-1 coilable, so Stage 2 never auto-escalated<br>
  cleared: none (0 decided) &middot; novel: untested — no design ever reached a Riks solve<br>
  best good: none (0/120 passed every criterion)
- **Verdict:** POWERED · REFUTED · discrete twisting vane<br>
  Reverting to discrete members did not
  fix it: still 0/115 valid designs pass the strict coilability check, so
  the sway failure mode isn't purely a monocoque-stiffness artifact as D26's
  own finding predicted. The weaker "coilable_legacy" proxy (same threshold
  convention every other family uses) passes 34/115 — a much bigger
  strict-vs-legacy gap than D26's, suggesting this family's failure mode is
  genuinely closer to (but still short of) real coiling than the tube's.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/D27_chiral_shell_vane_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Mode 1: 3 discrete twisting vanes, still non-coiling.</div>
</div>

<!--
**Input space:** t_shell&isin;[.2,2] — shell wall thickness. W&isin;[3,15] — vane width. B_max&isin;
[1,8] — vane curvature amplitude. twist_total&isin;[.2,1.5] — per-longeron twist over the mast
height. ratio_pitch&isin;[.3,1], ratio_top_diameter&isin;[0,.4] — usual per-storey pitch/taper
meaning. Fixed: n_longerons=3, ratio_shear_modulus=.3677.

**Seed:** FERTILE — the coilable_legacy gap (34/115 pass the looser proxy vs 0/115 strict)
suggests this family is genuinely closer to real coiling than D26's monocoque tube. Untested:
whether reducing twist_total and/or B_max toward the family's own lower bound continues that
trend into strict coilability, rather than assuming the gap is unclosable.

**Timeline:** This is H1 of run `20260804T221559`, delegation D006 (build) + D007
(120-pt LHS sweep, seed=2007).

**Infra:** ODB archived at data/idea_odbs/20260804T221559_D007_chiral_shell_vane/ (a
representative near-miss, not a "best" point — chosen because it clears the legacy
coilability proxy though not the strict one; n_longerons=3, t_shell=1.313mm,
W=4.225mm, B_max=5.977mm, twist_total=0.5157 rad, ratio_pitch=0.7005,
ratio_top_diameter=0.0742; sigma_crit=0.494 kPa, far below target and not coilable
regardless). Fidelity gate: thin-shell validity on the vane's own peak local radius of
curvature (R_eff = L&sup2;/(&pi;&sup2;&middot;B_max)), requiring R_eff/t_shell&ge;20
— this family's analog of the B31 slenderness&ge;10 floor / D25 tape-spring's
R_tape/t_tape&ge;10 floor. 5/120 designs rejected by this guard before the
coilability check. The per-longeron coupling (LOCAL_DATUM_i CARTESIAN, one local
datum per vane) reuses the tape-spring idea's (D25) coupling convention literally,
per this delegation's explicit instruction not to invent a new one. GIF: same
render_odb.py fix as D26 (AUTO scale, frames [0,1] only) applied here too — this ODB
is also a *BUCKLE step with 21 frames (base + 20 modes), not a Riks history.
-->

---
class: summary-slide
---

# Run `20260730T020245` — summary

<div class="text-sm leading-snug">

H3–H4 test the tape-spring's *mechanism*; H5–H8 are follow-up searches within that
same design family (see idea slide below) — none reached the 2% strain target.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H3 | Strain is set by the mast's overall coiling, not by a local fold (rival theory) | ❔ | predicted and measured strain matched on average, but the pattern didn't hold consistently design-to-design | D25 |
| H4 | Is a shell's σ_cr directly comparable to a beam's σ_cr? | ❔ | the check this needed couldn't run — every shell result here is an upper bound only, not a firm number | D25 |
| H5 | Wide, shallow ribbon escapes the strain floor | ❌ | badly underpredicted the real strain; a different failure mode (local buckling) hits first in 60% of designs | D25 |
| H6 | True strain minimum sits in an untested middle range | ❌ | best result there: 4.64% strain, still well above the 2% target | D25 |
| H7 | Near-misses were partly a measurement bug | ❌ | bug confirmed and fixed, but the fix helped some designs and hurt others — none reached the target either way | D25 |
| H8 | Dense search right around the closest miss | ❌ | best confirmed result: 2.7% strain, still 35% over the 2% target | D25 |

 &nbsp;&middot;&nbsp; **Cost: $42.87**
</div>

<!--
Run stats: all-Sonnet with an Opus-strategizer, GATED, evals_used=407,
14 delegations, 0 tool-call errors on the critical path. H1 (oracle
re-confirm, -0.0062% deviation, mcs/mls reproducing to 4-5 sig figs)
excluded from this deck entirely per the format contract. H2 (the
tape-spring fold mechanism itself) has its own idea slide, immediately
above.

Baseline is STILL 0.7704 kPa (`run17_rectangle`) — this run's headline is a
mechanistic negative result, not a new design. Of 407 ledgered
evaluations, exactly ONE is feasible: the run17_rectangle anchor itself
(0.770352 kPa), re-solved as this run's D002 oracle-wiring control, not a
discovery of this run. All 406 shell (circular=17) evaluations are
infeasible.

H3 detail: the strongest evidence in the run for the κ_coil·c law is
magnitude agreement (mean ratio 0.946, sd 0.533) and direct kinematics (no
cross-section flattens; curvature spreads over 25-50% of length; peak
strain sits near the free edge, across_frac 0.868-0.905) — exactly what an
extreme-fibre bending law predicts and exactly NOT what a localized fold
predicts. But the registered PREDICTION was a conjunction, and a
conjunction with one contradicted clause cannot be scored SUPPORTED
(Charter §4) — hence INCONCLUSIVE, with the sharper magnitude claim
re-registered fresh as H5.

H4 detail: this is the run's harshest self-imposed check, and it could
only be partially executed. The registered falsification criterion
demanded an amplitude sweep (~t/10 to ~t); D011 found by direct code
inspection that `workspace/data_generator.py` sets
`sim2_params["imperfection"]` as an unconditional constant (0.067mm),
never read from the design dict for any family, so the sweep the criterion
demanded is simply not executable through the registered oracle. This does
not affect the run's headline (no shell design was ever feasible), but it
means every shell sigma_crit value in this run's ledger must be read as an
UPPER BOUND on the true physical buckling load, not a number directly
comparable to the beam families' sigma on the same footing.

H5-H8 detail: each is a corridor sub-search or targeted recheck of the
SAME tape-spring shell family (H2), not a separate mechanism, per this
deck's rule 1 — full stats live in the idea slide's own speaker notes,
above. Five stalled/non-converged solves masquerading as low-strain
artifacts were caught and excluded across this run's campaigns (one per
H5/H6/H8's underlying delegations plus two more in the deep-corridor
data) — each recorded explicitly in `hypotheses.json` so none is ever
later cited as a success.
-->

---
layout: two-cols-header
class: idea-slide
---

# D25 &middot; Thin-walled open circular-arc ("tape-spring") longeron

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the solid B31 longeron with a thin-walled, open-arc S4R
  **shell** section, hypothesizing a *localized elastic fold* could escape
  the mast-scale coiling curvature capping every beam family.
- **Origin:** Named for Calladine inextensional shell-folding theory and
  Seffen–Pellegrino tape-spring mechanics.¹
- **Stats:** n=406 → 176 coil → 137 riks → 0 good
  p50/p90/p100 — σ_crit: 2.11/17.6/88.3 · mcs: 1.02/1.04/1.06 · mls: .047/.130/.447
  cleared: 128 of 137 decided ≥ 2× Bessa (0.2244) · novel: yes — the σ threshold isn't the
  gate here, mcs/mls (strain) are, so raw σ clears easily while every design still fails
  best good: none (0/406 passed every criterion)
- **Verdict:** POWERED · REFUTED · localized elastic fold<br>
  The curvature keeping the arc locally stable is the same curvature setting its
  bending-strain floor — it can never be shallow enough to fold locally without first
  buckling, so strain follows ordinary beam bending at every depth, not a fold.
<div class="text-xs opacity-50 mt-1">
¹ Named theories cited by the delegation; no single specific paper was looked up/verified this run.
</div>

</div>

::right::

<div class="flex flex-col gap-2" style="height: 450px">
  <div class="flex items-center justify-center" style="height: 170px">
    <img src="/gifs/D25_tape_spring_mini.png" style="max-height: 170px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 272px">
    <img src="/gifs/D25_tape_spring_landscape.gif" class="rounded shadow-lg" style="max-height: 272px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** t_tape&isin;[.4,1.6] — tape thickness. R_tape&isin;[6,400] — arc radius.
alpha_tape&isin;[.05,2.2] — arc angle subtended (section depth driver). beta_tape&isin;[0,3.14] —
section orientation. ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] — usual
per-storey pitch/taper meaning. Fixed: circular=17 (cross-section-family switch), n_longerons=3,
n_storeys=1, twist_angle=0, ratio_shear_modulus=.3677.

**Seed:** BARREN — twist the arc along the sweep, so no station carries the
full curvature, was already tried and settled (68 more under contact, 0 feasible).

SEED RATIONALE (added 2026-08-08, rule 3(e)). The arc is straight along the sweep, so every
station carries the same section curvature and therefore the same bending-strain floor -- the
mechanism this campaign falsified. A twist re-orients the section along the length, so the floor
is not set everywhere at once. That is a genuine perturbation of the idea, not a re-run of it.
Partly attempted already as D27 (chiral shell vane), which reached 0/115 coilable -- but that was
STAGE-1 ONLY and PRE-CONTACT, so the mechanism is unrefuted rather than supported. Whoever picks
this up should read the D25 re-study slide first: the idea AS STATED here is now settled under
contact as well (68 further designs, 0 feasible).
This is H2 of run `20260730T020245` (all-Sonnet, Opus-strategizer, GATED,
evals_used=407, 14 delegations). H1 (oracle re-confirm, -0.0062% deviation)
is excluded from this deck entirely per the format contract. H3–H8 are
companion/rival/refinement hypotheses of this SAME run and are covered on
this run's own summary slide, not repeated here — consistent with the
`20260727T011550` bistable-arch worked example.

Full mechanistic picture, carried here because it is the run's central
finding:
- **Deep corridor (H2/H3):** sections lose to extreme-fibre bending
  (measured/(κ_coil·arc_depth) = 0.946 mean, Pearson r=0.545) — the rival
  H3 hypothesis (strain ~ κ_coil·c for ANY cross-section) is the better
  description of the physics, though its own registered correlation clause
  (ρ>0.5 vs arc_depth) fell short at ρ=0.358, keeping H3 itself
  INCONCLUSIVE rather than cleanly SUPPORTED.
- **Shallow-wide corridor (H5):** making the section wide and thin does not
  buy low strain — a competing local plate/free-edge instability preempts
  the global coiling mode in 60% of designs, and measured strain there
  (0.0576–0.2046) is 3.9–48× the value the fold-scale law predicted. This
  is a direct refutation of H5's own motivating premise that the B31
  (the simple 1-D beam element type used to model each longeron) slenderness
  floor was merely a simulator-validity limit rather than a
  real physical constraint.
- **Intermediate corridor (H6):** no interior strain minimum — the
  corridor's own best converged design (mls=0.0464) sits between the deep
  and shallow flanks, not below both, with 65% local-mode preemption.
- **Measurement integrity (H7):** a mid-run post-processor bug was found
  and fixed — max_local_strain had been truncated using the Riks
  load-proportionality factor as a proxy for true compression
  (`|U3|/mast_height`), silently scanning past mcs=0.80 for most designs.
  Re-solving the 4 lowest-strain deep-corridor designs through the
  corrected oracle flipped one design's ring_passthrough 1→0 and improved
  its strain (-9%), but also made another design's strain WORSE (+25%) —
  a bidirectional correction, evidence the fix is genuine rather than a
  thumb on the scale. None reached the 2% cap.
- **Local sweep around the closest near-miss (H8):** design C (t_tape=
  0.419, R_tape=19.675, alpha_tape=0.639, beta_tape=1.483, ratio_pitch=
  0.845, ratio_top_diameter=0.360; corrected mls=0.027516, σ=0.6167 kPa,
  ring_passthrough=0 — the run's single closest miss, failing ONLY
  criterion 3) was swept densely (51 evals + mandatory mesh-refinement
  confirmation). The steering variable (arc_depth) had NO local purchase
  on strain (slope -0.0061/mm, r=-0.17) — flat to mildly inverted. Best
  mesh-CONFIRMED design (P023): mls=0.027053, still 1.35× the cap. The
  mesh check earned its place: P035 looked like a winner at the default
  mesh (0.024783, beating C) but rose 16.4% under refinement, ending worse
  than C — exactly the class of false positive this study has had to
  retract before (see the bistable-arch slide).
- Constructive diagnosis (why, not just that): a curved shell section
  needs transverse curvature to be locally stable; that same transverse
  curvature (= depth in the coiling-bending plane) is what sets the strain
  floor. The feature that was supposed to enable fold localization is the
  same feature that forbids the fold from ever going shallow enough.

ODB used: `data/idea_odbs/20260730T020245_H2_tape_spring/` (archived from
scratch `riks_61bd47913d8e45ff9e0a124d3536305d`, D012's corrected re-solve
of design C — the run's own closest-miss, chosen per the format contract's
no-winner convention: a typical, well-converged, thoroughly-characterized
design from the search, not the literal best nor an empty slot). This ODB
has NO `E` field output at all (S4R shell family with self-contact enabled
records only `LE`, `S`, contact variables, COORD, U/UR, RF/RM) — the
render script's existing try-E-else-LE fallback (built originally for the
pin-jointed tensegrity truss) picked LE11 automatically with no code
change needed; see `render_odb.py` gotcha 5b and this deck's format
contract for the confirmed detail.
-->

---
class: summary-slide
---

# Run `20260729T012952` — summary

<div class="text-sm leading-snug">

Smallest-budget run in this batch (93 evals); no new idea — all three fold
into existing idea slides (chiral-brace, bistable-arch) as refinements.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | Split single-ring chiral brace into N≥3 parallel ligaments | ⏳ | lit only: weak N^-1/3 scaling; elements share strain, don't distribute it; never tested | D15 |
| H3 | Distribute bistable arch segments along the full longeron | ❔ | confounded — joint-discontinuity strain check never run; more transition joints than precedent | D24 |
| H4 | Graded/staggered K=3 bistable arch chain | ❌ | reversal signals cluster at the bottom-ring segment at every K, not staggering-specific | D24 |

 &nbsp;&middot;&nbsp; **Cost: $23.10**
</div>

<!--
Run stats: GATED, evals_used=93. H1 (oracle re-confirm, -0.0062% deviation)
excluded from this deck entirely per the format contract.

H3 detail: mls-reduction numbers themselves (19.6%/17.5% from D004/D005
identical-rise controls) were real per the raw beam output, but the
registered prediction explicitly demanded the joint-discontinuity check
before those numbers could be trusted — precisely because that same failure
mode (beam theory underestimating real strain at a curvature-discontinuity
joint) is what forced the retraction of `20260727T011550`'s H4 headline.
Since the check was never run, and K=2/K=3 configs have 4-6 such transition
joints vs. the single-segment precedent's fewer, INCONCLUSIVE is the correct
call regardless of which way the raw numbers point.

H4 detail: precision fix after adversarial review — "segment 1 reversed in
5/54 K=3 rows" is the raw count; restricted to the ledger-feasible subset,
3 of those 5 remain. Neither reading changes the FALSIFIED verdict.
-->
---
class: summary-slide
---

# Run `20260728T023457` — summary

<div class="text-sm leading-snug">

Aperiodic bracing lowers ligament strain but not enough to clear the 2% wall — the real finding is analytical: peak local strain is structurally coupled to member stiffness across every family tried this study, not just bracing.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | Peak strain (mls) at high σ is invariant, only reducible by a compound aperiodic-bracing+clearing mechanism | ❌ | conjunctive claim; strain-clears-2%-wall conjunct fails — 0/280 designs clear it | D15 |
| H3 | Aperiodic (golden-ratio) elastic bracing network beats single periodic ring/helix brace | ❌ | lowers ligament strain (6.03% vs 13.92%) but feasible-σ and ≤2%-strain regions never overlap | D15 |
| H4 | Peak local bending strain is structurally coupled to member cross-section size/stiffness, across every family | ✅ | ρ=0.534/0.512/0.690 within all 3 sub-campaigns, all clearing the ρ>0.5, p<0.01 bar | — |
| H5 | Tapering the brace ligament relieves ligament strain | ❔ | 10-pt diagnostic: strain fell only 14.3% while σ fell 22.4% — worsening trade-off, full campaign not run | D15 |

 &nbsp;&middot;&nbsp; **Cost: $24.72**
</div>

<!--
Run stats: GATED, evals_used=294. H1 (oracle re-confirm, matches to 4-5 sig
figs) excluded from this deck entirely per the format contract.

H2 detail: same adequate 280-eval evidence base (D004+D005+D006) used for the
structurally identical H3 claim below; a conjunctive prediction is false if
either conjunct is false, and the "clears the wall" conjunct is the one that
fails here.

H4 detail: this is the run's most load-bearing analytical result — it
generalizes the mls-wall finding across every beam/brace family tried in the
whole study, not just bracing, and explains why so many "novel" mechanisms
independently hit the same strain ceiling.

H5 detail: higher tapers (0.6-0.85) caused solver stalls rather than further
strain relief; the full pre-registered multi-D BO campaign was not run
(deliberately, given the diagnostic's discouraging trend), so this stays
INCONCLUSIVE rather than FALSIFIED.
-->

---
class: summary-slide
---

# Run `20260727T011550` — summary

<div class="text-sm leading-snug">

The run's own headline design (H4, bistable-arch reinvestment beating baseline) was retracted post-hoc once a continuum submodel showed the beam idealization understated real joint strain by 2.7×+ — that retraction was itself later reversed (2026-08-18, a restrained-warping check found corrected strain 1.963%, under the ceiling; see D24's own slide).

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | Bistable shallow-arch snap segment near bottom ring cuts mls by ≥20% | ❌ | real effect (16/24 feasible, mean ~7%, max 12.3%) but short of the 20% bar | D24 |
| H3 | mls is a near-invariant kinematic property of coiling, independent of cross-section/added segments | ✅ | same 24-pt grid; no design cleared the 20% refutation threshold | D24 |
| H4 | Reinvest H2's mls headroom via joint cross-section+arch re-opt to beat 0.7704 kPa | ✅ | retraction reversed 2026-08-18 — restrained-warping check found real joint strain 1.963%, under the ceiling; see D24's own slide | D24 |
| H5 | Second, independently-snapping arch at top ring further lowers mls | ❌ | top segment never actually snaps | D24 |

 &nbsp;&middot;&nbsp; **Cost: $26.32**
</div>

<!--
Run stats: all-Sonnet, 12h budget, finished in ~6.5h, GATED on 3rd critic
attempt, evals_used=133, 0 errors. Baseline STILL 0.7704 kPa — the run's own
headline claim was retracted post-hoc, see H4's slide for the full account.
H1 (oracle re-confirm, 0.006% relative error) excluded from this deck
entirely per the format contract.

Post-hoc finding (2026-07-27), after the run closed: the H4 headline
(0.850864 kPa) sat at mls=0.0196, a hair under the 2% ceiling, right where
the arch's curvature transitions into the plain longeron. A continuum
(solid, not B31 beam) submodel of that exact joint — control-tested against
the literature Bessa point to confirm the submodel methodology itself was
trustworthy (it was) — found real local strain at that joint running 2.7x+
over the beam-reported value by mid-compression, still climbing with mesh
refinement. The headline is retracted; baseline remains 0.7704 kPa. This is
a worked example of the study's own "Scientific integrity of simulation
results" principle: a beam-reported number sitting right at a feasibility
wall, next to a geometric discontinuity the beam idealization can't see
into, is exactly the situation that deserves a faithfulness check before
being trusted.
-->

---
layout: two-cols-header
class: idea-slide
---

# D24 &middot; <u>Single bistable shallow-arch snap segment near the ring joint</u>

::left::

<div class="text-sm leading-snug">

- **What:** Spliced one bistable, shallow-arched snap-through segment near
  the bottom ring, jointly re-optimized with the base cross-section, to
  reinvest local-strain headroom into higher σ_cr,nd than 0.7704 kPa.
- **Origin:** elastic-instability/bistable-mechanism metamaterials
  literature; follow-on to a same-run hypothesis whose single-arch strain
  cut (mean ~7%, max 12.3%) fell short of a pre-registered 20% bar.
- **Stats:** n=133 → 132 coil → 66 riks → 1 good (6.5× Bessa)
  p50/p90/p100 — σ_crit: .76/1.50/1.99 · mcs: 1.00/1.00/1.04 · mls: .0194/.0230/.0267
  cleared: 66 of 66 decided ≥ 2× Bessa (0.2244) · novel: yes — genuinely varied arch geometry,
  not duplicates; measured under the retired pre-contact eigenvalue metric (see notes)
  best good: a=.00961 b=.033165 arch_rise=.0343 arch_length=.4305 → σ=.8509 mcs=1.00 mls=.0196
- **Verdict:** SUPPORTED · WORKS<br>
  **Retraction reversed 2026-08-18** (see speaker notes for why): the decisive,
  boundary-artifact-free restrained-warping check — same method that resolved
  `run17_rectangle`'s identical scare — finds the corrected joint strain holds at 1.96%, under
  the 2% ceiling; the continuum submodel's 2.7&times;+ finding does not survive. **Update (2026-09-01):**
  re-measured under the current contact oracle at a resolution fine enough to converge
  cleanly (10&times; finer arc-length than the oracle's default) — &sigma;_peak=0.6404 kPa
  (5.71&times; Bessa) at mcs=5.07%, clearing the 2&times; bar comfortably; this design's
  status stands under the contact metric too (see Seed for how the default-resolution
  run's very different 1.0495 kPa/false-snap reading was resolved).


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/D24_bistable_arch_headline_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
**Input space:** a&isin;[.007,.012], b&isin;[.025,.045] — base cross-section semi-axes, jointly
re-optimized with the arch. arch_rise&isin;[.02,.09] — bistable snap-arch height. arch_length
&isin;[.25,.5] — arch length along the longeron. Fixed: ratio_pitch=.681277,
ratio_top_diameter=.04444, circular=15 (cross-section-family switch), stabilization=1,
dual_arch=1.

**Re-solved under the CURRENT contact oracle (2026-09-01), closing the FERTILE item this
Seed used to pose:** at the oracle's default arc-length (initialInc=5e-3), this exact design
reproduces &sigma;_eig=0.8509 kPa almost exactly (geometry/coilability confirmed) but Stage-2
reports &sigma;_peak=1.0495 kPa at mcs=0.125% AND arch_snap_reversal=1 — a striking,
at-first-glance genuine-snap-confirmed reading, the only positive `arch_snap_reversal` this
whole family's headline design has ever shown. A 10&times;-finer arc-length re-solve
(initialInc=5e-4) converges cleanly with no solver errors, to a smooth curve:
&sigma;_peak=0.6404 kPa (5.71&times; Bessa) at mcs=5.07%, arch_snap_reversal=0.0. Both the
spike and the snap-positive reading are the SAME 1-frame numerical artifact — the identical
signature already established for D24-2's Rank-3 point (see D24-2's own Seed). Pushing
further (50&times;, 100&times;, 250&times; finer) makes the solver fail to converge at all in
this region — a separate solver-brittleness finding, not evidence against the 10&times;-finer
answer, which is this design's best available converged read. Net: the design clears
2&times; Bessa under the current contact oracle (5.71&times;), but — like every other
properly-resolved point in this family — shows no genuine snap.

**Snap not confirmed (2026-08-31, verdict audit):** across every properly-resolved solve in
this whole family — this design, D24-2's Rank-1/Rank-3, and 294/294 chained-arch (D44)
solves — the oracle's own genuine-snap diagnostic (`arch_snap_reversal`) has never once
confirmed a real two-equilibrium snap. WORKS above means the design is real and feasible
under the study's actual pass/fail bar, not that the bistable mechanism itself is confirmed
engaged — see D24-2's Seed and D44's own audit note for the same finding in this family's
other members.

**2026-08-29 update (run 20260829T005522, H4/H8/H10 -- a broader family search, NOT the same
design as above):** a real, adaptive 42-design search of the bistable-arch family's full 6D box
found 13 converged designs, 11 passing every feasibility criterion -- genuinely working designs
exist elsewhere in this family. The best clears 2x Bessa (~2.4x). But the actual bistable-snap
mechanism was not confirmed in any of them: only 1 showed any snap-reversal, and it is a known
near-zero-compression numerical artifact (mcs_at_peak=0.00125). Whether the good designs' capacity
comes from the snap idea specifically, or from ordinary cross-section/pitch geometry, remains
unresolved (H10, which asked exactly this, was itself confounded). Does not change the
retraction/reconfirmation history below, which concerns a single, different, already-litigated
design point.

Full context — this is one of the most consequential, previously-contested
results in the whole study; state it carefully and consistently with the
CURRENT state of PROBLEM_STATEMENT.md and bo/confirmed_anchors.json (checked
2026-07-29), not any earlier draft:

- Registered as H4 of run `20260727T011550` (all-Sonnet, 12h budget, finished
  ~6.5h, GATED on 3rd critic attempt, evals_used=133, 0 errors). This run's
  H1 (oracle re-confirm) is excluded from the deck entirely. H2 (single
  bistable arch, mls-reduction-only test, FALSIFIED against its own
  pre-registered 20% bar despite a real ~7% mean effect) and H3 (mls is a
  near-invariant kinematic property, SUPPORTED at the registered bar) are
  companion hypotheses of the SAME run and are covered on this run's own
  summary slide, not repeated here.
- H5 (same run, a second/top-ring arch) is a REFINEMENT of this idea, not a
  new one, per the deck format contract's explicit worked example — even
  though H5's design point (0.850864 kPa, i.e. the same design cited above)
  is literally the number this whole study's headline claim rests on. H5
  itself is FALSIFIED on its own stated mechanism: `arch_snap_reversal_top=0`
  in every tested config, meaning the "second arch" never actually snaps —
  it is a curved-but-monotonic compliant segment, not a second bistable
  element. Both H4 and H5 point at the exact same retracted design; there is
  only one design here, and only one verdict on it (retracted).
- **The manifest (`data/idea_odbs/MANIFEST.md`) and this ODB folder's own
  `PROVENANCE.txt` still describe this design as "SUPPORTED (valid
  headline)" / "this study's best fully-valid headline design" — that text
  predates the post-hoc retraction and is now STALE.** The authoritative,
  current status lives in `PROBLEM_STATEMENT.md`'s run-by-run log (search
  "Post-hoc finding (2026-07-27)") and is what this slide follows: retracted,
  baseline remains 0.7704 kPa.
- Separately and NOT to be confused with this retraction: the 0.7704 kPa
  `run17_rectangle` baseline itself went through its own same-day
  (2026-07-28) continuum-FE scare (apparent 1.4-3.6x strain amplification
  across every rectangular design) and was then RECONFIRMED valid via a
  decisive 6-cut-distance convergence study (`validation/warping_check/README.md`
  Round 6) — true amplification ~1.05x, corrected joint strain ~0.0181,
  comfortably inside the 2% ceiling. `run17_rectangle` is the currently
  cleared, confirmed 5.9x-Bessa design (`bo/confirmed_anchors.json`); it is
  cited for context only, not as the bar to beat (the study's actual target
  is 2x Bessa plus genuine mechanism novelty). `h8_rectangle` and this
  chained-arch design were NOT re-checked with that convergence method and
  remain unconfirmed on that specific question.
- Stats-migration note (2026-08-04): D006 of this same run's own ledger records a
  stronger raw result (σ_crit=1.144 kPa, `campaign_summary.json`) for a design in
  this same bistable-arch-near-ring-joint family. It doesn't change anything above
  — the retraction applies to the MECHANISM (any arch-to-longeron joint in this
  family), not to the one specific 0.850864 kPa design, so a stronger raw number
  from the same family is equally retracted, not a missed opportunity.

- **2026-08-18 UPDATE — RETRACTION REVERSED, edited in place by explicit user
  instruction ("update D24 slide in place for this time only").** This is a
  deliberate, one-time exception to rule 3(d)/7(d)'s append-only convention (a
  re-test would normally earn a new numbered slide, e.g. "D24 revisited"), made
  because this is not a re-test under a changed contract — it is a correction of
  the RETRACTION's own grounds, the same situation `run17_rectangle` resolved
  same-day before any slide existed to show the interim wrong state. D24's
  retracted state sat in this deck for weeks first, so there is no clean "final
  state only" slide to write instead; this note preserves the full arc rather
  than erasing it.
  Ran `validation/warping_check/restrained_warping_check.py` (the exact tool and
  method that reconfirmed `run17_rectangle`, Round 6) directly against this
  design's own archived ODB (`data/idea_odbs/20260727T011550_H4_bistable_arch_single_segment/`,
  confirmed still present with its `.inp` — no re-solve needed). Result
  (`validation/warping_check/results/D24_bistable_arch_single_segment.json`):
  `corrected_total_strain_at_global_peak = 0.019630` (1.963%), `verdict: "HOLDS UP
  (below ceiling)"`. The correction at the global peak location is negligible
  (`eps_extra_at_peak_location` ~1.8e-9); even at the joint zone specifically
  (frame 818) the corrected strain is 1.856%, still under the 2% ceiling. This
  does not confirm the archived continuum submodel's 2.7×+ amplification claim —
  consistent with that submodel's own known failure mode (a driven cut boundary
  contaminating the peak-strain location), the same artifact that caused
  `run17_rectangle`'s own scare.
  **What this does NOT do**: it does not re-measure this design under the
  current σ_peak/contact-oracle infrastructure (this design predates 2026-08-06
  and has only ever been reported in the retired eigenvalue metric), and it does
  not change "The current baseline" section of `PROBLEM_STATEMENT.md` or
  `bo/confirmed_anchors.json` — both still cite `run17_rectangle`. Whether this
  design should be re-solved under the current oracle and potentially become a
  new incumbent is a separate, larger decision, not made here.
- ODB used for this render: `data/idea_odbs/20260727T011550_H4_bistable_arch_single_segment/`
  (archived from scratch riks_b8226d64576d43f4b8b9724b9ec7daf8) — this is the
  retracted design's own Riks solve, shown because the format contract's
  "no-winner convention" calls for a faithful native render of a TYPICAL
  design from the idea's search, not an empty slot, even for a retracted
  result. Rendered fresh this session; the pre-existing `bistable_winner.gif`
  and `dual_arch_winner.gif` in `assets/public/gifs/` are old
  matplotlib-pipeline renders of this same design family, not native-Abaqus
  exports, so per the format contract's native-only rule they are not reused
  here.
- Two later runs (`20260728T023457`, `20260729T012952`) tested further
  variants of this bistable-arch idea (golden-ratio-spaced multi-arch,
  multi-location arches, graded K=3 chains); all are refinements folding into
  this same idea and are covered only as bullets on their own runs' summary
  slides.
-->

---
class: summary-slide
---

# Run `20260724T012622` — summary

<div class="text-sm leading-snug">

Four attempts at escaping the strain ceiling all fail, and a dedicated twist-angle sweep shows why: local strain is set by coiling curvature demand itself, not by any cross-section shape this run tried.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | Continuously-twisted rectangle cross-section ("twisted-strip" beam) | ❌ | existence search stopped at 43/~100-110 planned evals, 1/43 feasible — underpowered; properly-powered 2026-08-03, see speaker notes | — |
| H3 | The local-strain wall is intrinsic to coiling curvature demand, not a fixable cross-section problem | ✅ | 8-pt twist sweep 0-120°: mls only rises (1.99%→5.01%), σ twist-invariant (<0.07% drift) | — |
| H4 | Fractal-order longeron centerline perturbation lowers peak strain | ❌ | matched quad, order 0-3: mls flat-to-slightly-increasing at every order | — |
| H5 | Swap chiral brace planform for a true helical coil | ❔ | ligament strain falls 9.05%→6.00%, still 3× over the 2% limit (rests on 3 non-converged salvage reads, not settled) | D16, D15 |

</div>

<!--
Run stats: all-Sonnet, 12h, GATED, evals_used=272, $26.83. Baseline unchanged
at 0.7704 kPa. H1 (oracle re-confirm, bit-consistent re-solve) excluded from
this deck entirely per the format contract.

H2 detail: existence-search prong self-corrected from an initial over-eager
FALSIFIED back to INCONCLUSIVE once the validator flagged the campaign as
short of its own pre-registered power bar. Properly-powered out-of-band
verification (2026-08-03, not a new agentic run): a 3-phase shrinking-zoom
CEI-BO and a TuRBO trust-region search, 120 real evals each, against the same
D005 oracle. 3-phase zoom found best sigma_crit=0.1106 (14.4% of the 0.7704
target), improving monotonically each phase (0.040->0.069->0.111); TuRBO
found 0.0332 (4.3%), plateauing early once its trust region shrank to its
floor. Neither beats the target, so H2 stays FALSIFIED as an existence-beats-
target claim, but the direction is now a real signal, not noise, and the
verdict no longer rests on an underpowered campaign.

H3 detail: this is a real, substantive analytical/mechanistic result, not a
single-design test — it argues the mls wall is intrinsic to coiling
kinematics rather than any one cross-section's fault, motivating why later
cross-section and bracing variants keep hitting the same ceiling.

H5 detail: broadest sweep's own best point was 4.22% ligament strain at a
much lower-sigma design (sigma=0.627), farther from the 2% threshold than
`20260721T201733`'s own 2.15% near-miss — this run explored a different
brace shape without closing the gap. Every config keeping the ligament under
budget destabilizes the host's own coiling (mcs collapsing to 0.27-0.37); the
one all-criteria-satisfying config sits at a near-zero-sigma corner
(sigma=0.0143 kPa). A real, well-evidenced negative result, not proof of
absence.
-->

---
class: summary-slide
---

# Run `20260723T010834` — summary

<div class="text-sm leading-snug">

Chained true-bistable snap-through segments hit a solve-completion wall, not a strain wall, while a real counterexample confirms the milder sub-bistable arch family from the previous run.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H2 | Chain of true-bistable (Q≥2.31) snap-through arch segments | ❌ | solve-completion wall, not a strain wall — 18 coilable, only 2/18 converged with valid stabilization, 1 near-degenerate "success" | D23 |
| H3 | (Absence claim) no valid chained mild pre-curved sub-bistable arch design exists | ✅ | refuted — real counterexample found, σ=0.776506 kPa, see idea slide | D23 |

 &nbsp;&middot;&nbsp; **Cost: $18.00**
</div>

<!--
Run stats: GATED, evals_used=206. H1 (oracle-wiring re-confirm) excluded from
this deck entirely per the format contract.

H2 detail: mechanistically-explained wall, not noise — the same Riks-stall
failure (arc-length solver cannot traverse the sequential snap-through
equilibrium path) recurs across n_segments=2..6 and across 2+ orders of
magnitude in cross-section size, matching a priori literature risk flagged
during the run's own literature review (arXiv:2010.07850: snap-through is
rate-dependent/delayed-bifurcation even in the ideal quasi-static elastic
case). Of 18 coilable (Stage-1-passed) true-bistable-regime designs, only
2/18 converged with a valid stabilization-energy ratio, and of those only 1
met both mcs>=0.80 and mls<=0.02 — a near-degenerate cross-section at
sigma_crit=0.001622 kPa, ~475x below the 0.7704 kPa target — not a real
candidate. (Corrected 2026-08-26, deck audit item 1: this paragraph
previously quoted "23/72 coilable... sigma=2.97e-5 kPa" -- D005's numbers,
the earlier 72-eval campaign the very next paragraph explains was retracted
for being confounded. The numbers above are D006's, the actual corrected,
validator-satisfying campaign this paragraph has always claimed to describe.)

H2 self-correction (why this FALSIFIED is trustworthy, not premature): the
strategizer's FIRST attempt at this verdict, based on an earlier 72-eval
campaign (D005), was ALSO "FALSIFIED" -- but the automated verdict validator
rejected it, citing a Duhem-Quine confound: the registered criterion demanded
a >=100-eval campaign, D005 ran only 72, and its failure mode (Riks
non-convergence) is confounded with a possible solver/rate limitation rather
than demonstrated evidence the mechanism itself fails. The strategizer
retracted to INCONCLUSIVE and re-ran a properly-powered, non-confounded
follow-up (D006, above) before re-closing FALSIFIED -- the detail above IS
that corrected, validator-satisfying campaign, not the original rejected one.
Strategizer's own retrospective calls this "the single most important thing
that happened this run."

H3 detail: registered falsification criterion was explicit — "a single valid
(slenderness>=10, all 5 criteria) design beating 0.7704 kPa refutes the
absence claim outright." D004 found exactly such a counterexample at
circular=11 (n_segments=3, arch_rise_ratio=0.10, run-17-rectangle base
cross-section): sigma_crit=0.776506 kPa, mcs=1.032523, mls=0.019394,
slenderness=10.248; ring-passthrough independently confirmed clear via a
dedicated follow-up delegation (D007) that bit-identically cross-checked the
original Riks solve. Note this counterexample sits in the SUB-BISTABLE regime
(Q~1.23, below the 2.31 true-bistability floor) — a mild alternating
pre-curvature, not genuine snap-through. Not re-checked with the continuum
cut-distance convergence method (unlike run17_rectangle) — see this idea's
own slide notes for the caveat.
-->

---
layout: two-cols-header
class: idea-slide
---

# D23 &middot; <u>Chained mild pre-curved ("sub-bistable") arch-segment longeron</u>

::left::

<div class="text-sm leading-snug">

- **What:** Chain of N alternating-sign pre-curved shallow-arch segments,
  rise-to-thickness ratio (Q) kept *below* the bistability floor (Q≈2.31) —
  mild repeating curvature, not genuine snap-through.
- **Origin:** follow-up to the same run's H2 (*true* bistable, Q≥2.31
  chain), which hit a Riks numerical wall in 71/72 cases; asks whether
  backing off avoids the wall while still beating baseline.
- **Stats:** n=133 → 19 coil → 3 riks → 1 good (5.9× Bessa)
  p50/p90/p100 — σ_crit: .12/.65/.78 · mcs: 1.00/1.03/1.03 · mls: .0194/.0267/.0285
  (quartiles from just those 3 points, not a real distribution)
  cleared: 1 of 3 decided ≥ 2× Bessa (0.2244) · novel: yes, thin — the one clearing point is
  also the slide's own best-good design, too few points to call it a population
  best good: n_segments=3 arch_rise=.10 → σ=.7765 mcs=1.03 mls=.0194
- **Verdict:** FALSIFIED · WEAK<br>
  As an absence claim — one genuine 5-criteria
  counterexample beats the 0.7704 kPa baseline. Valid, but a mild curvature
  perturbation, not the true bistable mechanism originally proposed. **Not yet
  continuum-reconfirmed (see Deferred) — treat the +0.8% margin as unconfirmed,
  not cleared.**


</div>

::right::

<div class="flex flex-col gap-2" style="height: 450px">
  <div class="flex items-center justify-center" style="height: 170px">
    <img src="/gifs/D23_chained_bistable_arch_mini.png" style="max-height: 170px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 272px">
    <img src="/gifs/D23_chained_bistable_arch_landscape.gif" class="rounded shadow-lg" style="max-height: 272px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** n_segments&isin;[2,6] — chain length (discrete). arch_rise&isin;[.02,.3] — per-
segment rise, kept below the Q&asymp;2.31 bistability floor. Fixed: a=.009213, b=.033238,
ratio_pitch=.681277, ratio_top_diameter=.04444, circular=11 (cross-section-family switch).

**Seed:** FERTILE — apply the restrained-warping check that resolved D24's own numerical scare
to H2's TRUE bistable (Q&ge;2.31) chain variant, which hit a Riks convergence wall in 71/72
cases rather than a physics failure; untested whether that wall is the same class of solver
artifact, not a real barrier.

**Deferred:** 0.7765 kPa (this idea) is marginally above the 0.7704 kPa rectangle
baseline (+0.8%) — a real but very thin margin, not a decisive win. IMPORTANT —
continuum-verification caveat: per PROBLEM_STATEMENT.md's "More background" section
and `bo/confirmed_anchors.json`'s `_README`, only `run17_rectangle` has been
re-checked with the decisive cut-distance continuum-FE convergence study (Round 6)
and reconfirmed valid (~1.05x local-strain amplification, well inside the 2%
ceiling). `chained_arch` (this design) was explicitly NOT re-checked with that
method — its 0.019394 beam-reported max_local_strain (a hair under the 2% wall) has
never been independently verified against a continuum joint model. Treat it as an
unconfirmed-but-not-yet-falsified counterexample, not a fully-cleared "beats
baseline" claim, until it receives the same treatment run17_rectangle got.

**Timeline:** Registered as H3 of run `20260723T010834` (GATED, evals_used=206). H1 of
this run is the oracle-wiring sanity check and is excluded from this deck entirely,
per the format contract. H2 (chain of TRUE bistable, Q>=2.31, segments) is a
refinement of this same chained-arch idea and is FALSIFIED on a numerical-convergence
wall (D006's corrected campaign: 18 coilable, only 2/18 converged with valid
stabilization, 1 met mcs/mls at sigma_crit=0.001622 kPa, ~475x below baseline — not a
real candidate; corrected 2026-08-26 deck audit, this paragraph previously cited
D005's own retracted 72-eval numbers); it does not get its own slide, see this run's
summary slide.

**Infra:** ODB: `data/idea_odbs/20260723T010834_H3_chained_bistable_arch/` (archived
from scratch riks_adedcff397644c99a451e61cb6127f1b). Rendered fresh this session; no
native gif existed for this idea before (an old-pipeline gif with a similar name does
not exist under this slug — `bistable_winner.gif` and `dual_arch_winner.gif` in the
gifs directory belong to the different, later single-arch idea below, not this
chained-segment idea).
-->

---
class: summary-slide
---

# Run `20260721T201733` — summary

<div class="text-sm leading-snug">

The largest single-run batch this study ran (867 evals, 8 hypotheses) — every chiral-bracing variant tried either fails outright or clears the host's own criteria while violating the apples-to-apples brace-strain check.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Properly-powered re-test of the tapered-longeron family | ❌ | best 0.362763 kPa = 2.78× Bessa but only 47% of baseline | D18 |
| H2 | Doubly-symmetric cruciform/I-beam cross-section | ❌ | own slide, this deck | D22 |
| H3 | Continuous elastic chiral/auxetic bracing at a fixed host | ❌ | only 2/120 evals converged near the boundary — underpowered; properly-powered 2026-08-03, see speaker notes | D15 |
| H4 | Jointly optimize host + chiral brace together | ❌ | numerically supported but not citable — brace strain 7.7–9.1%, same apples-to-apples violation as tensegrity | D15 |
| H5 | Bistable snap-through segment near the ring joints | ⏳ | ran out of budget this run; tested the following run | D24 |
| H6 | Among H4's designs, keep the brace ligament elastic too | ❌ | 440 evals; closest miss ligament strain 2.15%, just over the 2% limit | D15 |
| H7 | Does n_longerons change per-longeron σ? | ✅ | confirms the oracle carries no n_longerons scaling bug | — |
| H8 | Longer/more convoluted multi-loop brace ligament path | ❌ | 349 evals, only 1/349 meets all 6 criteria, at 19% of baseline | D15 |

</div>

<!--
Run stats: all-Sonnet, 14h, GATED, evals_used=867, $59.50. Baseline unchanged
at 0.7704 kPa this run. Explicitly steered toward genuinely novel mechanisms
rather than resizing the known rectangle.

H3 detail: properly-powered out-of-band verification (2026-08-03, not a new
agentic run): a 3-phase shrinking-zoom CEI-BO and a TuRBO trust-region search,
120 real evals each, against the same D007 oracle (host fixed at the
run17_rectangle anchor, only the brace's own 4D geometry searched). Zero
feasible designs in either -- the 3-phase zoom's own phase 1 (40 evals, full
box) already found nothing and correctly declined to zoom further. Combined
with the original 120 evals (D007+D008), that is 280 real evals across 3
independent search strategies with zero feasible hits -- this is no longer an
underpowered result, it is a clean negative.

H4/H6 detail: H4's registered prediction covered only the host's own
criteria (coilable, mcs, host mls, slenderness) and never mentioned brace
strain, so H4 is correctly SUPPORTED on its literal text — closing it as
FALSIFIED post-hoc using the brace-strain finding would itself have been an
improper goalpost move. But every one of H4's 6 winning designs (best
sigma=1.2457 kPa, 9.5x Bessa) has brace-ligament strain 7.7-9.1% in the SAME
PLA material the study elsewhere holds to a 2% elastic-strain convention —
exactly the tensegrity pattern (numerically real, but "wins" only by
relocating strain to an unchecked member). 1.2457 kPa is not a citable
result and never will be for this exact parametrization. H6 settles this:
440 evals across D009 (in-run), D011 (in-run), and a dedicated 220-eval
standalone follow-up (patience never even triggered) find zero designs
keeping host AND brace elastic simultaneously for this single-ring topology.
The near-miss (ligament strain 2.15% vs. the 2.00% limit, at sigma=0.337 kPa
= 2.58x Bessa, which would itself clear this study's 2x target) suggests the
brace mechanism is not dead, only this exact single-ring realization —
PROBLEM_STATEMENT.md explicitly frames a structurally different brace
topology as the genuinely open thread, not a re-run of this box.

H3 stats: ligament strain 7.9-8.8% (genuinely elastic mechanism), but 120
evals across 2 rounds found only 2 Riks-converged near-boundary points — an
inadequate probe of the mcs/mls boundary, not a contradiction.

H7 stats: n_longerons=4, sigma=0.770342 (-0.0014% vs. baseline 3-longeron
value), critical load scales almost exactly proportionally with
n_longerons — independently hand-verified.

H8 stats: 349-eval campaign (D014-D017) spanning the full physically-verified
n_loops in [1,10], patience-plateaued. Best-under-5-criteria is 0.737 (96% of
baseline) and still fails ligament strain.
-->

---
layout: two-cols-header
class: idea-slide
---

# D22 &middot; Doubly-symmetric cruciform/I-beam cross-section

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the anisotropic-rectangular longeron cross-section with an
  open thin-walled cruciform/I-beam profile, chosen so torsional stiffness
  (J) is tunable independently of bending stiffness (Ixx/Iyy), unlike a solid
  rectangle where the two are coupled.
- **Origin:** classical flexural-torsional beam theory (common-sense
  cross-section engineering, not a specific outside citation) — the
  motivating idea was that decoupling J from Ixx/Iyy might let the section
  reach high axial stiffness without paying the local-bending-strain penalty
  the rectangle family pays.
- **Stats:** n=91 → 90 coil → 0 riks → 0 good<br>
  quartiles unavailable — 90/91 Stage-1 coilable, but all 90 failed to reach a converged Riks
  solve, so Stage 2 has no population to compute over<br>
  cleared: none (0 decided) &middot; novel: untested — no design ever reached a Riks solve<br>
  best good: none (0/91 passed every criterion)
- **Verdict:** BLOCKED · UNKNOWN-NO-EVIDENCE · cruciform/I-beam Stage-2 convergence<br>
  A solve-completion wall, not a strain wall: all 90 coilable designs failed
  to reach a converged Riks solution, so the mechanism was never actually
  tested. An untried fix for this exact wall exists — see Seed.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/D22_cruciform_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">From a <b>non-converged</b> solve (see notes).</div>
</div>

<!--
**Input space:** b&isin;[.015,.05] — flange width. h&isin;[.02,.08] — section height.
tf&isin;[.002,.012] — flange thickness. tw&isin;[.0015,.008] — web thickness. ratio_pitch
&isin;[.3,1.5], ratio_top_diameter&isin;[0,.3] — usual per-storey pitch/taper meaning. Fixed:
circular=8 (cross-section-family switch), n_longerons=3, n_storeys=1, twist_angle=0,
ratio_shear_modulus=.3677.

**Seed:** FERTILE — untested whether the 0/90 Stage-2 convergence is a genuine physical
incompatibility or a solver-specific difficulty; this deck's own Explicit-dynamics escalation
resolved an analogous convergence wall for D29/D34 without changing the design, and was never
tried here.

**Deferred:** Stats-migration note (2026-08-04): mcs and max_local_strain do correlate
strongly (r=0.76) among the non-converged salvage reads for this campaign — real
numbers, consistent with classical flexural-torsional coupling, but built entirely on
partial/non-converged Riks reads, not genuine converged solutions, which is why the
Verdict above leads with the solve-completion failure itself rather than this
correlation.

**Corrected 2026-08-31 (verdict audit):** this Deferred note previously claimed
"PROBLEM_STATEMENT.md explicitly lists it as a settled null result" — checked directly,
PROBLEM_STATEMENT.md never mentions cruciform or I-beam anywhere; that citation was
false. This slide's own Seed tag (FERTILE — the Explicit-dynamics fix was never tried)
was the accurate one and the Verdict above has been corrected to match; the family is
BLOCKED on an untried fix, not a confirmed dead end.

**Timeline:** Registered as H2 of run `20260721T201733` (all-Sonnet, 14h, GATED,
evals_used=867, $59.50 for the whole run). Same run's H1 (properly-powered 128-eval
re-test of the tapered-longeron family, best feasible 0.362763 kPa = 2.78x Bessa but
only 47% of the 0.7704 kPa rectangle baseline) is a refinement of an idea that already
has its own slide from an earlier run, so it is NOT repeated here — see this run's own
summary slide for its one-line status.

**Infra:** ODB used for this render: `data/idea_odbs/20260721T201733_H2_cruciform_ibeam/`
(archived from scratch riks_de8c7e06e10b40e2a80fd6146e69eeee). Best *infeasible* sigma
found in the campaign was ~0.68 kPa, below the 0.7704 kPa baseline even before the
strain-correlation problem is considered. GIF: native Abaqus/CAE Viewer render via
`presentation/render/render_odb.py` (E11 strain coloring, top-right legend, schematic
dashed-circle ring overlay recomputed from COORD every frame, portrait 480-wide
canvas), same pipeline as the rest of this deck. Rendered fresh this session directly
from the archived ODB (no native gif existed for this idea before).
-->

---
class: summary-slide
---

# Run `20260718T132852` — summary

<div class="text-sm leading-snug">

Two hypotheses fold into existing idea slides as refinements, while the run's one new mechanism — Class-1 tensegrity — clears the σ target numerically but gets demoted for violating apples-to-apples comparability.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Distributed N-cell (N&ge;3) flexure-hinge chain | ❌ | folds into the flexure-hinge idea's slide | D13 |
| H2 | Smooth continuous taper vs. the piecewise "waisted" family | ❔ | folds into the waisted-tapered idea's slide | D18 |
| H3 | Class-1 tensegrity strut-and-cable replacement (own slide) | ❌ | 220.89 kPa but demoted via the apples-to-apples criterion | D21 |
 &nbsp;&middot;&nbsp; **Cost: $33.67**
</div>

<!--
Per-hypothesis detail:

- H1: does a distributed-compliance longeron built from N>=3 repeated stiff/thin unit
  cells (alternating thick and thin flexure segments) reach sigma_cr,nd>0.7704 kPa at
  full feasibility? D005: 58-eval slenderness-valid constrained campaign, 0/58 fully
  feasible; best mcs>=0.80 point has sigma=2.058 kPa but mls=0.0576 (nearly 3x the 2%
  limit). A corrected matched N-sweep (fixed geometry, hinge_fraction=0.15,
  sigma=0.443 across N=3..6) shows mls DOES decrease slightly with N
  (0.0375->0.0366->0.0360->0.0358) -- a real but far too small effect to reach
  feasibility at competitive sigma. Falsified on the primary (existence-at-target)
  claim.
- H2: does a smoothly (continuously) tapered longeron beat the piecewise "waisted"
  family's issues? D006: 39-eval search, only 1/39 fully feasible, best-feasible
  pinned at sigma=0.2785 across the whole campaign -- the search barely located the
  feasible manifold at all, an inadequate test of an existence claim per the study's
  Charter. Downgraded from an initial FALSIFIED to INCONCLUSIVE. One suggestive
  mechanistic observation: mls clusters at 0.0199-0.0225 across taper_exponent 0.5-4.0,
  i.e. close to but not clearly below the 0.02 limit.
- H3: see idea slide below.
-->
---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T132852</div>

# D21 &middot; <u>Class-1 tensegrity strut-and-cable longeron replacement</u>

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the bending longeron with a pin-jointed, prestressed
  Class-1 tensegrity assembly — stiffness from prestress/geometry, not
  beam bending.
- **Origin:** Amendola et al. (2018) tensegrity prestress-stiffness theory,
  contrasted with Meng (2012)/Sorrentino (2021) on bending-family
  strain-stiffness coupling.
- **Stats:** n=45 → 45 coil → 44 riks → 12 good (1691&times; Bessa)
  p50/p90/p100 — &sigma;_crit: 72.8/220.8/238.4 · mcs: 1.12/1919/2929 · mls: .205/8.41/9.55
  cleared: 44 of 44 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes — 42 distinct designs
  spanning 3 orders of magnitude in &sigma;, but disqualified on comparability (see Verdict)
  best good: a_strut=.03 slen_strut=10.29 area_cable=.0046 mid_h=.523 prestrain=.0193 +2 more &rarr; &sigma;=220.89 mcs=1.15 mls&asymp;9e-14
- **Verdict:** SUPPORTED (DISQUALIFIED) · DEAD-END<br>
  Largest &sigma;_cr,nd in the study (re-verified via direct ODB mode-1
  extraction) — but pin-jointed/prestress isn't comparable elastic bending.
  The broken-looking mcs/mls above (up to 2929/9.55) are a truss-vs-beam
  strain scaling, not an error — the real signal is the near-zero material
  strain apples-to-apples exists to catch (mls&asymp;9&times;10<sup>-14</sup>, i.e. none).

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/D21_tensegrity_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Colour = LE11 (axial strain); no beam bending field here.</div>
</div>

<!--
**Input space:** a_strut&isin;[.0001,.05], slen_strut (reparametrized from ratio_b_strut&isin;
[.0001,.08] as pitch/(2*max(a,b))) — strut cross-section/slenderness. area_cable&isin;[1e-7,1e-2]
— cable cross-section area. mid_h&isin;[.05,.95] — mid-height ratio of the tensegrity's waist.
prestrain&isin;[-.05,.05] — cable pre-tension strain. ratio_pitch&isin;[.1,2],
ratio_top_diameter&isin;[0,.8] — usual per-storey pitch/taper meaning. Fixed: circular=7
(cross-section-family switch), n_longerons=3, n_storeys=1, twist_angle=0,
ratio_shear_modulus=.3677.

**Seed:** BARREN — blocked on printability (prestressed cables, pin joints).

**Timeline:** This is hypothesis H3 of run `20260718T132852`, delegation D005 for the
initial search plus D013 for a dedicated verification-only follow-up (0 new oracle
evals -- direct inspection of already-archived Stage-1 ODBs). D013 settled an
adversarial review's MAJOR finding: is the shared `coilable` flag (computed from the
analytical reference point's UR3 rotation) a genuinely meaningful signal for the
tensegrity topology, given its joint-to-ring coupling ties only translations
(u1=u2=u3=ON, ur1=ur2=ur3=OFF)? D013 extracted the actual mode-1 displacement of the 3
physical strut-top nodes directly and fit a rotation angle independently of the UR3
field: winning design's fitted theta matched the reported UR3 to 5.8e-10 rad absolute
difference (and a non-coiling control case matched to 1.5e-9 rad) -- the flag is
confirmed genuine, not a reference-point artifact. DEMOTION, per project record (this
study's "Artifact vs physical" / "Apples-to-apples criterion" policy): a comparable,
apples-to-apples design must be (a) elastic, no folding/mechanism collapse, (b) a
comparable stress measure, and (c) printable/realizable as a single continuous member
family. A pin-jointed, prestress-driven tensegrity assembly fails (a) and (c) by
construction (it is a mechanism assembly with rigid-body joint rotations, not a
single continuously-bending elastic beam) -- so despite being a real, reproducible,
fully-feasible 220.89 kPa design, it is excluded from this study's beam-family
headline comparisons. WHY "fully feasible" IS trustworthy despite a real gate bug
found mid-run: D009 (implementer, flagged) discovered the mls<=0.02 feasibility gate
was computing a field that does not exist in this ODB and silently returning 0.0 for
every one of 94 designs evaluated so far -- meaning the gate had never actually been
enforced. D010 fixed the oracle (added the missing LE field request) and D011 then
DELIBERATELY discarded all pre-fix ledger rows and re-ran the full campaign fresh
against the corrected oracle (explicitly removing D009's own reuse/idempotency logic
so no stale mls=0.0 row could leak back in). The reported 220.89 kPa / fully-feasible
result is from that corrected, post-fix campaign. Separately, the critic flagged the
287x-over-baseline magnitude itself as CRITICAL-severity implausible against this
study's own commissioned literature review; the strategizer spent two further bounded
delegations (D012 sweep, D013 mode-shape verification above) specifically to settle
that concern with new evidence rather than soften the claim or drop it under time
pressure (strategizer's own closing retrospective).

**Infra:** GIF NOTE: this ODB (data/idea_odbs/20260718T132852_H3_tensegrity/tensegrity_RIKS.odb)
has no 'E' (beam bending strain) field output at all -- physically correct, since
T3D2 truss/cable elements have no bending strain concept. The render script's primary
contour variable was extended with a principled fallback (try E/E11 first; if absent,
use LE/LE11, axial logarithmic strain -- the truss-family analogue of the same
physical quantity) rather than leaving color off or fabricating a bending-strain
field that does not exist for this topology. Only 10 frames were available in this
ODB's Riks step (vs up to 30 elsewhere); all 10 rendered cleanly.
-->

---
class: summary-slide
---

# Run `20260718T071133` — summary

<div class="text-sm leading-snug">

Mining an existing dataset and testing a 2-storey mast both come up empty; the one real hit (H2's built-up longeron) clears feasibility but sits 1000× below the target.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Mine the Bessa 7D dataset for a real, realizable profile | ❔ | folds into the extended-J hollow-tube slide; 0/8 coilable rows pass all 4 criteria | D2 |
| H2 | Laced/battened two-parallel-chord built-up longeron (own slide) | ❌ | existence confirmed (1/50 feasible, real hit); 1000x below target either way | D20 |
| H3 | 2-storey mast reduces peak local strain | ❔ | folds into the multi-storey idea's slide; no clean signal | D4 |
 &nbsp;&middot;&nbsp; **Cost: $16.87**
</div>

<!--
Per-hypothesis detail:

- H1: does the 50,000-point Bessa 7D generalized-cross-section dataset contain an
  independent Ixx/Iyy/J/area combination that, realized through a real
  DURING_ANALYSIS-capable profile (rectangular-anisotropic or box) at fixed
  rsm=0.3677 and slenderness>=10, clears all feasibility criteria? D003 (direct ledger
  re-query via QueryStore, after a numeric-accuracy correction per critic audit): of 8
  coilable rows, 3 pass mcs>=0.80 (all 3 fail mls badly: 0.063/0.112/0.062), 2 pass
  mls<=0.02 (both fail mcs badly: 0.077/0.072), and the remaining 3 fail both at once.
  0/8 pass all 4 criteria simultaneously; max coilable sigma_crit=19.51 kPa (well above
  the floor) but always at the cost of one of the other two criteria.
- H2: see idea slide below.
- H3: does a 2-storey mast built from the known winning rectangle cross-section reduce
  peak local bending strain for a given compression, by splitting curvature demand
  across two storeys? D006 (after a critic-audit correction to the slenderness formula,
  circular==2 now uses max(ratio_a,ratio_b) not ratio_b alone): 3/36 pass the raw
  slenderness threshold under the corrected formula (not 4/36 as originally miscounted);
  0/36 coilable rows were also converged==True. Inconclusive, no clean signal either way.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T071133</div>

# D20 &middot; Laced/battened two-parallel-chord built-up longeron

::left::

<div class="text-sm leading-snug">

- **What:** Replaced each solid longeron with two parallel slender chords
  separated by a fixed gap (a laced/battened built-up member), aiming to
  set global bending stiffness by chord separation while peak local strain
  stays governed by each chord's own small radius.
- **Origin:** common-sense mechanistic hypothesis grounded in the
  parallel-axis theorem (2&middot;A_f&middot;(h/2)&sup2;), not a
  literature citation.
- **Stats:** n=62 &rarr; 50 coil &rarr; 50 riks &rarr; 1 good (0.0061&times; Bessa)
  p50/p90/p100 — &sigma;_crit: .09/2.64/6.15 · mcs: .76/1.03/1.07 · mls: .031/.079/.107
  cleared: 20 of 50 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes — 20 distinct
  designs varying rc/h/n_battens/pitch/top_d; mls (local strain) is the gate that blocks them
  best good: rc=.0024 h=.0234 n_battens=2 pitch=.75 top_d=.13 &rarr; &sigma;=.00079 mcs=1.00 mls=.014
- **Verdict:** FALSIFIED · WEAK<br>
  As a viable mechanism. 50 evals clears this study's existence bar (n&#8805;48, settled
  2026-08-02), and a genuine feasible hit was found, so existence was never in question. The
  real finding is competitiveness: the one feasible design is 1000&times; below target, too
  large a gap to blame on under-search rather than the mechanism.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 430px">
  <div class="flex items-center justify-center" style="height: 160px">
    <img src="/gifs/D20_built_up_mini.png" style="max-height: 160px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 262px">
    <img src="/gifs/D20_built_up_landscape.gif" class="rounded shadow-lg" style="max-height: 262px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** rc&isin;[.001,.02] — chord radius. h&isin;[.01,.15] — separation between the two
chords. n_battens&isin;[2,8] — discrete batten count. ratio_pitch&isin;[.25,1.5],
ratio_top_diameter&isin;[0,.8] — usual per-storey pitch/taper meaning. Fixed: circular=4
(cross-section-family switch), n_storeys=1, twist_angle=0, ratio_shear_modulus=.3677.

**Seed:** BARREN — the one feasible design is 1000&times; below target; a gap this large is a
mechanism ceiling, not an under-search artifact, and no perturbation within this parameter box
plausibly closes three orders of magnitude.

**Timeline:** Stats-migration note (2026-08-04): among the 50 converged designs, &sigma;_crit is
easy to push high unconstrained (p90=2.64 kPa) — only the strain constraint (mls, already over
the 0.02 limit at the median) blocks it; the trade-off is sharp, not a search-coverage gap. This is
hypothesis H2 of run `20260718T071133`, delegation D005 (50-eval CEI-BO campaign over the
laced/battened two-chord longeron). Originally left INCONCLUSIVE per the verdict validator's
critique: with feasibility this sparse (2%), a zero-or-near-zero hit rate could have meant either
"this mechanism is bad" or "the search never found where it's good" -- indistinguishable without
more power. REVISED 2026-08-03 once the study settled a concrete existence-testing default
(n_doe=48, giving p<=6.25% confidence on a zero-hit read): 50 evals already clears that bar, and
unlike the zero-hit case this campaign found a REAL feasible point -- existence is directly
observed, not inferred from an absence. The only open question was ever competitiveness, and a
1000x gap from target is decisive on its own terms; no plausible amount of additional search
closes three orders of magnitude from a single documented mechanism. Flipped INCONCLUSIVE ->
FALSIFIED.

**Infra:** ODB: data/idea_odbs/20260718T071133_H2_laced_built_up/SUPERCOMPRESSIBLE_RIKS.odb,
sourced from presentation/resim/built_up/riks_4a8e6e6a4c504a5abfa2ef1b0d5f21c1. Rendered cleanly
through the full native pipeline; the twin-chord (two-parallel-rod) construction of each longeron
and its coiling motion are clearly visible.
-->

---
class: summary-slide
---

# Run `20260718T031519` — summary

<div class="text-sm leading-snug">

Elliptical top/bottom rings are cleanly falsified again — every point in a 32-point sweep is non-coilable — while a new in-plane meander perturbation idea stays inconclusive.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Elliptical top/bottom rings with phase offset, re-tested | ❌ | every point in a 32-point sweep was non-coilable | D10-2 |
| H2 | In-plane serpentine/meander centerline perturbation (own slide) | ❔ | inconclusive | D19 |
 &nbsp;&middot;&nbsp; **Cost: $17.46**
</div>

<!--
Per-hypothesis detail:

- H1: does replacing circular top/bottom rings with ellipses at an independent
  top-view phase offset contain a slenderness-valid design beating 0.7704 kPa? D006: a
  30-point LHS spanning the full registered 2D box (ellipse_aspect_ratio 0.035-0.970,
  phase_offset 0.0145-1.0269 rad) at the fixed run17_rectangle cross-section returned
  coilable=0 for EVERY point. Two additional near-degenerate boundary probes (aspect=
  0.99/phase~1.1deg; aspect=0.90/phase~2.9deg) were ALSO coilable=0 -- even a ~1 degree
  phase perturbation from the exact circular/zero-phase anchor switches the first
  buckling mode away from coiling entirely. A systematic loss of the coiling mechanism
  across the whole tested box, not a scattered/thin-coverage null result.
- H2: see idea slide below.

**Split out 2026-08-31 (verdict audit):** this H1 previously read "folds into the
elliptical-rings slide" -- old rule-1 language, before D&lt;n&gt;-&lt;k&gt; numbering
existed. Promoted to its own D10-2 slide since it's a real, decisive, well-powered
re-test, not a thin/incidental one (rule 1's own carve-out for folding several
different base ideas' one-design checks into a single slide does not apply here --
this is one base idea, tested properly).
-->

---
layout: two-cols-header
class: idea-slide
---

# D10-2 &middot; Systematic re-test: every point non-coilable

::left::
<div class="text-sm leading-snug">

- **What:** Re-tested D10's ellipse-top/bottom-ring idea with a proper systematic
  sweep — a 30-point LHS spanning the full registered 2D box (ellipse_aspect_ratio,
  phase_offset), plus 2 boundary probes within ~1&deg; of the circular/zero-phase
  anchor, at the fixed run17_rectangle cross-section.
- **Origin:** D10's own base slide could not close FALSIFIED — the study's own
  adequacy bar (Charter &sect;2) blocks a non-existence verdict when the guiding
  surrogates aren't predicting above chance. This re-test answers the question
  directly, by full coverage, not by surrogate prediction.
- **Stats:** n=32 (30 LHS + 2 boundary probes) &rarr; 0 coil &rarr; 0 riks &rarr; 0
  good.<br>
  Every single point — the full registered box plus two probes ~1&deg; from the
  circular anchor — is non-coilable. A ~1&deg; phase perturbation switches the first
  buckling mode away from coiling entirely.<br>
  cleared: none &middot; novel: no — same mechanism as D10, testing coverage, not a
  new idea.
- **Verdict:** POWERED &middot; REFUTED &middot; elliptical/phase-offset ring
  symmetry-breaking<br>
  Full-coverage, direct observation (not surrogate-dependent) that the mechanism
  fails everywhere in the registered box. This is the systematic re-test D10's own
  Verdict said was needed before a closed non-existence call could be licensed —
  it's now licensed.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-2 px-4">
  <div class="text-sm opacity-70 text-center">No video or chart (rule 2c-VIS
  exception): every one of 32 points failed Stage-1 coilability — no Stage-2 data
  exists to chart, and no archived ODB for this specific 2026-07-18 campaign was
  found on scratch or in this run's own delegation logs to render (ephemeral sandbox
  cleanup, not a fabrication — same situation as D1's own slide).</div>
</div>

<!--
**Input space:** same 2D box as D10's own base slide (ellipse_aspect_ratio,
phase_offset) — no new parameter, a coverage re-test.

**Seed:** BARREN — full-coverage sweep, not a thin sample; no untried perturbation of
this idea remains distinct from D10's own already-BARREN Seed.

**Timeline:** D006 of run `20260718T031519`, H1.

**Infra:** no code changed — same oracle path as D10's own base campaign.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T031519</div>

# D19 &middot; <u>In-plane serpentine/meander longeron centerline</u>

::left::

<div class="text-sm leading-snug">

- **What:** Perturbed each longeron's centerline into a periodic,
  small-amplitude in-plane serpentine (meander) wave instead of a straight
  line, aiming to distribute bending curvature along the member's length
  rather than concentrate it at one region.
- **Origin:** common-sense mechanistic hypothesis (a curvature-distribution
  argument), not drawn from an outside literature source.
- **Stats:** n=17 &rarr; 17 coil &rarr; 8 riks &rarr; 3 good (5.89&times; Bessa, pre-contact
  eigenvalue metric — see notes)
  p50/p90/p100 — &sigma;_crit: .769/.774/.783 · mcs: 1.000/1.032/1.067 · mls: .0220/.0224/.0226
  cleared: 8 of 8 decided &ge; 2&times; Bessa (0.2244) &middot; novel: no — clears only because
  it IS the baseline (&Delta;&sigma;&lt;0.2%); the meander itself adds nothing
  best good: amplitude_rel=.0047 n_periods=3 &rarr; &sigma;=.7694 mcs=1.02 mls=.0198
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  Not a contradiction with the "3 good" above:
  those points clear Bessa because they ARE essentially the unperturbed
  run17_rectangle host (&sigma;=.7694 vs baseline's own .7704, &lt;0.2% apart) — the
  meander perturbation contributes nothing on top of it, and among the 8
  trust-gated points, local strain correlates *positively* with both amplitude
  (+0.42) and n_periods (+0.53), the opposite of the hypothesized
  strain-distributing benefit. Recorded inconclusive only because that
  trustworthy sample is thin (8 of 17), but the direction is unambiguous.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D19_meander_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D19_meander_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** amplitude_rel&isin;(0,.02] — meander amplitude relative to the mast diameter.
n_periods&isin;[1,6] — number of wave periods along the longeron. Fixed: host geometry =
run17_rectangle (a=.009213, b=.033238, ratio_pitch=.681277, ratio_top_diameter=.04444).

**Seed:** BARREN — meandering raises local strain rather than distributing it away in both
amplitude and period count, the opposite of the hypothesized direction; the sample is thin
(8/17) but the direction is unambiguous, leaving no reason to expect a properly-powered
re-test would reverse it.

**Timeline:** D007: 17-point existence search; H2's headline correlation figures
corrected by a third critic pass -- earlier-cited correlations (+0.522/+0.593) had
wrongly included D003's unledgered pre-registration regression check (an amplitude=0
"control" point never re-solved through get_evaluator()); recomputed using ONLY
genuine ledgered D007 rows, trust-gated (converged==True AND
stabilization_energy_ratio<0.05, n=8 of 17 -- 9 points never produced a trustworthy
read at all): corr(amplitude, mls)=+0.419, corr(n_periods, mls)=+0.530, both clearly
positive (unfavorable direction). Run `20260724T012622` H4: later
hierarchical/fractal-order refinement of this idea, also falsified -- not in this
batch's scope, noted here for continuity only.

**Infra:** ODB: data/idea_odbs/20260718T031519_H2_meander_serpentine/SUPERCOMPRESSIBLE_RIKS.odb,
sourced from presentation/resim/meander/riks_545d6f9df95a45a195e0991a7c74a888. Rendered
cleanly through the full native pipeline; the meander perturbation is subtle at this
(small, per-hypothesis) amplitude but visible along each longeron's length.

**Chart rebuilt with `bo/mini_chart.py` (2026-09-01)** — real data confirms this IS the
cited best-good design (amplitude_rel=.0047, n_periods=3 matches sim_info.pkl exactly).
Note: &sigma;_crit=.7694 kPa above is the Stage-1 eigenvalue (this run predates the
2026-08-06 contact oracle); the real Stage-2 nonlinear force reading from this same ODB's
own U/RF history is &sigma;_peak=0.6055 kPa at mcs=1.017 — lower, as expected, but the
"clears only because it's the baseline" conclusion is unaffected either way (baseline's
own &sigma;_crit=.7704 is likewise an eigenvalue reading from the same era).
-->

---
class: summary-slide
---

# Run `20260717T192331` — summary

<div class="text-sm leading-snug">

The rectangle-anchor value reconfirms bit-identically and the Kresling ceiling holds, while this run's new "waisted" longeron idea gets a promising point that a later slenderness-formula fix invalidates.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Rectangle search extended beyond the known corner | ✅ | reconfirms 0.7704 kPa bit-identically | D6 |
| H2 | Extend Kresling ψ ceiling beyond 30° | ❌ | no design in [0,60°] beat the 0.711 kPa anchor | D17 |
| H3 | Smoothly radially-tapered ("waisted") longeron | ❔ | new idea, own slide below | D18 |
| H4 | Local refinement near the 0.877 kPa waisted point | ❔ | point later invalid under corrected slenderness formula | D18 |
 &nbsp;&middot;&nbsp; **Cost: $24.95**
</div>

<!--
Per-hypothesis detail:

- H1: does the rectangle family, explored beyond the previously-confirmed corner,
  contain a slenderness-valid design at sigma_cr,nd>=0.3918 kPa? D004: pre-registered
  >=20-eval extension campaign (30 real evals: 13-pt DoE + 4 CEI-BO rounds, widened
  box), slenderness>=10 hard-constrained. Best feasible sigma_cr,nd=0.770352 kPa --
  bit-identically reconfirms the H1 (run 20260717T014507) result, all 4 criteria met.
- H2: does extending the Kresling psi ceiling beyond 30deg improve on the 0.7110618 kPa
  anchor? D003: 47 real evals (1 stabilized anchor re-run + fixed-geometry psi-sweep +
  26-pt global LHS/EI-lite BO + 16-pt local trust-region refinement around the anchor,
  slenderness>=10 pre-screened, meeting the >=30-eval budget). Best feasible remains the
  psi=30deg anchor itself (0.710977 kPa, within cross-run noise of 0.7110618 kPa) -- no
  design anywhere in [0,60deg] beat it, and the trend did not show a rising tail.
- H3: see idea slide below.
- H4: is the 0.877050 kPa point found serendipitously in D006 (this run) near a local
  ceiling, or the base of a still-climbing trend? Moot: this point was found (this
  run's own ledger audit) to FAIL criterion 4 under the corrected slenderness formula
  (true slenderness 8.351, not the self-reported 33.724). D008's 23-eval local
  refinement was ALSO built on the same wrong (waist-based) slenderness pre-screen, so
  its results inherit the same invalidity.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260717T192331</div>

# D18 &middot; Smoothly radially-tapered ("waisted") longeron

::left::

<div class="text-sm leading-snug">

- **What:** Tapered a longeron's radial thickness along its arc-length —
  thick at both ring ends, waisted at mid-span — a fixed-volume
  optimal-column shape, not a uniform section.
- **Origin:** classical Lagrange-Keller / Tadjbakhsh-Keller optimal-column
  result, adapted to this study's longeron geometry.
- **Stats:** n=29 &rarr; 29 coil &rarr; 29 riks &rarr; 1 good (0.57&times; Bessa, current metric)
  p50/p90/p100 — &sigma;_crit: .756/3.04/3.58 · mcs: .677/1.058/1.072 · mls: .0192/.0277/.0441
  cleared: 26 of 29 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes — 26 distinct
  waist_ratio/ratio_b combinations, not repeats of one baseline
  best good: a_end=.0049 waist=.414 b=.0419 pitch=.870 top_d=.0385 &rarr; &sigma;=.0643 mcs=.95 mls=.013
- **Verdict:** INCONCLUSIVE · UNTESTABLE<br>
  The mis-specified (waist-based) constraint
  never searched the real feasible region; the headline fails corrected.


</div>

::right::

<div class="flex flex-col gap-1" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D18_waisted_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 265px">
    <img src="/gifs/D18_waisted_landscape.gif" class="rounded shadow-lg" style="max-height: 265px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">This point reaches 6&times; Bessa but fails the
  corrected slenderness gate (8.35&lt;10) — NOT the best-good design (0.57&times;) in Stats.
  Waist barely visible here (ratio=.98); best-good's real .41 taper has no archived render.</div>
</div>

<!--
**Input space:** a_end&isin;[.004,.02] — end (ring) cross-section radius. waist&isin;[.30,.98] —
mid-span radius as a fraction of a_end. b&isin;[.012,.06] — secondary semi-axis.
ratio_pitch&isin;[.4769,.8857], ratio_top_diameter&isin;[.0311,.0578] — usual per-storey
pitch/taper meaning, narrowed for this campaign. Fixed: circular=4 (cross-section-family
switch), n_storeys=1, twist_angle=0.

**Seed:** FERTILE — the waist-based constraint that defined this campaign's search box was
mis-specified, so the real feasible region was never actually searched; a corrected re-run
(real slenderness formula, not the invalidated one) is untried.

**Deferred:** FINAL SETTLEMENT (quoted from the run's own hypothesis log): "Settling
here permanently (no further reversal), accepting the validator's final point: D006's
CEI-BO search was guided by constraints built on the (my own mis-specified)
waist-based slenderness, so it never searched FOR feasibility under the corrected,
problem-statement-faithful ratio_b-based slenderness -- a search not aimed at the real
constraint is not an adequate test of it, regardless of what a post-hoc recompute of
the same data shows."

**Timeline:** Stats-migration note (2026-08-04): initial 0.877 kPa headline proved
invalid under the corrected slenderness formula (8.35, below the &ge;10 floor) — the
study's slenderness criterion is defined on the tangential half-width ratio_b
(ratio_pitch/(2*ratio_b)), which a purely-radial taper does not touch, so the taper
family's self-reported "slenderness" (computed off the tapered/waisted radial
dimension, 33.7 for the 0.877 kPa point) was the wrong quantity entirely. Direct
recomputation from D006+D008 (the only two delegations actually testing this
family — D003/D004/D007 in this same run belong to unrelated hypotheses) finds
exactly 1 point clearing every corrected criterion, not 2 as an earlier draft of this
slide stated — the second point implied by "2/30" could not be located; reported as
G=1, verified, rather than repeating an unconfirmed number. This is hypothesis H3 of
run `20260717T192331`. The mis-specification bug was caught by a later ledger audit
(this run's own H4), and independently re-confirmed in run `20260718T132852`'s H2.

**Infra:** ODB: data/idea_odbs/20260717T192331_H3_waisted_tapered/SUPERCOMPRESSIBLE_RIKS.odb,
sourced from presentation/resim/waisted/riks_b25001089f5c4baa82473915d82f8736 -- a
typical member of this family's search per the format contract's no-winner
convention, not necessarily the single best (and specifically NOT the
later-invalidated 0.877 kPa point). Rendered cleanly through the full native
pipeline; the radial taper toward each longeron's mid-span waist is visible even in
the undeformed frame.
-->

---
class: summary-slide
---

# Run `20260717T014507` — summary

<div class="text-sm leading-snug">

This run finds the 0.7704 kPa rectangle-anchor design that becomes the study's canonical baseline, while a diagonal cable-stay bracing attempt finds nothing feasible beyond the unbraced control.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Existence ≥0.3918 kPa in the rectangle family | ✅ | 0.7704 kPa found — becomes the study's canonical anchor | D6 |
| H2 | Pretensioned diagonal cable-stay bracing | ❔ | 0/45 feasible — only the no-brace control was feasible | D15 |
| H3 | Kresling/TCO bar-hinge longeron | ❔ | new idea, own slide below | D17 |
 &nbsp;&middot;&nbsp; **Cost: $22.06**
</div>

<!--
Per-hypothesis detail:

- H1: within the known slenderness-valid rectangle family (best confirmed point 0.3648
  kPa), is there a design at sigma_cr,nd>=0.3918 kPa (3x Bessa point)? D005's 71-eval
  CEI-BO campaign (seeded at the known optimum + Sobol fill, hard-constrained to
  slenderness>=10) found ratio_a=0.009213, ratio_b=0.033238, ratio_pitch=0.681277,
  ratio_top_diameter=0.044440 -> sigma_cr,nd=0.770352 kPa (1.97x target, 2.11x prior
  baseline), coilable=1, mcs=1.0, mls=0.0199, slenderness=10.25. This becomes the
  study's canonical "run17_rectangle" anchor for the rest of the study.
- H2: adding pretensioned diagonal bracing (cable-stayed-column precedent, Gurfinkel &
  Krishnan 2017) to the best-known cross-section. D006: pre-registered >=40-eval joint
  CEI-BO campaign (45 real evals) over brace stiffness/pretension/attachment-height
  jointly with cross-section dims, seeded on both the historical control and the new
  0.770352 kPa best. Result: 0/45 braced points feasible -- only the
  ratio_brace_area=0 control (reproducing 0.364826 kPa) was feasible. A genuine,
  budgeted null result, not a decisive disproof (7D search, thin coverage).
- H3: see idea slide below.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260717T014507</div>

# D17 &middot; <u>Kresling/TCO two-segment bar-hinge longeron</u>

::left::

<div class="text-sm leading-snug">

- **What:** Replaced each longeron with two straight beam segments meeting
  at an interior hinge node, offset circumferentially by angle
  `psi_kresling`, coupling axial compression to rigid-body strut
  re-orientation instead of relying purely on elastic bending.
- **Origin:** the Kresling origami folding pattern (a well-known
  bar-hinge/triangulated-cylinder mechanism), adapted here to this study's
  beam-longeron model — a real, specific geometric precedent, not a
  fabricated citation.
- **Stats:** n=45 &rarr; 37 coil &rarr; 37 riks &rarr; 8 good (5.44&times; Bessa)
  p50/p90/p100 — &sigma;_crit: .574/1.28/2.52 · mcs: 1.00/1.00/1.00 · mls: .0217/.0294/.0483
  cleared: 31 of 37 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes — the cleared set
  spans 9 distinct nonzero psi values, not duplicates of the degenerate psi=0 case
  best good: a=.0120 b=.0151 pitch=.618 top_d=.0351 psi=.5236 +1 more &rarr; &sigma;=.7111 mcs=1.00 mls=.0196
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  A genuinely feasible design existed and once
  cleared all four original criteria, but was later rejected on a separate
  ring-passthrough criterion (see notes); not a validated winner.

</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 165px">
    <img src="/gifs/D17_kresling_mini.png" style="max-height: 165px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 285px">
    <img src="/gifs/D17_kresling_native.gif" class="rounded shadow-lg" style="max-height: 285px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** a&isin;[.006,.014], b&isin;[.008,.025] — cross-section semi-axes.
ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.6] — usual per-storey pitch/taper
meaning. psi_kresling&isin;[0,.6] rad — hinge offset angle (0 = hinge off). ratio_hinge_height
&isin;[0,1] — where along the longeron's length the hinge node sits. Fixed: circular=2
(cross-section-family switch), n_storeys=1, twist_angle=0.

**Seed:** BARREN — later resolved decisively: the bar-hinge kink is a real reentrant-corner
stress singularity (confirmed via mesh refinement, fillets, and an independent referee — see
D17-3), not a numerical artifact and not floor-passthrough. No perturbation
within this geometric-kink realization survives; a genuinely different hinge (an actual
pin/flexure joint) would be a different idea.

**Deferred:** The run's own gate critic FINAL SETTLEMENT (quoted): "the honest path...
is to settle H3 at its last validator-endorsed INCONCLUSIVE and stop re-litigating" --
reverting a subsequent (disputed) FALSIFIED flip back to the last validator-endorsed
status, on the same D007 evidence, and stopping there. REJECTION, reported per the
manifest/PROVENANCE.txt: this exact feasible design (psi=30deg, sigma=0.711 kPa) was
later REJECTED in bo/confirmed_anchors.json (`_rejected.kresling_snap`) for failing
criterion 5 (ring-passthrough) -- the bar-hinge kink lets the longeron's mid-span node
pass through the ring's 0-D plane undetected during coiling, a failure mode this
study's beam-only feasibility criteria (coilable/mcs/mls/slenderness) do not check
for. So this idea passed every criterion it was originally tested against, then
failed a criterion added later in the study -- an honest, still-open example of
criteria evolving mid-study, not a contradiction.

**Timeline:** D007: 45 real, ledgered evals -- 1 stabilized anchor re-run +
fixed-geometry psi-sweep + 26-pt global LHS/EI-lite BO + 16-pt local trust-region
refinement, all slenderness>=10 pre-screened, meeting the registered >=30-eval budget
(this is hypothesis H3 of run `20260717T014507`). Best feasible design:
psi_kresling=30deg, sigma_cr,nd=0.7110618 kPa.

**Infra:** ODB: data/idea_odbs/20260717T014507_H3_kresling_bar_hinge/SUPERCOMPRESSIBLE_RIKS.odb,
sourced from presentation/resim/kresling_run17/riks_93eadc4e3f4f4c5fa20d3e80954e6b60.
Rendered cleanly through the full native pipeline; the bar-hinge kink partway up each
longeron is visible in the animation.
-->

---
class: summary-slide
---

# Run `20260715T191329` — summary

<div class="text-sm leading-snug">

No new idea this run — a rectangle-family ceiling check and a 5-family cross-cutting scan both come back bounded negative, neither a clean proof nor a way forward.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Rectangle family ceiling vs the 3× Bessa target | ❔ | high-σ points all fail mls (~0.032, well over the 0.02 limit) | D6 |
| H2 | Any novel family decouples buckling stiffness from radial strain? | ❔ | bounded negative across 5 families — existence claim, can't be proven absent | — |
 &nbsp;&middot;&nbsp; **Cost: $40.60**
</div>

<!--
Per-hypothesis detail:

- H1: within the verified anisotropic-rectangular family, enforcing all four
  feasibility criteria (incl. slenderness>=10, fully-converged Riks read), is there a
  feasible design at sigma_cr,nd>=0.3956 kPa? D002 (48-eval 4D CEI-BO): no feasible
  design found; its one clean converged high-sigma point (sigma=0.406, mcs=1.0) fails
  mls=0.032. D005 (clean converged 1D ratio_a sweep, mcs=1.0 throughout, no confound):
  sigma crosses the 0.3956 target at ratio_a=0.0146, but mls crosses 0.02 at
  ratio_a=0.0100 -- every design at or above the target sigma already has mls~0.032,
  well over the limit. Strong evidence of an absence, but not a proof; corrected to
  INCONCLUSIVE per validator/Charter guidance on budgeted absence claims.
- H2: a structurally-novel family that decouples buckling stiffness from radial
  bending strain (thin-walled/shaped open cross-section, or a topological change).
  Tested across FIVE novel families on the first trustworthy converged oracle: (1)
  serpentine wavy path (D004) -- converged Stage-1 sigma DROPS with amplitude
  (0.365->0.344), Stage-2 supercompression numerically intractable (early snap at
  11.7%, stab_ratio=1.1); (2) auxiliary bracing (D006) -- sigma bit-identical to
  baseline even at 10x strut area (coiling eigenmode insensitive to inter-longeron
  stiffness); plus three further families summarized in D008's 36-eval combined
  screen (2/36 coilable, coilable_rate 0.0556 overall vs 0.375 restricted to
  1-storey configurations, best coilable sigma=0.406 but mcs=0.01375 -- nowhere near
  feasible). An existence claim across five tried-and-failed families cannot be
  proven absent by a bounded negative, so INCONCLUSIVE rather than FALSIFIED, per the
  Charter's existence-claim handling.
-->

---
class: summary-slide
---

# Run `20260715T002538` — summary

<div class="text-sm leading-snug">

Four hypotheses converge on the same conclusion — a σ-vs-feasibility barrier at the 2% local-strain limit holds across box cross-sections, a helical path, and a 2-storey escape attempt alike.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Closed thin-walled box cross-section at slenderness≥10 | ❔ | mechanism confirmed (high-J → high σ) but coilability fails | D12 |
| H2 | Helical (chiral) longeron path | ❌ | new idea, own slide below | D16 |
| H3 | Feasible σ bound by the 2% local-strain limit | ❌ | knife-edge bifurcation, not a feasible window | — |
| H4 | 2-storey escape from the σ↔feasibility barrier | ❔ | barrier holds — same conflict pattern as single-storey | D4 |
 &nbsp;&middot;&nbsp; **Cost: $19.54**
</div>

<!--
Per-hypothesis detail:

- H1: among realizable closed thin-walled "box" cross-sections (maximizing torsional
  constant J), tested for a slenderness>=10 feasible design. D005: 48-eval box screen,
  27/48 coilable but only 1/48 feasible (sigma=0.000733 kPa, a degenerate thin-section
  point) -- far below both the ~0.06 kPa rectangular ceiling and the 2.3376 kPa floor.
  The MECHANISM is confirmed (high-J box designs do reach high sigma, best coilable
  sigma=5.68 kPa, above the floor, exactly as torsion theory predicts) but those
  high-sigma designs fail criterion 2 badly (best-coilable mcs=0.0625, far under 0.90):
  the same stiffness that raises buckling load suppresses full coiling compression.
- H2: see idea slide below.
- H3: at slenderness>=10, tested whether feasible sigma is bound by the 2% local-strain
  limit rather than coilability, within the straight rectangular family. D008: 29-eval
  sweep (18-pt focused screen + 11-pt ratio_a boundary trace + 1 confirm), 0/29
  feasible. Registered prediction (a feasible window at sigma~[0.3,1.5] kPa near the
  mls~0.02 boundary) was contradicted: the transition is a KNIFE-EDGE bifurcation --
  at fixed section, mcs jumps 0.53->1.0 across a single ratio_a step 0.0099->0.010, and
  mls crosses 0.02 in that SAME step (0.0166->0.0215) -- full compression and the local
  strain limit are breached in the same infinitesimal step, leaving no feasible
  straddle point at all.
- H4: tested whether a 2-storey mast (n_storeys=2) at slenderness>=10 escapes the
  sigma<->feasibility barrier by distributing coiling curvature across two storeys.
  D009: 16-eval bounded probe, 0/16 feasible. The highest-sigma coilable 2-storey
  design (sigma=2.0125 kPa, above the single-storey ~0.06 kPa ceiling and near the
  2.3376 kPa floor) fails BOTH remaining criteria at once (mcs=0.866<0.90 AND
  mls=0.047>0.02) -- the same conflict pattern as the single-storey family, no
  decoupling achieved.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260715T002538</div>

# D16 &middot; Helical (chiral) longeron path

::left::

<div class="text-sm leading-snug">

- **What:** Bent each longeron into a helix winding around the mast axis
  (a `helix_wrap` parameter), rather than a straight line, hypothesizing a
  spring-like geometry predisposed to reversible coiling.
- **Origin:** common-sense mechanistic hypothesis, explicitly distinguished
  from pre-twist (which rotates the cross-section) and radial bowing
  (which is planar) — both tried and falsified in earlier runs. Not drawn
  from an outside literature source.
- **Stats:** n=28 &rarr; 8 coil &rarr; 8 riks &rarr; 1 good (0.051&times; Bessa, current metric)
  p50/p90/p100 — &sigma;_crit: 1.09/6.04/14.76 · mcs: .881/1.00/1.00 · mls: .019/.118/.191
  cleared: 7 of 8 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes — 5 of the 7 carry a
  genuinely nonzero wrap, not duplicates of the degenerate wrap=0 case; mls (local strain) is the gate
  best good: a=.003 b=.008 pitch=.30 top_d=0 wrap=0 (degenerate) &rarr; &sigma;=.0057 mcs=1.00 mls=.0066
- **Verdict:** FALSIFIED · DEAD-END<br>
  Helical wrap raises critical buckling stress
  but destroys local-strain feasibility even faster, the opposite of the
  hypothesized reversible-coiling benefit.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D16_helical_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D16_helical_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center px-2">The wrap=0.6 comparison design (5.25&times;
  Bessa, windowed to the 2% cap) — NOT the best-good degenerate wrap=0 design (0.044&times;),
  which has no archived solve.</div>
</div>

<!--
**Input space:** a&isin;[.003,.03], b&isin;[.008,.06] — cross-section semi-axes.
ratio_pitch&isin;[.30,1.5], ratio_top_diameter&isin;[0,.6] — usual per-storey pitch/taper
meaning. helix_wrap&isin;[0,1.5708] rad — turns wound into the longeron before compression.
Fixed: n_storeys=1, twist_angle=0, ratio_shear_modulus=.3677.

**Seed:** BARREN — wrap raises buckling stress but destroys local-strain feasibility even
faster than it helps, the opposite of the hypothesized benefit; the best good design is
degenerate (wrap=0), meaning the mechanism actively hurts at any nonzero setting tested.

**Timeline:** D007: 28-eval existence search plus an independent matched-pair causal
sweep at wrap=0.0/0.6 (hypothesis H2 of run `20260715T002538`). The registered
falsification criterion was specifically the MECHANISM branch: "if no feasible
helical design even exceeds the ~0.06 kPa rectangular ceiling, the helical mechanism
confers no advantage." Only 1/28 designs was feasible at all, and it was the
degenerate wrap=0 (i.e. straight) case -- no genuinely-helical design was feasible, so
none exceeded the ceiling. The matched-pair sweep independently confirms the causal
direction: at wrap=0.6, sigma_cr,nd=2.306 kPa (well above ceiling) but
max_local_strain=0.191 (19.1%, vs the wrap=0 control's max_compressive_strain=0.976,
max_local_strain=0.0209 at the same cross-section) -- the helical mechanism trades a
large stiffness gain for a catastrophic strain penalty.
Deck audit item 2 (2026-08-26): this design was previously held/skipped for porting
because mini_plot.py flags reversed=True and its unwindowed tail reaches an unphysical
~273x Bessa. Investigated properly rather than left held: the mast reverses at frame
93 (mcs~96%) and the reaction-force reading explodes to a frozen ~273x-Bessa plateau
for 4900+ frames after that (ALLSD=0 throughout, ALLSE flat -- a genuine
equilibrium-path degeneracy, not stabilization trickery, but not real load-bearing
physics either: displacement stays essentially frozen while force keeps climbing).
None of this matters for the citable number: the 2% strain-limit window closes at
frame 16 (mcs=38.7%, sigma=0.5894 kPa peak, 5.25x Bessa), long before the reversal at
frame 93 or the force explosion after frame 40. reversed=True is true of the full
history and irrelevant to the windowed metric here -- unlike D30, where the reversal
happened INSIDE the citable range and needed careful handling. Cross-verified:
sigma_cr,nd=2.306 kPa reproduces exactly from the Stage-1 eigenvalue (loads[0]=54.339
N x to_kpa); max_local_strain=0.19521886 (scalar field) matches the cited 19.1% to
rounding.

**Infra:** ODB: data/idea_odbs/20260715T002538_H2_helical_longeron_path/SUPERCOMPRESSIBLE_RIKS.odb,
sourced from presentation/resim/helical/riks_helical_76b431f83394417ea38e227d26171b56
-- this is the wrap=0.6 matched-pair comparison point, not the "best good" degenerate
wrap=0 design (which has no ODB in this archive). Landscape render (28 frames, mcs
0-95%) confirms clean, no clipping; the mini-plot uses --windowed-only (the
post-reversal explosion is a numerical artifact, not real-but-noncitable physics, so
showing it in muted grey the way other slides' full curves are shown would mislead
rather than inform).
-->

---
class: summary-slide
---

# Run `20260714T020739` — summary

<div class="text-sm leading-snug">

Both a hard-slenderness rectangle search and a diagonal chiral-bracing lattice stay inconclusive — the former's trend was still climbing when the campaign stopped, and the latter's braced designs uniformly fail strain against an unbraced control.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Hard slenderness≥10 floor on rectangle family vs 2.34 kPa target | ❔ | best feasible 0.058 kPa, trend still rising when campaign stopped | D6 |
| H2 | Diagonal chiral-bracing lattice (see idea slide below) | ❔ | 0/42 feasible; braced 30/30 fail on strain vs 34/46 unbraced control | D15 |
 &nbsp;&middot;&nbsp; **Cost: $26.57** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H1: within the anisotropic-rectangular family, enforcing slenderness=ratio_pitch/
  (2*ratio_b)>=10 as a hard reject-and-resample constraint. D003 ran a 56-eval CEI-BO
  campaign (16-pt slenderness-constrained Sobol DoE + 5 batch-8 CEI rounds); only
  8/56 feasible, best feasible sigma_crit=0.0579 kPa (>1 order of magnitude below the
  2.3376 kPa floor), corroborating an independent earlier run's 0.3644 kPa ceiling.
  Initially marked SUPPORTED, then corrected to INCONCLUSIVE per validator feedback:
  the best-feasible trend was still rising sharply in the final round (0.01635->0.05789,
  a 3.5x jump) with no plateau and only 8/56 feasible points clustered in one corner --
  an inadequate test of an absence claim regardless of the large observed gap.
- H2: see the idea slide below for full detail. Two delegations: D005 (48-eval main
  campaign, 32/48 evals silently corrupted by an abaqus2py hardcoded 60s no_file_timeout
  tripping under heavy concurrent cluster load -- confirmed by comparing against a
  lower-concurrency diagnostic; 24 genuine evaluations left, 0/24 feasible) and D006
  (18-eval clean continuation at lower concurrency, verified genuine via .log markers).
  Combined 42 genuine evals, 0/42 feasible, failure dominated by max_compressive_strain
  (30/42, 71%). A corrected failure-rate comparison (treating Riks non-convergence/NaN
  as a feasibility failure, consistent with the study's own convention elsewhere) gives
  34/46 (73.9%) unbraced vs 30/30 (100%) braced -- the directional signal holds and, if
  anything, strengthens under the correction.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260714T020739</div>

# D15 &middot; Diagonal chiral-bracing lattice

::left::

<div class="text-sm leading-snug">

- **What:** Added a diagonal chiral-bracing lattice of short auxiliary beam
  struts between adjacent longerons, layered on the slenderness-valid
  rectangular family (two verified CEI-BO campaigns; see notes).
- **Origin:** common-sense — an alternative stiff load path to offload
  torsional/bending demand from the longerons (a later refinement drew a
  cable-stayed precedent, Gurfinkel & Krishnan 2017; see notes).
- **Stats:** n=42 &rarr; 30 coil &rarr; 22 riks &rarr; 0 good
  p50/p90/p100 — &sigma;_crit: 19.24/596.53/713.78 · mcs: .00/.06/.77 · mls: .00/.04/.25
  cleared: 22 of 22 decided &ge; 2&times; Bessa (0.2244) &middot; novel: yes, but not meaningful —
  16/22 have mcs=0.0 exactly, consistent with a stiff non-coiling mode, not real headroom
  best good: none (0/42 passed every criterion)
  (braced designs failed max_compressive_strain in 30/30 vs 34/46 for the unbraced control)
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  As an existence claim; directional signal is
  clear — bracing blocks coiling rather than helping it.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/D15_chiral_brace_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Undeformed only — no valid deformed state (see notes).</div>
</div>

<!--
**Input space:** a&isin;[.0025,.20], b&isin;[.0025,.075] — longeron cross-section semi-axes.
ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] — usual per-storey pitch/taper
meaning. z_brace&isin;[.05,.95] — axial position of the bracing lattice along the mast.
ratio_brace_area&isin;[0,3.5e-4] — brace strut cross-section area. brace_prestrain&isin;[0,.01] —
brace pre-tension strain. Fixed: circular=2 (cross-section-family switch), n_longerons=3,
n_storeys=1, twist_angle=0, ratio_shear_modulus=.3677.

**Seed:** BARREN — braced designs failed max_compressive_strain in 30/30 vs 34/46 for the
unbraced control; the directional signal is unambiguous even though the formal existence claim
stays INCONCLUSIVE (thin decided sample) — bracing blocks coiling, it does not help it.

**Deferred:** Stats-migration note (2026-08-04): this campaign predates an explicit
`riks_converged` field — R above counts rows with a real (non-NaN) mcs AND mls value,
a looser bar than a confirmed-converged flag. &sigma;_crit's high p90/p100 (596/714
kPa) almost certainly reflect a non-coiling, stiff buckling mode, not real progress —
mcs stays near 0 for most of these rows. GIF LIMITATION, reported honestly per this
task's instructions rather than skipped or faked: the archived ODB
(data/idea_odbs/20260721T201733_H4_chiral_brace/SUPERCOMPRESSIBLE_RIKS.odb) has a
genuine, ODB-specific rendering blocker. Two of its 2610 LONGERONS-instance nodes
(labels 562, 1369 -- both endpoints of two T3D2 brace/truss elements, 554-555 and
1363-1364) carry an Abaqus invalid/sentinel displacement value (magnitude 1e23-1e36)
in the U field output from increment 1 onward (frame 0 is clean; every later frame
checked -- 1,2,3,5,10,29,50,97 -- shows the identical two-node fault, so it is not a
transient blip). Excluding those two elements from the display group (a native,
non-fabricating fix -- same technique already used elsewhere in this pipeline to hide
the non-structural ANALYTICAL_SURF instance) stopped the crash risk but did NOT
restore the visible geometry: every frame after 0 still rendered fully blank
(confirmed with contour off, with per-frame camera re-assertion, and with
node-averaging disabled -- none fixed it), and rendering the same frame in plain
wireframe (renderBeamProfiles=OFF) segfaults Abaqus/Viewer outright (signal 11) for
this specific ODB. This appears to be a Mesa software-rendering depth/precision
failure triggered by those two divergent nodes' astronomical coordinates propagating
into the viewport's internal state even when the offending elements are excluded
from display -- not something fixable within this pass without deeper
Abaqus-internals investigation. Per this task's explicit instructions ("if you hit a
genuine blocker... report that specifically rather than skip it silently"), the
image shown is a genuine native Abaqus/CAE render of this same ODB's undeformed
(frame 0) configuration only -- a real, unfabricated render, just not an animation. A
full animated re-render of this idea remains open work.

**Timeline:** D005+D006: hypothesis H2 of run `20260714T020739`. It folds together
every later bracing variant tried in this study (cable-stayed, chiral-ring,
aperiodic/golden-ratio, multi-turn helical-coil) -- all are one "auxiliary bracing"
mechanism family per the manifest's boundary rule. That later run's H4 (sigma=1.2457
kPa) was a more elaborate joint host+brace optimization that never passed full
apples-to-apples (its own H6 found the brace ligament itself over-strains) -- so the
mechanism's overall arc across the study stayed negative/inconclusive despite that
one nominally-positive number.

**Infra:** ODB provenance: the permanent archive at
data/idea_odbs/20260721T201733_H4_chiral_brace/ (folder named for a later run because
that is where the best-known illustrative bracing point's ODB was recovered from;
PROVENANCE.txt is explicit that this is "an illustrative bracing point, not
bit-identical to the H4 optimum" -- the exact 8D optimum's parameters were never
recoverable from that later run's own text). Two small general-purpose fixes were
made to the shared presentation/render/render_odb.py during this investigation
(kept, since they are principled and harmless for every other ODB in this deck): (1)
`_current_positions` now falls back to undeformed-coordinates + U when an ODB has no
COORD field output at all (needed for this same bracing ODB's ring-schematic
overlay, which DOES render correctly in every frame); (2) a
`_divergent_element_labels` helper excludes from display any element touching a node
with a >1e30-magnitude field value in any rendered frame, general robustness for any
future ODB with a similar localized divergence, not a chiral-brace-specific hack.
-->

---
class: summary-slide
---

# Run `20260712T192155` — summary

<div class="text-sm leading-snug">

This run's H1 counterexample (2.5656 kPa) is this whole batch's best confirmed valid design — a refinement of the run17-rectangle-anchor idea, not a new mechanism, so it earns a bullet here rather than its own slide.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Fresh joint 4D search over the rectangle-anchor family (see idea slide below) | ❌ | counterexample found: σ_cr,nd=2.5656 kPa, all 3 criteria met — 2.2× prior best, >7× original anchor | D6 |
| H2 | 2-storey mast, independent tangential dim per storey (see idea slide below) | ❔ | 0 confirmed-feasible, but persistent Riks NaN gap — not a clean negative | D4 |

 &nbsp;&middot;&nbsp; **Cost: $47.10** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H1: an eventful verdict history — D003's first attempt (63 evals) was confounded by
  a slenderness gate the strategizer itself had mis-specified along the wrong axis
  (pitch/(2b) instead of pitch/(2a) for this reversed orientation), which excluded the
  known baseline's own neighbourhood entirely (INCONCLUSIVE, Duhem-Quine: the
  contradiction indicts the imposed constraint, not the hypothesis). D005's corrected
  re-test (40 evals, full domain, no slenderness gate) found several designs that
  clear both the sigma floor AND full compression but ALL fail max_local_strain
  (0.030-0.050 vs the 0.02 limit) — initially read as SUPPORTED (the "cannot find a
  counterexample" claim survives). D006-D012's continued local refinement (a
  one-at-a-time search, then a single-axis ratio_a bisection, then a joint local
  re-search) eventually found and repeatedly confirmed (bit-identical across 3
  repeats, D012) a design at ratio_a=0.009338 that DOES clear the floor while meeting
  all three criteria — reversing the verdict to FALSIFIED. Per adversarial review:
  the counterexample-finding methodology evolved from what was originally registered
  (a single ≥60-eval joint campaign) to a more targeted sequential search, but the
  registered PREDICTION itself (no design clears the floor) is unambiguously and
  repeatably contradicted, which is what the charter's FALSIFIED criterion actually
  turns on — methodology evolving mid-investigation is normal iterative science, not
  goalpost-moving on the claim.
- H2: D013 (8 evals) traced D007's earlier null result to a genuine domain confound
  (ratio_pitch lower bound excluded the exact pitch needed to match the new
  single-storey winner's height at 2 equal storeys) — the same class of bug as H1's
  D003 confound. Re-tested near the corrected region: the uniform-storey anchor
  numerically clears the floor (2.566 kPa) but Riks returned NaN for both
  compressive and local strain (could not confirm feasibility, treated conservatively
  as infeasible); 4 asymmetric b-splits all returned real values but collapsed to
  0.65-0.73 max_compressive_strain (a recurring buckling-mode-switch pattern seen
  throughout this study); 3 further ratio_a increases all returned NaN again. Net
  across 48 total evals (D007+D013): zero confirmed-feasible designs, but the NaN gap
  keeps this from being a fully clean negative.
-->
---
class: summary-slide
---

# Run `20260709T024901` — summary

<div class="text-sm leading-snug">

One new family tested and cleanly falsified; the run's real finding is analytical (H3) — the current best design is already strain-capped, not just under-searched.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Open thin-walled L-profile, shear-centre offset (see idea slide below) | ❌ | ~24× below the 1.1688 kPa baseline | D14 |
| H2 | n_longerons variation within rectangle-anchor family (tested later, run `20260721T201733` H7) | ⏳ | proposed, 0 evals this run | — |
| H3 | Rectangle-anchor optimum is bending-strain-limited, not under-searched | ✅ | both Riks criteria already at ceiling at 1.1688 kPa | D6 |

 &nbsp;&middot;&nbsp; **Cost: $33.51** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H2: statement registers that n_longerons might materially change achievable
  sigma_cr,nd per longeron within the winning rectangular family (a different
  question from this study's earlier, cross-section-independent n_longerons=5 test)
  — proposed this run with prior left at its initial value, zero evaluations before
  run close; picked up three runs later (outside this batch's scope).
- H3: D006 re-ran a corrected (ungated) joint 5D search (ratio_a, ratio_b, ratio_pitch,
  ratio_top_diameter, ratio_shear_modulus), 45 oracle evals, seeded at the known
  baseline (reproduced exactly: 1.168791, feasible, slenderness=6.35). Only 3/45
  points (6.7%) feasible even without any slenderness gate. Best feasible:
  σ_cr,nd=1.650585 (41% above baseline, not doubling it), at a materially different
  ratio_shear_modulus (0.423586 vs the 0.3677 held fixed throughout every prior run) —
  a genuine, if modest, new gain from freeing that one dimension. Objective GP
  surrogate CV R²=0.995. Registered prediction ("no design clears 2.3376 kPa; best
  feasible stays modestly above 1.1688, not doubling it") NOT contradicted → SUPPORTED.
-->

---
layout: two-cols-header
class: idea-slide
---

# D14 &middot; Open thin-walled L-profile (shear-centre offset)

::left::

<div class="text-sm leading-snug">

- **What:** An open thin-walled longeron cross-section with an inherent
  shear-centre-to-centroid offset (Abaqus `LProfile`) — a DOF the Bessa
  parametrization fixes to zero, never accessed by any prior family.
- **Origin:** parametric-space extension, tempered by a literature review
  (Zahn & Iwankiw 1989 flexural-torsional buckling theory) predicting
  AGAINST the mechanism beforehand (see notes).
- **Stats:** n=45 → 29 coil → 6 riks → 0 good
  p50/p90/p100 — σ_crit: .022/.073/.085 · mcs: .434/.564/.579 · mls: .010/.018/.018
  cleared: 0 of 6 decided ≥ 2× Bessa (0.2244) · novel: untested — σ itself never clears,
  well below the theoretical prior's expected ceiling for this cross-section
  best good: none (0/45 passed every criterion)
- **Verdict:** FALSIFIED · DEAD-END<br>
  Matches the theoretical prior; a GP surrogate fit
  on this data is genuinely predictive (well above a chance baseline, CV
  R²=0.881), confirming the flat, feature-less landscape is real and not a
  search-coverage artifact; not competitive with the 2.3376 kPa floor.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D14_offset_shear_lprofile_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D14_offset_shear_lprofile_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">Chart's final-frame spike (7.28&times; Bessa) is a
  1-frame termination artifact, not real capacity — see notes; does not change the verdict.</div>
</div>

<!--
**Input space:** a&isin;[.002,.02], b&isin;[.01,.06] — outer L-profile leg dimensions.
t_frac_a, t_frac_b&isin;[.02,.5] — wall thickness as a fraction of each leg's own outer
dimension. ratio_pitch&isin;[.30,1.5], ratio_top_diameter&isin;[0,.3] — usual per-storey
pitch/taper meaning (narrowed for this campaign). Fixed: n_longerons=3,
ratio_shear_modulus=.3677.

**Seed:** BARREN — matches the theoretical prior (Zahn & Iwankiw 1989) that predicted against
this mechanism beforehand, and a GP surrogate confirms the flat landscape is real, not a
search-coverage gap; the shear-centre offset genuinely does not help.

**Deferred:** Stats-migration note (2026-08-04): only 6 of 29 coilable designs
produced a real Riks reading (~21% Riks yield) — most coilable attempts in this
family failed to converge at all, not just fail feasibility. Verdict-history nuance:
the strategizer's first pass called this INCONCLUSIVE (deprioritizing given the
slenderness gate's potential to have excluded a narrow feasible region), but the
validator corrected this: the registered falsification criterion explicitly
specified the slenderness≥10 gate as part of the claim being tested, so the test as
run WAS exactly the registered one, and the result (zero feasible, adequate
coverage, above-chance surrogate) mandates FALSIFIED.

**Timeline:** D002: literature review. Quote: "the lowest root is always less than
either of the Euler flexural buckling stresses... and the pure torsional buckling
stress about the shear center" — the coupling this hypothesis needed is a bug in
classical FT buckling theory, not a feature, and open sections also have inherently
low torsional constant J relative to closed/solid sections, trading away the
dominant sigma_crit lever this study has repeatedly found (per Bessa's own
sensitivity analysis) to gain a coupling term theory says can only hurt. D005:
search (this is H1 of run `20260709T024901`).

**Infra:** ODB: data/idea_odbs/20260709T024901_H1_offset_shear_Lprofile/ (source:
SCRATCH path /oscar/scratch/eaguerov/supercompressible_oracle/
riks_a581638a45ad4424b5da6a66baa0cf06). GIF: native Abaqus/CAE Viewer export,
standard pipeline, no ODB-specific gotchas. The open L-shaped cross-section's
asymmetric profile is directly visible in the rendered beam geometry; the partial,
incomplete coiling shown (max mcs=0.579 observed across the family) is a faithful,
typical (not cherry-picked) result.

**Chart rebuilt with `bo/mini_chart.py` (2026-09-01)** — was a stale, pre-2026-08-31
chart with no mls color coding. Real unwindowed data: the last two raw frames read
mcs=0.5158..0.5790 with sigma smoothly DECLINING 0.48x&rarr;0.44x Bessa (frames 95-103),
then frame 104 reports sigma=0.8167 kPa (7.28x Bessa) AT THE SAME mcs as frame 103
(0.5790, zero displacement progress between the two) — the signature of a solve that
terminated mid-increment and recorded a spurious final force reading, not a genuine
capacity jump (same class of 1-frame artifact independently established for D24/D24-2,
D16's unwindowed tail, D18's chart). Not re-solved at finer resolution: this family's
verdict does not depend on it (falsified regardless, on 6/6 designs and a predictive
GP surrogate, matching a pre-registered literature prior) and spending an Abaqus
license-hour to sharpen the tail of an already-dead-end family is not a good trade
against this study's real open questions — flagged here rather than silently charted.
-->

---
class: summary-slide
---

# Run `20260708T021335` — summary

<div class="text-sm leading-snug">

Three new cross-section families tried this run, all dead ends — but the run's one refinement (H4) delivers the biggest single headline jump of this batch, more than tripling the established anchor's performance.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Flexure-hinge (piecewise stiff/thin) longeron (see idea slide below) | ❔ | strong negative signal, but underpowered surrogates | D13 |
| H2 | BoxProfile hollow-tube cross-section (see idea slide below) | ❔ | underperforms baseline | D12 |
| H3 | Heterogeneous (2 stiff + 1 compliant) longerons (see idea slide below) | ❔ | no improvement found | D11 |
| H4 | Increase only the tangential dimension of the rectangle-anchor family | ✅ | new best-found design, 1.1688 kPa — 3.2× the 0.3644 kPa anchor | D6 |

 &nbsp;&middot;&nbsp; **Cost: $97.39** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H4: D013's ledger — best feasible design is NOT the pure ratio_b-sweep optimum
  (1.15937 kPa) but a further +20% "stretch test" on ratio_top_diameter
  (1.16879 kPa, ratio_top_diameter=0.045534), coilable=1, max_compressive_strain=
  0.99974, max_local_strain=0.019593. Per an adversarial-audit correction: this is
  the BEST FOUND design in the family, not a proven optimum — ratio_top_diameter was
  still improving at the last tested step when the search stopped, so a better
  design in this same family plausibly exists just beyond what was tested.
- This best-found value (1.1688 kPa) becomes the working baseline for the next two
  runs (`20260709T024901`, `20260712T192155`), both of which try to beat it with a
  new 2.3376 kPa floor (2× this new baseline) — see their own summary slides.
-->

---
layout: two-cols-header
class: idea-slide
---

# D13 &middot; <u>Flexure-hinge (piecewise stiff/thin) longeron</u>

::left::

<div class="text-sm leading-snug">

- **What:** A spatially-varying longeron: thick `RectangularProfile` ends
  near both rings (global stiffness) with a deliberately thin mid-span
  "hinge" segment to cap peak bending strain.
- **Origin:** common sense — decouple average stiffness (thick ends) from
  peak local fibre strain (thin hinge), a DOF no uniform family could access.
- **Stats:** n=56 → 45 coil → 45 riks → 1 good (1.24× Bessa, current metric)
  p50/p90/p100 — σ_crit: 3.01/13.96/41.51 · mcs: .93/1.00/1.00 · mls: .067/.121/.250
  cleared: 40 of 45 decided ≥ 2× Bessa (0.2244) · novel: yes — σ clears easily across this
  family; mls (local strain) is the gate the hinge-thinness relationship never predicts
  best good: a=.00452 b_end=.0712 b_hinge=.0200 hinge_frac=.380 pitch=.860 +1 more → σ=.1391 mcs=1.00 mls=.019
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  By the study's strict adequacy bar, but the raw
  signal is a clear dead end: how thin the mid-span hinge is shows no
  consistent relationship with peak strain across 45 designs (sometimes
  thinner helps, sometimes it doesn't) — there's no sweet spot to dial in,
  and it underperforms the 0.3644 kPa uniform-section baseline regardless.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D13_flexure_hinge_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D13_flexure_hinge_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** a&isin;[.003,.03] — leg cross-section. b_end&isin;[.010,.075] — thick end-segment
depth (near the rings). b_hinge&isin;[.005,.030] — thin mid-span hinge depth. hinge_fraction
&isin;[.05,.9] — fraction of the longeron's length occupied by the thin hinge segment.
ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] — usual per-storey pitch/taper
meaning. Fixed: ratio_shear_modulus=.3677 (.334-.45 also swept as a free var in some runs of
this campaign — see notes).

**Seed:** BARREN — hinge thickness shows no consistent relationship with peak strain across 45
converged designs (sometimes thinner helps, sometimes it doesn't) — there is no sweet spot to
dial in, and every tested point underperforms the uniform-section baseline regardless.

**Deferred:** Stats-migration note (2026-08-04): this campaign's own feasibility gate
used mcs&ge;0.90 (not the usual 0.80) per `analyze_ledger.py` — the mcs quartiles
above reflect that stricter bar. Notably clean solve rate (45/45 Riks converged) vs.
other families in this deck.

**Timeline:** D002+D005+D006: search (this is H1 of run `20260708T021335`). D005's
first attempt died silently after only 12/50 planned evals — traced to a genuine
`cei_core.py` NaN-handling bug (not a process crash), fixed and verified before
D006's corrected continuation. D008: post-hoc CV adequacy check (Charter §2):
sigma_crit objective GP is strongly above chance (R²=0.940), but
max_compressive_strain (R²=-0.461) and the coilable classifier (identical to a
majority-class dummy on every fold) are not — the same binding-constraint-surrogate
failure mode this run's own H2/H3 also hit.

**Infra:** ODB: data/idea_odbs/20260708T021335_H1_flexure_hinge/ (source:
presentation/resim/flexure/riks_5d90665da6d54585b4b429f4c5d17007). GIF: native
Abaqus/CAE Viewer export, standard pipeline. The alternating thick/thin segments
along each leg's length are directly visible in the rendered beam profiles
(renderBeamProfiles=ON) — the coiled, fully-collapsed frame shown is the one
feasible design found (σ_cr,nd=0.1391 kPa).
-->

---
layout: two-cols-header
class: idea-slide
---

# D12 &middot; <u>BoxProfile hollow-tube cross-section</u>

::left::

<div class="text-sm leading-snug">

- **What:** A closed, thin-walled rectangular hollow-tube (`BoxProfile`)
  longeron, motivated by mining the 50,000-point Bessa 7D dataset for
  high-torsion/bending-stiffness combinations no solid family could reach.
- **Origin:** dataset-mining common sense — a least-squares fit of
  high-performing 7D rows to box geometries had poor residuals (~98%
  relative L2 error), so the family was built and searched directly.
- **Stats:** n=51 → 36 coil → 36 riks → 4 good (2.78× Bessa, current metric)
  p50/p90/p100 — σ_crit: 4.20/60.35/90.13 · mcs: .61/1.00/1.00 · mls: .043/.097/.151
  cleared: 33 of 36 decided ≥ 2× Bessa (0.2244), pre-contact metric, not comparable to the
  current incumbent · novel: no on shape — this idea's own Origin is mining Bessa's generalized
  section space for a point no solid shape reaches, then picking a shape to realize it; the high
  end likely also reflects the non-coiling stiff mode noted above, not 33 genuinely useful designs
  best good: a_out=.0184 b_out=.0543 t1=.003 t3=.002 pitch=.602 +1 more → σ=.3123 mcs=1.00 mls=.018
  (high σ_crit p90/p100 is a real, much stiffer coiling response that stalls early, not a
  different mode — see notes)
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  By the strict adequacy bar, but a clear
  negative signal — the box profile genuinely coils (confirmed by real rotation data), it
  just needs far more force and stalls before reaching full travel; same practical
  conclusion as the solid rectangle: underperforms.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/D12_box_hollow_tube_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
**Input space:** a_out, b_out&isin;[.006,.10] — outer box dimensions. t1, t3&isin;[.0005,.02] —
wall thicknesses. ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] — usual per-storey
pitch/taper meaning. Fixed: ratio_shear_modulus=.3677, circular=3 (cross-section-family switch).

**Seed:** BARREN — the outer-tangential-dimension sweep's feasible windows (0.02, 0.054) sit in a
sea of 6-of-8 infeasible points with no monotonic trend to climb. The "non-coiling stiff mode"
this slide previously blamed does not hold up: direct inspection of the one archived Riks
history (UR about the mast axis, ratio_a_out=.0389/ratio_b_out=.0753, a cleared-but-not-good
point) shows the top ring genuinely rotating past 116 degrees, unstabilized (ALLSD=0) — real
coiling, not a mode switch. It's just much stiffer (sigma_peak~5.2 kPa there, an order of
magnitude over typical designs) and stalls at 56% raw compression instead of reaching full
travel. A closed thin-wall box resists the twist the coiling mechanism needs, so it takes far
more force to get the same rotation and runs out of travel first — that's the real mechanism,
not a parameter this search under-sampled. Shape novelty was never a
real claim here either way — by the idea's own stated method, it was built by mining Bessa's own
generalized 7D dataset for a stiffness combination no solid shape reaches, then picking a shape
to realize that already-implicit point. The genuinely new information is mechanistic (a
different, mode-switching failure than the solid rectangle's clean collapse), not the shape.

**Timeline:** D004: build + validate the BoxProfile family. D007: search (this run's
H2) — the outer-tangential-dimension sweep found feasible windows at ratio_b_out=0.02
and 0.054 but infeasible at 6 of 8 other swept points, a genuinely different
mechanical behavior from the solid-rectangle family's clean, monotonic collapse (this
run's H4, which folds into the run17-rectangle-anchor idea), even though the net
practical result (underperforms) matches.

**Infra:** ODB: data/idea_odbs/20260708T021335_H2_box_hollow_tube/ (source:
presentation/resim/box/riks_c6f5fdb729c549fd93c5ddb53065dde3). GIF: native Abaqus/CAE
Viewer export, standard pipeline. The hollow box's rectangular tube profile is
directly visible in the rendered beam cross-sections.
-->

---
layout: two-cols-header
class: idea-slide
---

# D11 &middot; <u>Heterogeneous (2 stiff + 1 compliant) longerons</u>

::left::

<div class="text-sm leading-snug">

- **What:** Made the 3 longerons non-identical: 2 stiff `RectangularProfile`
  + 1 compliant `RectangularProfile`, same radial dimension, unchanged
  rings.
- **Origin:** common sense — the compliant longeron absorbs large
  rotations, "rescuing" compressibility while the stiff ones carry
  buckling load.
- **Stats:** n=46 → 32 coil → 32 riks → 1 good (3.25× Bessa, current metric)
  p50/p90/p100 — σ_crit: 1.86/21.94/40.42 · mcs: .53/1.29/1.49 · mls: .060/.130/.396
  cleared: 30 of 32 decided ≥ 2× Bessa (0.2244), pre-contact metric, not comparable to the
  current incumbent · novel: no — σ clears easily across this family; the ratio's non-monotonic
  relationship to strain is what actually blocks feasibility
  best good: a=.00920 b_stiff=.01875 b_compliant=.01875 pitch=.602 top_d=.038 → σ=.3644 mcs=1.00 mls=.020
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  By the study's adequacy bar, but the mechanism
  is contradicted: the stiffness ratio between the compliant and stiff
  longerons shows no consistent relationship with strain across the 32
  converged designs (weak, non-monotonic) — a more compliant leg sometimes
  helps and sometimes doesn't, undercutting the core hypothesis that mild
  heterogeneity predictably "rescues" compressibility (ratio=0.951 stalled
  at mcs=0.160 vs. ratio=1.0's mcs=0.9999) — no improvement over uniform
  found anywhere.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D11_heterogeneous_longerons_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D11_heterogeneous_longerons_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center px-2">Chart/gif show a typical population point
  (&sigma;=0.867 kPa) — NOT the best-good design (&sigma;=0.3644) described in Stats.</div>
</div>

<!--
**Input space:** a&isin;[.003,.03] — radial dimension, shared by all 3 legs. b_stiff&isin;
[.010,.075] — the 2 stiff legs' tangential dimension. b_compliant&isin;[.005,.030] — the 1
compliant leg's tangential dimension. ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8]
— usual per-storey pitch/taper meaning. Fixed: ratio_shear_modulus=.3677.

**Seed:** BARREN — the stiffness ratio between compliant and stiff legs shows no consistent
relationship with strain across 32 converged designs (weak, non-monotonic: ratio=0.951 stalled
at mcs=0.160 while ratio=1.0, i.e. uniform, hit mcs≈1.0) — there is no direction to dial the
heterogeneity in, and the best-found point never beat the uniform baseline it was meant to rescue.

**Deferred:** Stats-migration note (2026-08-04): mcs values exceeding 1.0 appear in
this raw dataset (p100=1.49) — a real logged value, not a typo; not investigated
further.

**Timeline:** D010: build + validate (exact degenerate reproduction of the known
baseline). D011: 45-eval search (this run's H3). D012: post-hoc CV — shows the same
recurring pattern as this run's H1/H2: sigma_crit is strongly learnable (R²=0.920),
max_compressive_strain is moderately learnable (R²=0.418, above chance but noisier).

**Infra:** ODB: data/idea_odbs/20260708T021335_H3_heterogeneous_longerons/ (source:
presentation/resim/heterogeneous/riks_fb818885227f43fe888ec53eafa44a17, representative
point solved at sigma=0.867; the family's actual near-degenerate best-found point was
~0.3644, i.e. the baseline itself). GIF: native Abaqus/CAE Viewer export, standard
pipeline. The visibly different cross-section sizes among the three legs (two thick,
one thin) are directly visible in the rendered beam profiles — the asymmetric coiling
behavior this produces is real, not a rendering artifact.
-->

---
class: summary-slide
---

# Run `20260706T204732` — summary

<div class="text-sm leading-snug">

Every hypothesis this run either fails outright or is blocked by the same recurring issue: the Riks compressive-strain constraint surrogate is consistently unreliable in the sparse-feasible regions this run searched.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Relax rectangle-anchor slenderness floor to ≥8 | ❔ | folds into run17-rectangle idea slide; surrogates not above chance; raw 0.3130 kPa, worse than ≥10 baseline | D6 |
| H2 | Add pretwist to the rectangle-anchor family | ❔ | folds into run17-rectangle idea slide; same surrogate-adequacy standard as H1/H3 | D6 |
| H3 | Elliptical top/bottom rings, phase offset | ❔ | own idea slide below; strongly suggestive dead end | D10 |
| H4 | Scale ratio_b and pitch together at slenderness=10 | ❌ | folds into run17-rectangle idea slide; feasibility collapses past smallest tested width | D6 |
| H5 | Radially bowed longerons | ❌ | own idea slide below | D9 |

 &nbsp;&middot;&nbsp; **Cost: $75.28** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H1: D003 ran a 60-eval constrained CEI-BO campaign in the [8,10) slenderness band;
  2/60 feasible, best 0.3130 kPa (worse than the established ≥10 optimum, 0.3644 kPa).
  D014's post-hoc 5-fold CV: sigma_crit GP R²=0.997 (excellent) but
  max_compressive_strain R²=-0.192 and max_local_strain R²=-5.26 (both below chance) —
  applying the same standard later used for H2/H3, retracted from FALSIFIED to
  INCONCLUSIVE.
- H2: D014's CV shows max_compressive_strain R²=-0.026 for this campaign too — the
  identical binding-constraint failure mode as H1/H3. D004's own cross-cutting finding:
  only 1/44 coilable rows in the whole campaign was fully feasible.
- H4: D005 ran the anchor reproduction (bit-matched, sigma_crit=0.364418) plus a
  systematic 2-stage grid (48 new points) holding slenderness fixed at exactly 10.0;
  only the smallest tested b (closest to baseline) had any feasible point at all (2/6);
  every larger b anchor (0.025 through 0.075) had zero feasible points out of 6 each.
-->

---
layout: two-cols-header
class: idea-slide
---

# D10 &middot; Elliptical top/bottom rings, phase offset

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the mast's circular top and bottom rings with
  independently-parametrized ellipses plus a phase offset between the top
  and bottom ring's major-axis orientation, to break the rotational
  symmetry that forces every longeron to undergo identical peak curvature.
- **Origin:** common sense structural-symmetry-breaking hypothesis, not a
  literature citation.
- **Stats:** n=67 → 9 coil → 9 riks → 0 good
  p50/p90/p100 — σ_crit: 0.36/1.97/4.05 · mcs: 0.36/0.47/0.78 · mls: .012/.021/.039
  cleared: 9 of 9 decided ≥ 2× Bessa (0.2244) · novel: no — every coilable design clears σ
  trivially near the untwisted baseline's own 0.364 kPa; mcs (compressive strain) is the gate
  best good: none (0/67 passed every criterion)
  (combines D008's 19-pt dense grid + D010's 48-pt broader search; the sharper
  finding — mcs collapses 0.9999→0.398 at the first non-circular step tested —
  doesn't survive as an aggregate quartile, see speaker notes)
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  By the study's own strict adequacy bar (the
  guiding constraint surrogates were not demonstrably above chance, so a
  closed non-existence verdict isn't licensed) — but the raw picture is
  about as close to a clean dead end as this deck sees short of a formal
  FALSIFIED: elliptical rings very sharply destroy coilability rather than
  redistributing strain as hypothesized.


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D10_elliptical_rings_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D10_elliptical_rings_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
  <div class="text-xs opacity-50 text-center">No — across all 67 evals in both campaigns, the
  single best mcs ever reached was 0.78 (p100), and even that one failed other criteria;
  this chart's own typical point tops out at 0.40.</div>
</div>

<!--
**Input space:** ring_aspect_ratio&isin;[1,1.5] — ellipse major/minor axis ratio.
ring_phase_offset&isin;[0,.2] rad — rotation between top and bottom ring's major axis.
a&isin;[.004,.02], b&isin;[.01,.045] — longeron cross-section semi-axes. ratio_pitch&isin;
[.3,1], ratio_top_diameter&isin;[0,.6] — usual per-storey pitch/taper meaning. Fixed:
circular=2 (cross-section-family switch), n_longerons=3, n_storeys=1, twist_angle=0,
ratio_shear_modulus=.3677.

**Seed:** BARREN — already re-run once (see below) with the phase offset re-tested directly and
still FALSIFIED; the cliff at the first non-circular step is sharp and reproduced twice, leaving
no untried perturbation of this idea rather than a genuinely different symmetry-breaking mechanism.

**Deferred:** Verdict history: the strategizer initially closed this FALSIFIED given
the sharp cliff and zero-feasible broad search; the validator flagged (per Charter §2)
that the guiding constraint surrogates (max_compressive_strain, max_local_strain,
coilable) were NOT above chance (mean-fold R²=-0.036/-0.050, classifier below majority
baseline) — Charter §2 requires ANY guiding surrogate to predict above chance before a
non-existence verdict can close, and "near-chance surrogate performance is what you'd
expect near an empty region anyway" is exactly the post-hoc plausibility argument the
charter forecloses. Retracted to INCONCLUSIVE.

**Timeline:** This is H3 of run `20260706T204732`. This idea was re-tested once more,
outside this deck's batch range, in run `20260718T031519` H1 (elliptical rings w/
phase offset re-test, FALSIFIED) — that refinement folds into this same idea, but
belongs to a later batch's summary slide.

**Infra:** ODB: data/idea_odbs/20260706T204732_H3_elliptical_rings/ (source:
presentation/resim/elliptical/riks_ellring_48e398830e1c4b4ca2e491e4da1e547d). GIF:
native Abaqus/CAE Viewer export, standard pipeline. The rendered design shows visibly
incomplete/partial coiling (a mid-strain frame, not the collapsed cliff case) — a
representative, still-somewhat-coiling point from the family, per the format
contract's "typical, not necessarily best" no-winner convention.

**Chart rebuilt with `bo/mini_chart.py`** (was a stale, pre-2026-08-31 chart with no
mls color coding) — real data from the same archived ODB above, sigma_peak=0.2912 kPa
at mcs=0.3983 max, matching this slide's own "mcs collapses to 0.398" figure exactly.
Never turns grey because this specific design's own strain never approaches the 2%
cap — its failure mode is the mcs collapse the Stats bullet already names, not strain.
-->

---
layout: two-cols-header
class: idea-slide
---

# D9 &middot; Radially bowed (pre-curved) longerons

::left::

<div class="text-sm leading-snug">

- **What:** Gave each longeron a smooth radial offset by height — zero at
  both rings, max inward bow at mid-height — to geometrically pre-condition
  the coiling path and retain high compressive strain.
- **Origin:** common sense geometric hypothesis, not a literature citation.
- **Stats:** n=48 → 45 coil → 27 riks → 1 good (0.53× Bessa)
  p50/p90/p100 — σ_crit: 1.37/8.97/16.00 · mcs: 0.44/1.00/1.00 · mls: .024/.045/.071
  cleared: 23 of 27 decided ≥ 2× Bessa (0.2244) · novel: no — clearing the σ bar is common
  in this family, mcs (compressive strain) is the gate that bowing itself collapses
  best good: bow_amp=.087 a=.005 b=.013 pitch=.32 top_d=.35 → σ=.0591 mcs_full=1.00 mls=.013
- **Verdict:** FALSIFIED · WEAK<br>
  Bowing does the opposite of hypothesized — a confound-free dose-response sweep shows
  max_compressive_strain decreasing monotonically with bow (48% drop, 0.5846→0.3040),
  collapsing strain rather than protecting it. A broader 48-eval joint search finds one real
  feasible design, but far weaker than baseline (0.53× Bessa). Across the full converged
  population the effect washes out once other dimensions vary freely — real in the controlled
  comparison, not generalizable (see notes).


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D9_bowed_longerons_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D9_bowed_longerons_landscape.gif" class="rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** bow_amp&isin;[0,.2] — max inward radial bow at mid-height (zero at both rings).
a&isin;[.004,.02], b&isin;[.01,.045] — cross-section semi-axes. ratio_pitch&isin;[.3,1],
ratio_top_diameter&isin;[0,.6] — usual per-storey pitch/taper meaning. Fixed: circular=2
(cross-section-family switch), n_longerons=3, n_storeys=1, twist_angle=0,
ratio_shear_modulus=.3677.

**Seed:** BARREN — the dose-response sweep is a clean, monotonic causal result in the wrong
direction (more bow → less strain retained), not a noisy or ambiguous one; there is no amplitude,
sign, or profile of "bow" left to try that the mechanism itself doesn't already rule out.

**Timeline:** D011: mechanism dose-response sweep (this run's H5). D012: 48-eval joint
5D existence follow-up — Pearson/Spearman check on the converged subset (mcs vs.
bow_amplitude: r=-0.175, ρ=-0.163, p=0.417) finds only a weak, non-significant
correlation. This is one of the deck's clean mechanism falsifications, analogous in
kind to the format-example twisted-strip slide's claim (a): a single-variable,
matched-conditions, causal dose-response sweep is adequate on its own terms (no
CV/surrogate check needed) because it is a designed experiment directly testing the
causal claim, not a surrogate-guided search whose adequacy depends on above-chance CV.
Deck-port pass (2026-08-26): σ corrected from .0757 kPa (pre-2026-08-06 Stage-1
eigenvalue metric) to .0591 kPa (0.53× Bessa, current Stage-2 windowed sigma_peak) —
78% of the old figure, consistent with response_metrics.py's own documented
0.736-0.859 overprediction ratio for this metric-version change. mcs and mls both
independently reproduce the cited values exactly (mls=.013256), confirming the same
design point; only σ needed correction. Verdict (FALSIFIED · WEAK) unchanged either
way.

**Infra:** ODB: data/idea_odbs/20260706T204732_H5_bowed_longerons/ (source:
presentation/resim/bowed/riks_bow_86c0a1b0a97a46e480420304ad196708). Landscape
re-render (2026-08-26): clean, no clipping across the full window (mcs 0%→88%);
replaces the old native-export gif with the split-panel layout, same underlying ODB.
-->

---
class: summary-slide
---

# Run `20260705T181941` — summary

<div class="text-sm leading-snug">

The run that broke the SCLF "486 kPa" headline (real physics, invalid strain) and replaced it with a smaller but genuinely valid anchor (0.3644 kPa) the rest of the study builds on.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Re-test "thick SCLF" under the new local-strain criterion | ✅ | mls=24.7% — invalidates SCLF; see that slide | D5 |
| H2 | SCLF family ceiling: stiffness-vs-strain trade-off (analytical) | ✅ | no circular design breaks it, 95 evals, above-chance surrogates | D5 |
| H3 | n_storeys=2 lowers curvature/strain | ❔ | mechanism runs backwards — strain rose 13.5%; folds into multi-storey slide | D4 |
| H4 | Elliptical cross-section | ❔ | untestable — Abaqus 2024 has no EllipticalProfile; own idea slide below | D8 |
| H5 | Square cross-section | ❌ | own idea slide below | D7 |
| H6 | Anisotropic rectangle, original orientation | ❌ | folds into run17-rectangle-anchor slide | D6 |
| H7 | Anisotropic rectangle, reversed (compound claim) | ❔ | under-powered; folds into run17-rectangle-anchor slide | D6 |
| H8 | Anisotropic rectangle, reversed (clean existence claim) | ✅ | becomes the study's canonical anchor; own idea slide below | D6 |

 &nbsp;&middot;&nbsp; **Cost: $65.62** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail beyond the idea slides:

- H2: D009 5-fold CV on 95 combined ledger rows (D003+D006+D008) — sigma_crit
  (log1p) GP CV R²=0.891 (pooled 0.904), max_local_strain GP CV R²=0.654 (pooled
  0.661, the actually-binding constraint), coilable classifier CV accuracy=0.905 vs
  0.737 majority baseline — all three clearly above chance, satisfying both prongs
  of the study's Charter §2 adequacy bar (coverage AND above-chance surrogate).
- H3: 41 evals, stopped on the eval cap not convergence — inadequate power for the
  broad existence-negation claim (retracted from an initial FALSIFIED). The
  mechanistic A/B pair (identical ratio_d/pitch/top_diameter, only n_storeys differs)
  is a clean, confound-free comparison on its own terms: max_local_strain
  0.01994→0.02263 (+13.5%) at n_storeys=2, opposite of the registered prediction.
- H6: two decorrelated 1D sweeps (D010) — Exp 1 (tangential fixed, radial varied):
  strain rises 4× (0.0203→0.0804) tracking sigma_crit. Exp 2 (radial fixed, tangential
  varied): strain flat (0.041-0.047), sigma_crit swings 22× (0.138→3.05) — exactly
  backwards from the registered mechanism (radial was predicted to drive stiffness,
  tangential to be flat).
-->

---
layout: two-cols-header
class: idea-slide
---

# D8 &middot; Elliptical cross-section

::left::

<div class="text-sm leading-snug">

- **What:** Proposed an elliptical longeron cross-section (Abaqus-native
  `EllipticalProfile`, `DURING_ANALYSIS` integration), oriented so its short axis lies in the
  plane of dominant coiling bending, to raise torsional stiffness past the circular family's
  strain ceiling. Free: none — untestable, see Verdict
- **Origin:** direct mechanistic extension of the SCLF (circular) family —
  common sense, not a literature citation.
- **Stats:** n=0 &rarr; 0 coil &rarr; 0 riks &rarr; 0 good — untestable (hard software-capability
  gap, see Verdict)<br>
  quartiles unavailable — no design was ever built, so there is no population to compute over<br>
  cleared: none (0 decided) &middot; novel: untested — the geometry itself could never be built<br>
  best good: none (0/0)
- **Verdict:** INCONCLUSIVE · UNTESTABLE<br>
  Genuinely so: the hypothesis as registered is untestable, not falsified —
  `model.EllipticalProfile` doesn't exist in the installed Abaqus 2024 kernel, and
  `GeneralizedProfile` + `DURING_ANALYSIS` is rejected at `.inp`-write time. A hard
  software-capability gap, not a negative physics result; substituting `RectangularProfile` was
  registered separately as its own hypothesis, not a silent reinterpretation.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-8 text-center opacity-70 max-w-xs mx-auto">
    <div class="text-3xl mb-2">⊘</div>
    <div class="text-sm">No ODB: untestable, not a negative result — the installed
    Abaqus 2024 has no EllipticalProfile section type compatible with
    DURING_ANALYSIS integration.</div>
  </div>
</div>

<!--
**Seed:** BARREN — reviving this literally requires an Abaqus kernel with a native
`EllipticalProfile`/`DURING_ANALYSIS`-compatible section, an infra change outside this study's
control; the mechanistic question it was asking (anisotropic torsional stiffening) was already
substituted and tested as this run's H6 and came back FALSIFIED, so the physics question this
idea wanted answered is closed even though the literal geometry was never built.

**Timeline:** D005: introspection — confirmed `model.EllipticalProfile` absent from
the installed Abaqus 2024 kernel, and `GeneralizedProfile(...,
integration=DURING_ANALYSIS)` rejected at input-file-write time (this run's H4).
Originally the strategizer briefly closed this FALSIFIED before the validator/Charter
§4 correction: an untestable literal claim cannot be falsified, only marked
untestable. D010: the substituted, actually-tested idea (anisotropic
RectangularProfile, radial-long/tangential-short orientation, registered as this same
run's H6) — FALSIFIED via two decorrelated 1D sweeps showing max_local_strain
tracking sigma_crit almost proportionally along the radial axis, the opposite of the
intended decoupling; folds into the run17_rectangle_anchor idea's story, since the
REVERSED orientation tested next (H7/H8) is what actually becomes the study's anchor
family.

**Infra:** No ODB, by design — one of only two ideas in the whole 25-idea "genuinely
new" list with no ODB (the other: pretwisted longerons, earlier this run-range). The
tape-spring idea (`20260730T020245` H2) previously belonged in this no-ODB group
while that run was still executing; it has since closed and its own ODB was archived
— see its own slide, elsewhere in this deck.
-->

---
layout: two-cols-header
class: idea-slide
---

# D7 &middot; <u>Square (isotropic) cross-section</u>

::left::

<div class="text-sm leading-snug">

- **What:** Tested a square longeron cross-section — at matched
  half-width/fiber-distance, a square carries ~1.7× a circle's moment of
  inertia (I_square/I_circle=64/(12π)), bend axis on a flat side not a
  diagonal.
- **Origin:** common sense, basic section-property comparison — not a
  literature citation.
- **Stats:** n=50 → 50 coil → 50 riks → 9 good (1.23× Bessa)
  p50/p90/p100 — σ_crit: .22/4.54/13.15 · mcs: .99/1.00/1.00 · mls: .022/.055/.098
  cleared: 23 of 50 decided ≥ 2× Bessa (0.2244), pre-contact metric, not comparable to the
  current incumbent · novel: no on shape — a genuinely varied sweep over side/pitch/top_diameter,
  not a repeated point, but Bessa's own generalized section space already covers this axis; mls
  (local strain) is what blocks feasibility
  best good: side=.0097 pitch=.25 top_d=.218 → σ=.160 mcs=1.00 mls=.020
- **Verdict:** FALSIFIED · WEAK<br>
  Contradicted by an adequate,
  above-chance-surrogate search (σ_crit CV R²=0.999, mls CV R²=0.545).
  (Square does edge circular in σ_crit at matched strain, 0.16-0.19 vs
  ~0.13-0.22, but the 0.196 kPa floor-clearing prediction — 2× the 0.1306
  kPa baseline — still failed: best feasible was 0.1600 kPa, 18.4% short.)


</div>

::right::

<div class="flex flex-col gap-2" style="height: 460px">
  <div class="flex items-center justify-center" style="height: 175px">
    <img src="/gifs/D7_square_section_mini.png" style="max-height: 175px; max-width: 100%" />
  </div>
  <div class="flex items-center justify-center" style="height: 277px">
    <img src="/gifs/D7_square_section_native.gif" class="max-h-100 rounded shadow-lg" style="max-height: 277px; max-width: 100%" />
  </div>
</div>

<!--
**Input space:** side&isin;[.005,.025] — square side length. ratio_pitch&isin;[.25,1],
ratio_top_diameter&isin;[0,.6] — usual per-storey pitch/taper meaning. Fixed:
ratio_shear_modulus=.3677, circular=2 (cross-section-family switch), n_longerons=3,
n_storeys=1, twist_angle=0.

**Seed:** BARREN — the shortfall (18.4%) is the same radius^4-stiffness-vs-linear-strain trade-off
this run's H2 established analytically for the circular family; the square section edges circular
slightly at matched strain but doesn't escape the trade-off, and there is no reason a different
cross-section shape family would either (each subsequent variant re-confirms the same ceiling).

**Deferred:** σ recomputed directly from the ODB (2026-08-26) gives σ_max=.1549 kPa
(1.38&times; Bessa) — close to but not exactly the cited .160 (mcs and mls both
reproduce the cited values almost exactly: mcs_full=1.094, mls=.019773&asymp;.020), a
small (~3%) discrepancy left unresolved since it doesn't change the FALSIFIED verdict
either way.

**Timeline:** D011: search (this run's H5). D012: surrogate CV adequacy check. This
run's H2 (SCLF family ceiling, meta/analytical) established the underlying physical
trade-off this idea (and every subsequent cross-section variant) runs into: buckling
stiffness scales with cross-section radius^4 while coiling-induced local bending
strain scales only linearly with radius×curvature — 90 evaluations (D003+D006+D008,
cross-validated by D009) found no circular-family design that breaks this trade-off,
and the square-section test is essentially the same trade-off restated for a
different section shape.

**Infra:** ODB: data/idea_odbs/20260705T181941_H5_square_section/ (source:
presentation/resim/square/riks_c91bd5835aaf40f99dc06a3228aa4411). GIF: native
Abaqus/CAE Viewer export, standard pipeline, no ODB-specific gotchas — the square
cross-section's flat-sided profile is visible in the rendered beam geometry
(renderBeamProfiles=ON), distinguishing it visually from the circular SCLF renders
elsewhere in this deck. Landscape re-render (2026-08-26) clips real content (one
longeron's bottom end runs off-canvas at mcs=95% — this family's geometry is wider
than the landscape frame is tuned for, same class of issue as D34/D41/D17); kept the
existing native-export gif and only added the σ-vs-mcs mini-plot panel above it.
-->

---
layout: two-cols-header
class: idea-slide
---

# D6 &middot; <u>Anisotropic rectangle, reversed orientation (run17 anchor)</u>

::left::

<div class="text-sm leading-snug">

- **What:** Anisotropic `RectangularProfile` longeron, radial SHORT /
  tangential LONG — reverse of this run's earlier falsified orientation,
  at slenderness≥10, testing whether max_local_strain and sigma_crit
  decouple.
- **Origin:** direct extension of the elliptical-substitution idea above —
  mirror of this run's own H6, common sense, not a literature citation.
- **Stats:** n=165 → 149 coil → 148 riks → 6 good (2.79× Bessa)
  p50/p90/p100 — σ_crit: .86/4.26/7.52 · mcs: .80/1.00/1.00 · mls: .022/.034/.043
  cleared: 131 of 148 decided ≥ 2× Bessa (0.2244) · novel: yes — spans 3 independent BO
  campaigns over the same 4D box, not repeats of one point
  best good: a=.0092 b=.0188 pitch=.602 top_d=.038 → σ=.3644 mcs=1.00 mls=.0195
  (3 of the 6 also clear this run's own higher 0.196 kPa target; headline
  slenderness=16.04)
- **Verdict:** SUPPORTED · WORKS<br>
  Real, repeatable, non-fluke. This design
  becomes "run17_rectangle," the canonical anchor baseline reused
  throughout the rest of this deck (later refined to 0.7704 kPa, 5.9×
  Bessa, in subsequent runs — see speaker notes, not this campaign's own
  result).

</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/D6_run17_rectangle_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
**Input space:** a&isin;[.004,.014] — radial (short) semi-axis. b&isin;[.01,.045] — tangential
(long) semi-axis. ratio_pitch&isin;[.25,1], ratio_top_diameter&isin;[0,.6] — usual per-storey
pitch/taper meaning. Fixed: ratio_shear_modulus=.3677, circular=2 (cross-section-family
switch), n_longerons=3, n_storeys=1, twist_angle=0.

**Seed:** BARREN — it SUCCEEDED and became the floor. Beat **run17_rectangle**, not Bessa.

SEED RATIONALE (added 2026-08-08, rule 3(e)). BARREN here does not mean "failed" -- it means
SUCCEEDED and became the floor. Perturbations of the cross-section alone (aspect ratio,
orientation, taper) are inside the box this family already searched, so a rectangle-only campaign
that beats Bessa is re-deriving a settled result. The bar for a new slide is beating
run17_rectangle, not beating Bessa.
**Timeline:** H8 (this slide) of run `20260705T181941`, following H6 (original
orientation, FALSIFIED — max_local_strain rises 4× with the radial axis, tracking
sigma_crit almost proportionally, the opposite of decoupling; D010's two decorrelated
1D sweeps) and H7 (reversed orientation, but an over-specific compound prediction
demanding "multiple designs with meaningful margin" — INCONCLUSIVE, since only 1/46
valid-slenderness evals cleared the floor, too little data to confirm or deny the
compound claim). H8 registers only the clean, supported half of H7's claim: existence
of at least one valid design. Three distinct qualifying designs: D014's row 308
(ratio_a=0.00774, ratio_b=0.01417, slenderness=10.52, sigma_crit=0.2712 — found
incidentally in a broader unconstrained sweep, before the two slenderness-gated
searches ran), D016's design (slenderness=16.04, sigma_crit=0.3644, the headline,
rendered here), and D017's design (slenderness=15.85, sigma_crit=0.2287). The 2026-08-04
Stats-migration's G=6 adds 3 more designs meeting every universal criterion but below
this run's own 0.196 kPa target: two occurrences of sigma_crit=0.1786 and one at
0.1003 — real, just not this run's own headline finding. One row in the 149-row
Riks-converged population (D014/D016/D017 combined) showed mcs=1.41/mls=1.37, both
physically impossible (mcs is bounded to [0,1] by definition) — excluded from the
R=148 quartile population above as corrupted data, not merely flagged. This family
keeps improving across later runs, none of which earn a new idea slide (all fold into
this one per the deck's rule 1): run `20260706T204732` tests relaxing the slenderness
floor to ≥8 (INCONCLUSIVE) and adding pretwist (INCONCLUSIVE), run `20260708T021335`
H4 raises the tangential dimension alone to a new best of 1.1688 kPa (SUPPORTED), and
run `20260712T192155` H1 eventually finds a repeatable 2.5656 kPa counterexample
(FALSIFIED against a tighter 2.3376 kPa floor introduced by then) — see those runs'
own summary slides for detail.

**Corrected 2026-08-31 (verdict audit):** the Timeline above traces this family's own
campaigns to 0.3644 (D016, this slide's own headline) -> 1.1688 (run
`20260708T021335` H4) -> 2.5656 (run `20260712T192155` H1, later FALSIFIED against a
tighter floor) -- none of which is 0.7704 kPa, the number this slide's own Verdict
cites as what "run17_rectangle" became. Checked directly: `bo/confirmed_anchors.json`
IS the authoritative provenance record for that exact figure (its own `role` field
documents the full warping-check saga and the 2026-08-06 metric-v1 re-derivation to
0.6071/0.6077 kPa current-metric) -- but this slide's own Timeline does not actually
contain the step that arrives at 0.7704 specifically. Left as a disclosed gap rather
than a fabricated derivation; cite `bo/confirmed_anchors.json` directly for this
number's provenance, not this slide's own Timeline.

**Infra:** ODB: data/idea_odbs/20260705T181941_H8_run17_rectangle_anchor/ (source:
SCRATCH path /oscar/scratch/eaguerov/supercompressible_oracle/riks_09377e3040e64b82be337fcb827bd32e,
gold-verified in bo/confirmed_anchors.json). GIF: native Abaqus/CAE Viewer export,
standard pipeline — re-rendered fresh for this batch (an earlier square-canvas,
unlabeled-legend version existed from a prior rendering pass and has been replaced
with the current portrait/top-right-legend/schematic-ring pipeline to match this
deck's contract).
-->

---
class: summary-slide
---

# Run `20260630T164908` — summary

<div class="text-sm leading-snug">

The run that discovered circular cross-sections can pass Stage 2 where generalized sections categorically cannot — but its own headline design would not survive the local-strain criterion introduced the very next run.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Generalized Bessa-optimum Stage-2 Riks test (J=6.65e-6) | ❌ | 9.23% strain, not 90%; motivates the SCLF pivot | D2 |
| H2 | Solid Circular Longeron Family (SCLF), existence test | ✅ | 486 kPa at 90.06% strain — later invalidated (mls=24.7%, 12× the limit); own idea slide below | D5 |
| H3 | Shorter-pitch SCLF variant (ratio_pitch=0.30–0.40) | ❌ | best 50.91% strain; pitch=0.30 not even coilable | D5 |
| H4 | SCLF thick design (same finding as H2) | ✅ | same headline, later invalidated; see idea slide | D5 |
| H5 | Smaller top-ring SCLF variant | ❌ | 83.68% strain — smaller ring makes h_min LARGER, opposite of predicted | D5 |

 &nbsp;&middot;&nbsp; **Cost: $10.79** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H1: registered floor was 90% Riks strain on the exact Bessa-optimum design; result
  9.23%, RF3 history -1165N→-170N (snap-back, not coiling collapse). Adequate test
  (exact registered design, standard Riks scripts), prediction decisively contradicted.
- H3: D006 tested d=0.09 at pitches 0.40 (45.75% strain), 0.35 (50.91%), 0.30
  (not coilable, ztop_ur IndexError). Power-law extrapolation from H2's data had
  overestimated where 90% strain would occur.
- H4: D008 Test A used finer Riks arc-length steps (initialArcInc=0.01,
  maxArcInc=0.2, maxNumInc=600) than D007's earlier coarse attempt, which had failed
  to converge near the geometric limit (h_min=9.244mm) and was misread as a design
  failure rather than a numerical-settings issue.
- H5: D008 Test B1, top_diam=0.50 at the same pitch/d as H4; h_min=15.175mm (vs
  9.244mm at top_diam=0.5978) — mechanism is opposite of registered prediction.
-->

---
layout: two-cols-header
class: idea-slide
---

# D5 &middot; Solid Circular Longeron Family (SCLF), thick variant

::left::

<div class="text-sm leading-snug">

- **What:** Constrained the cross-section to a solid circle (ratio_d ∈
  [0.08,0.16], else free) after the generalized Bessa optimum failed
  Stage 2 categorically — testing whether J/I=2 is what Stage 2 needs.
- **Origin:** follow-up to this run's H1 (generalized optimum: 9.23% Riks
  strain, not 90%) — circular is the shape closest to Bessa 2019's own
  demonstration.
- **Stats:** n=42 → 28 coil → 5 riks → 0 good (mls never measured this campaign)
  p50/p90/p100 — σ_crit: 431.8/497.8/505.7 · mcs: .837/.892/.901 · mls: not measured
  cleared: 5 of 5 decided ≥ 2× Bessa (0.2244), pre-contact metric, not comparable to the
  current incumbent · novel: no — this is inside Bessa's own explored circular family, just
  thicker; mls (never measured) is the gate that later invalidated all 5 points anyway
  best good: none (0/42 passed every criterion)
- **Verdict:** SUPPORTED (RETRACTED) · DEAD-END<br>
  As existence at the time — circular passes Stage 1
  and this campaign's own Stage-2 mcs bar, generalized doesn't. Later
  invalidated (next run's H1): peak local strain 24.7%, 12× the 2% PLA
  limit, never checked here — the mechanism insight stands, the headline
  number doesn't.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/D5_sclf_thick_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
**Input space:** ratio_d&isin;[.08,.16] (constrained solid circle; else free) — cross-section
diameter. ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] — usual per-storey
pitch/taper meaning. Fixed: circular=1 (cross-section-family switch), n_longerons=3,
twist_angle=0, ratio_shear_modulus=.43681, and the generalized-optimum moments this campaign
was testing against (area=.00215, Ixx=1.35e-6, Iyy=1.24e-6, J=6.65e-6).

**Seed:** BARREN — the invalidating local-strain measurement (24.7%) is 12× over the 2% PLA
limit, the same order-of-magnitude gap this deck treats as unclosable elsewhere; the design's
real legacy is the three-criteria contract it forced into existence, not a refinement candidate.
This design sits entirely inside Bessa's own explored circular family (just thicker), so it was
never a shape novelty claim to begin with, and its own huge, real-looking σ numbers (431-506
kPa, all "cleared" against the campaign's own bar) hid a 24.7% strain violation the moment
someone actually measured it — the mechanism insight that forced the three-criteria contract is
the design's entire contribution, not the shape or the raw number.

**Timeline:** Stats-migration note (2026-08-04): N=42 combines D003's 36-pt Stage-1
LHS sweep (23 coilable) with 6 targeted refinement points across D004(2)/D005(2)/
D008(2); 5 of those 6 reached a converged Riks solve. test_A (the 485.996 kPa
headline) nominally passed this run's own mcs&ge;90% bar but mls was never measured
here — G=0 reflects the complete modern criteria, not this run's own incomplete pass
flag. This is H2 (existence) and H4 (this specific thick design) of run
`20260630T164908`, delegations D005/D008. H3 (shorter pitch, FALSIFIED — best 50.91%
strain, pitch=0.30 not even coilable) and H5 (smaller top ring, FALSIFIED —
top_diam=0.50 gives strain=83.68%, WORSE than the original 0.5978, because a smaller
top ring produces a LARGER geometric coiling limit h_min, opposite of what was
predicted) are both refinements of this same idea, folded in here. H1 this run
(generalized Bessa optimum Stage-2 test, J=6.65e-6/Ixx=1.35e-6, sigma=65.31kPa): max
compressive strain only 9.23% (RF3 peak -1165N then snap-back to -170N, not a coiling
collapse) — this is what motivated the whole SCLF pivot and folds into the extended-J
hollow-tube idea's story (same "generalized sections fail Stage 2" finding as H6/H7
of the prior run). The invalidation (run `20260705T181941` H1, delegation D001):
max_local_strain=0.24719 (24.7%), max_compressive_strain=0.89534 (barely below the
0.90 Stage-2 threshold too, at these exact Riks settings) — fails TWO of the three
criteria, not just one. This finding is what motivated the study's own formal
adoption of the three-criteria feasibility contract (coilable, Riks strain≥90%,
local strain≤2%) used in every subsequent run.

**Infra:** ODB: data/idea_odbs/20260630T164908_H4_SCLF_thick/ (source:
presentation/resim/thick_sclf/riks_6944016ddcca48608b995e9d6a4cbdfd). GIF: native
Abaqus/CAE Viewer export, thick circular tube visibly coiling into a tight
double-helix, strain colored (E11), dashed schematic rings, portrait canvas —
standard pipeline, no gotchas specific to this ODB.
-->

---
class: summary-slide
---

# Run `20260629T191754` — summary

<div class="text-sm leading-snug">

Three genuinely new mechanisms this run (multi-storey, n=5 longerons, extended-J hollow tube) — the extended-J family clears the Stage-1 sigma floor but categorically fails to actually coil (Stage 2), a pattern that reshapes every subsequent run's strategy toward circular cross-sections.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Pre-twist family, 46-eval anchor sweep | ❔ | suggestive negative; folds into pretwisted-longerons slide | D1 |
| H2 | Multi-storey topology (n_storeys=2) | ❔ | own idea slide below | D4 |
| H3 | n_longerons=5 (extended topology) | ✅ | exceeds 65.3 kPa but not the 75.1 kPa floor; own idea slide below | D3 |
| H4 | Max-torsion single-longeron anchor (n_longerons=3, twist=0) | ❌ | 71.59 kPa, below 75.1 kPa floor; motivated H5's search | D2 |
| H5 | Extended-J hollow/cellular longeron | ✅ | Stage 1 only, 83.66 kPa; own idea slide below | D2 |
| H6 | Stage-2 Riks test of H5's D4 design | ❌ | 32% strain, not 90%; folds into extended-J slide | D2 |
| H7 | Stage-2 Riks test of H5's C4 design | ❌ | 9% strain, even worse; folds into extended-J slide | D2 |

 &nbsp;&middot;&nbsp; **Cost: $28.23** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail beyond what's in the idea slides:

- H1: 46/80 registered evals (license-server outage killed 26 planned runs);
  6/46 coilable, all ≤65.31 kPa; posterior path 0.8→0.35→0.25→(briefly FALSIFIED,
  validator-corrected)→0.03 INCONCLUSIVE.
- H4: direct point-test of B1 anchor (ratio_J=7.77e-6, ratio_Ixx=1.4e-6,
  ratio_shear_modulus=0.44); result 71.5943 kPa vs 75.1 kPa registered floor;
  power-law fit (σ∝J^0.56, sub-linear, not the naively-assumed linear GJ scaling)
  motivated the extended-J-beyond-domain-max search in H5.
- H6/H7: D4 Riks converged 18 increments then diverged (RF3: -1501N→-615N, load
  shedding, but "SOLUTION APPEARS TO BE DIVERGING"), max |U3| strain 15.99/50mm=32%.
  C4 Riks converged 22 increments, terminated at 5.90/65.32mm=9.0% strain — worse
  than D4 despite lower torsional stiffness, because of its longer mast height.
-->

---
layout: two-cols-header
class: idea-slide
---

# D4 &middot; Multi-storey topology (n_storeys=2)

::left::

<div class="text-sm leading-snug">

- **What:** Split the mast into two stacked storeys — an intermediate rigid
  ring at mid-height, still 3 continuous longerons per storey — instead of
  Bessa's single-storey topology, to see if a shorter per-segment coiling
  path could beat the Bessa 2019 paper optimum (65.3 kPa/longeron).
- **Origin:** common sense topology extension of the Bessa rocking-mast
  concept, not drawn from an outside literature source.
- **Stats:** n=32 → 9 coil → 0 riks → 0 good (mcs/mls never tracked this campaign)
  p50/p90/p100 — σ_crit (coilable only): 5.6/64.3/65.0 · mcs: not tracked · mls: not tracked
  (best coilable is 99.5% of the single-storey Bessa optimum by Stage-1
  σ_crit alone — never checked against real feasibility)
  cleared: none (0 decided) &middot; novel: untested — Stage 2 never ran this campaign
  best good: none (0/32 passed every criterion)
- **Verdict:** UNDERPOWERED · FERTILE-PARAMETRIC · max-J-at-half-pitch, n_storeys=2<br>
  The topology recovers almost all of the single-storey Stage-1 performance
  without losing coilability, and a real follow-up (40 evals on a lower-
  dimensional reparametrization) also found 0 feasible — but the single
  specific point flagged as the natural next step (max-J-at-half-pitch,
  extrapolated to ~75.9 kPa, clearing both floors) has still never been
  directly run at n_storeys=2 — see Seed. Not a confirmed dead end.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/D4_multistorey_n2_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
**Input space:** twist_angle&isin;[.05,.35] rad. ratio_pitch&isin;[.25,1.5], ratio_top_diameter
&isin;[0,.8] — usual per-storey pitch/taper meaning. ratio_shear_modulus&isin;[.334,.45].
ratio_area&isin;[1.17e-5,4.1e-3], ratio_Ixx&isin;[1e-7,1.4e-6], ratio_Iyy&isin;[1e-7,1.4e-6],
ratio_J&isin;[1e-6,7.77e-6] — generalized cross-section moments (Bessa's own 7D
parametrization). Fixed: n_longerons=3, n_storeys=2.

**Seed:** FERTILE — the lower-dimensional rectangle-family reparametrization that actually tracks
mcs/mls has only spent 40 of its own planned 120-eval budget (phase 1 zero-feasible, correctly
declined to zoom further with no incumbent); the max-J-at-half-pitch point extrapolated at ~75.9
kPa (clearing both floors) was flagged as the natural next step and still hasn't been directly run.

**Timeline:** Stats-migration note (2026-08-04): this idea has since been re-tested
out-of-band (not a new agentic run — see docs/assistant_investigation_diary.md, not
tracked in this repo) using the study's own default 3-phase zoom search on D006's
lower-dimensional 4D rectangle-family reparametrization of this same topology
(`bo/experiments/real_designs/run_multistorey.py`): 40 real evals, phase 1 found zero
feasible points and correctly declined to zoom further (no incumbent to center a
smaller box on). This directly checks mcs/mls (unlike D004 above) and still finds
nothing — reinforcing, not resolving, the open question; a full 120-eval budget
hasn't been spent on this reparametrization yet. This is H2 of run `20260629T191754`,
delegation D004 (32/48 planned evals). Linear-scaling extrapolation predicted the
untested max-J-at-half-pitch point could reach ~75.9 kPa, potentially clearing BOTH
the 65.3 kPa and 75.1 kPa floors — this was flagged as the natural next step and
picked up by a later delegation testing max-J at n_storeys=1 (B1 anchor) before
committing further n_storeys=2 budget. This idea keeps reappearing across later runs
as a refinement target (an independent per-storey ratio_b variant in run
`20260712T192155` H2, a strain-barrier escape attempt in run `20260715T002538` H4, a
peak-local-strain reduction test in run `20260718T071133` H3) — all fold into this
same slide per the deck's rule 1, none earn their own slide. Run `20260718T071133`
H3, why INCONCLUSIVE (not FALSIFIED as first drafted): the strategizer's first pass
marked H3 FALSIFIED on the delegation's own self-reported "4/36 feasible,
best=0.1085 kPa, clear plateau" (diagnostics.jsonl VERDICT_SUBSTANCE_FLAG,
2026-07-18T11:38:07). A critic pass (retrospective, critic node, 2026-07-18T13:07:02)
caught two compounding problems by re-querying the ledger directly rather than
trusting the report: (1) a slenderness-formula bug meant the true feasible count was
3/36, not 4/36 -- one of the "feasible" rows didn't actually clear criterion 4; (2)
more importantly, ALL of the rows counted as feasible had `converged=False` -- they
were non-converged salvaged reads, not genuine Riks solutions. The strategizer's own
closing retrospective (2026-07-18T13:23:20) calls this out directly: a sparse,
non-converged-only "feasible" set cannot support a falsification claim per the
Charter, and the verdict was downgraded to INCONCLUSIVE. Kept here rather than fixed
silently, because it's a real instance of the adversarial-critic layer catching a
genuine science-integrity error the automated validator did not flag on its own axis
(it flagged sparsity; the critic separately caught the convergence issue).

**Infra:** ODB: data/idea_odbs/20260629T191754_H2_multistorey_n2/ (source:
presentation/resim/twostorey/riks_9a82d64e16d34b71ac1e541263cd92bf; illustrative
rectangular-family point, not bit-identical to the original run's anchor A5, but
representative of the n_storeys=2 mechanism). GIF: native Abaqus/CAE Viewer export
(presentation/render/render_odb.py). Only 5-6 Riks increments are present in this
archived ODB (a relatively shallow coiling test at this twist/pitch combination), so
the animation is short; the legs show very low strain throughout (E11 range roughly
±1.6e-3), consistent with this being a modest, not-yet-optimized point in the family
rather than its best-found design. Structural (beam-element) instance only, dashed
schematic top/bottom ring annotation per the format-contract convention (this render
script draws only the true top/bottom rings from the structural instance's own
z-min/z-max — it does not know about or annotate the intermediate mid-height ring
specific to this n_storeys=2 topology, since that ring is likewise a 0-D reference
point with no solid geometry to render).
-->

---
layout: two-cols-header
class: idea-slide
---

# D3 &middot; n_longerons = 5 (extended topology)

::left::

<div class="text-sm leading-snug">

- **What:** Increased the mast's rotational symmetry from Bessa's fixed 3
  longerons to 4, 5, and 6, at the same (near-optimal) 7D cross-section, to
  test whether more legs raise the per-longeron critical load.
- **Origin:** common sense topology extension — Bessa's own parametrization
  never varies longeron count, fixing it at 3 throughout the 2019 paper.
- **Stats:** n=31 (D005's own ledger; "48-evaluation" in an earlier draft
  could not be corroborated) → 20 coil → 0 riks → 0 good (Stage 2 never run)
  p50/p90/p100 — σ_crit (coilable only): 61.5/71.2/71.6 · mcs: not tracked · mls: not tracked
  cleared: none (0 decided) &middot; novel: untested — Stage 2 never ran this campaign
  best good: none (0/31 passed every criterion)
- **Verdict:** SUPPORTED · DEAD-END<br>
  As registered — but with an important nuance: none
  of n=4/5/6 reached the study's actual 75.1 kPa floor, and per-longeron
  σ_cr,nd turned out to be empirically independent of n_longerons at fixed
  cross-section (λ_cr ∝ n×J, and the /n normalization exactly cancels it) —
  so this axis alone does not open a new performance regime, it is
  orthogonal to it.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/D3_n5_longerons_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Native Abaqus render — no strain coloring (see notes).</div>
</div>

<!--
**Input space:** twist_angle&isin;[0,&pi;]. ratio_area&isin;[1.17e-5,4.1e-3], ratio_Ixx&isin;
[1e-7,1.4e-6], ratio_Iyy&isin;[1.13e-11,1.4e-6], ratio_J&isin;[1e-6,7.77e-6] — generalized
cross-section moments (Bessa's own 7D parametrization). ratio_pitch&isin;[.25,1.5],
ratio_top_diameter&isin;[0,.8] — usual per-storey pitch/taper meaning. n_longerons&isin;[3,6] —
the axis under test (main batch fixes it at 5; anchors also test 4, 6). Fixed: n_storeys=1.

**Seed:** BARREN — the independence from n_longerons is analytical, not a search artifact
(λ_cr ∝ n×J and the /n per-longeron normalization exactly cancels it), so no re-sweep of this
axis at any other cross-section would change the conclusion; it is a dimension the design space
can vary freely without it opening or closing performance, not a lead to chase further.

**Timeline:** This is H3 of run `20260629T191754`, delegation D005. n_longerons=5
topology variant of the extended-J Bessa-7D family; Stage-1 sigma_cr,nd=71.59 kPa,
matching the original finding, Riks re-solved fresh for this archive. Critical insight
carried forward: this run's finding that σ per longeron is independent of n_longerons
at matched cross-section directly motivated the extended-J search (H4/H5 next) as the
actual lever for beating the Bessa optimum.

**Infra:** ODB: data/idea_odbs/20260629T191754_H3_n5_longerons/ (source:
presentation/resim/n5_longerons/riks_60c367f12e3a4903839e9afe3127aa00). RENDERING
BLOCKER, reported per this batch's instructions rather than skipped: this archived
ODB's Riks step only recorded RF/RM/U/UR field output — no `E` (strain) field was
ever requested when the resim was originally run. render_odb.py's strain-coloring
step (`setPrimaryVariable(variableLabel='E', ...)`) therefore fails with "Primary
Variable not available: 'E' at integration points" on this specific ODB. This is a
genuine data-provenance gap in the earlier resim pipeline for this one family
(confirmed identical in the un-archived source copy too, so it is not an archiving
mistake), not a bug in render_odb.py itself, and not something fixable without a
fresh Abaqus solve (out of scope for this rendering-only batch). The gif shown is
therefore rendered WITHOUT strain coloring (uniform shaded beam profiles, no legend)
— an explicit, honest degradation per the format contract's gotcha 5 ("if colour
carries no data meaning, turn it off entirely"), not a fabricated E11 contour. The
same limitation affects one other idea in this batch (the extended-J hollow-tube
longeron, next).
-->

---
layout: two-cols-header
class: idea-slide
---

# D2 &middot; Extended-J hollow/cellular longeron

::left::

<div class="text-sm leading-snug">

- **What:** Pushed torsional-stiffness ratio_J beyond the Bessa 7D
  dataset's own max (7.77e-6) — hollow/cellular cross-sections (e.g. a
  hollow tube) unreachable by any solid Bessa-parametrized material.
- **Origin:** common-sense extrapolation of the Bessa family's torsion
  axis — σ_cr,nd scales with GJ, and the Bessa optimum sits at only 86%
  of max ratio_J.
- **Stats:** n=18 → 16 coil → 1 riks → 0 good<br>
  quartiles unavailable — C4's own "σ_crit=76.1 kPa" is the Stage-1 linear-buckling
  eigenvalue (loads[0]=1794N, not a Stage-2 reading); Stage 2 itself reached only 9%
  compression before stalling and produced no comparable stress of its own (see notes)<br>
  cleared: none — the "1 of 1" figure was an eigenvalue read as a decided result · novel: no
  on shape (Bessa's own section space already spans it)<br>
  best good: none (0/18 passed every criterion)
- **Verdict:** BLOCKED · UNKNOWN-NO-EVIDENCE · max-J Stage-2 convergence<br>
  Stage-1 existence supported (5/16 cleared 75.1 kPa by the same eigenvalue reading), but
  neither Stage-2 candidate ever produced a real result: D4 errored ("too many attempts"),
  C4 ran to a genuine solver stall at 9% compression with no stress reading of its own. No
  design in this family has ever produced a trustworthy Stage-2 number.

</div>

::right::

<div class="flex flex-col items-center justify-center gap-1" style="height: 420px">
  <img src="/gifs/D2_hollow_tube_D4_native.gif" style="max-height: 340px; max-width: 100%" class="rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">D4 design; native render, no strain coloring (see notes).</div>
</div>

<!--
**Input space:** twist_angle&isin;[0,&pi;]. ratio_area&isin;[1.17e-5,4.1e-3], ratio_Ixx&isin;
[1e-7,1.4e-6], ratio_Iyy&isin;[1.13e-11,1.4e-6], ratio_J&isin;[1e-6,1.5e-5] — generalized
cross-section moments, ratio_J pushed beyond the Bessa 7D dataset's own max (7.77e-6).
ratio_pitch&isin;[.25,1.5], ratio_top_diameter&isin;[0,.8] — usual per-storey pitch/taper
meaning (D006's Stage-1 screen; the Stage-2 anchors D4/C4 named in Timeline below fix these at
specific points instead). Fixed: n_longerons=3, n_storeys=1.

**Seed:** FERTILE on convergence only, not on contribution. D4, the closer near-miss (32%
strain), never actually converged ("too many attempts" mid-solve); this deck has elsewhere
(D5/H4) traced an identical Riks non-convergence to coarse arc-length settings rather than a
real physics wall, so a finer-step re-solve of D4 alone would settle whether the GJ-vs-coiling
tradeoff genuinely blocks it or was never properly tested. But resolving that question would
not make this idea novel: Bessa's own generalized cross-section space (the 7D dataset's
ratio_area/Ixx/Iyy/J columns) already spans this shape-agnostic stiffness axis abstractly —
picking a hollow/cellular shape is just one way to reach a point in that space a solid material
can't. The one thing Bessa's own generalized work never checked is local strain against the 2%
cap, so a real strain-verified point here would carry weak novelty at best. De-prioritize
relative to ideas that change the centerline, topology, or load path, not just the
cross-section shape.

**C4 forensics (raw scratch data for this design is gone, purged from
`/oscar/scratch/eaguerov/supercompressible_oracle/` since it was solved 2026-06-29; recovered
from delegation D008's own transcript in `runs/20260629T191754/debug/delegation_log.jsonl`,
still on disk): C4's exact inputs are ratio_area=.00215261, ratio_Ixx=ratio_Iyy=1.4e-6,
ratio_J=9.0e-6, ratio_pitch=.653233, ratio_top_diameter=.445325, ratio_shear_modulus=.449.**
The Stage-1 linear-buckling load was loads[0]=1794.0 N -- convert to nominal stress
(1794*1000/(&pi;*100&sup2;/4*3)) = 76.14 kPa, matching the slide's own cited "76.1 kPa" exactly.
This is an EIGENVALUE, computed before any Stage-2 solve ran. The actual Stage-2 Riks solve
ran 22 increments and stalled with max|U3|=5.896mm out of a 65.32mm mast height (0.0903
compression, matching the slide's own "mcs=.090") -- the final two increments returned an
identical displacement, the signature of a genuine solver bifurcation/stall, not a sustained
reading -- and never produced a Stage-2 stress number of its own. mls was also never measured.
So "cleared 2xBessa" was never really tested here at all: the only number that clears it is a
Stage-1 quantity, and the one real Stage-2 attempt hit a wall before producing anything to
compare.

**Timeline:** This is H5 of run `20260629T191754`, delegation D006 (Stage-1
existence), with Stage-2 Riks tests as H4 (max-J single-longeron anchor, FALSIFIED,
this same run), H6 (D4, FALSIFIED at 32% strain, delegation D007) and H7 (C4,
FALSIFIED at 9% strain, delegation D008, run `20260630T164908`'s own H1 later
reconfirms this 9%-strain failure pattern is categorical for ANY generalized-section
design, not just this one). The D4 design specifically: n_longerons=3, twist=0,
ratio_J=1.2e-5, ratio_Ixx=ratio_Iyy=1.4e-6, ratio_pitch=0.5,
ratio_top_diameter=0.445325, ratio_shear_modulus=0.449. Key finding: coilability at
J≥9.0e-6 REQUIRES max Iyy=1.4e-6 — lower-Iyy ("Set A") designs at the same J lost
coilability entirely. This idea directly set up run `20260630T164908`'s H1
(generalized-section optimum fails Stage 2 categorically, 9.23% strain) and
motivated the pivot to the Solid Circular Longeron Family (next run) as the family
that can actually pass Stage 2.

**Infra:** ODB: data/idea_odbs/20260629T191754_H5_extended_J_hollow_tube_D4/ (source:
presentation/resim/hollow_tube/riks_6b8f4808e5e2404fb8b7d33e75b28015). Same rendering
blocker as the n=5-longerons idea above: this ODB's Riks step recorded no `E` field
output (only RF/RM/U/UR), so render_odb.py's strain-coloring step cannot run;
rendered here without color as an honest degradation (format contract gotcha 5), not
fabricated. Both affected ODBs come from the same era of the resim pipeline
(2026-07-20), before `E` was added to the standard field-output request list used by
later resims.
-->

---
class: summary-slide
---

# Run `20260629T145434` — summary

<div class="text-sm leading-snug">

This run proposed two new mechanisms (pre-twist, longeron count) but completed zero oracle evaluations of its own — both hypotheses were tested in the following run.

| # | Claim | Verdict | Key evidence | Idea |
|---|---|---|---|---|
| H1 | Pre-twisted longerons (twist_angle ∈ [π/6, π]) | ⏳ | zero evals this run; resolved next run — suggestive negative, underpowered; own idea slide below | D1 |
| H2 | n_longerons &isin; &#123;4,5&#125; — path past Bessa's fixed 3-longeron design | ⏳ | zero evals this run; resolved next run as SUPPORTED (65.31–71.59 kPa, still below the 75.1 kPa floor) | D3 |

 &nbsp;&middot;&nbsp; **Cost: $9.16** (floor -- strategizer's own transcript cost unrecoverable)
</div>

<!--
Per-hypothesis detail:

- H1 (pre-twisted longerons): statement "twist_angle ∈ [π/6, π] with optimized 7D
  cross-section achieves ≥75.1 kPa/longeron"; prior 0.6; proposed 2026-06-29T15:03:13Z;
  zero evaluations this run (status stayed OPEN at run close). See idea slide below for
  full resolution (run `20260629T191754`, delegation D003, INCONCLUSIVE).
- H2 (n_longerons ∈ {4,5}): statement "n_longerons=4 or 5 with optimized 7D
  cross-section achieves ≥75.1 kPa/longeron"; prior 0.45; also zero evaluations this
  run. Resolved next run as H3 (SUPPORTED: n=4/5/6 all achieve 65.31-71.59 kPa,
  exceeding the registered 65.3 kPa prediction threshold, though not the study's
  75.1 kPa floor).
- Both hypotheses are excluded from any "oracle-wiring-check" treatment — they are
  genuine, substantive design proposals, just not yet tested when this run closed.
-->

---
layout: two-cols-header
class: idea-slide
---

# D1 &middot; Pretwisted longerons

::left::

<div class="text-sm leading-snug">

- **What:** Added a helical pre-twist (twist_angle from π/6 up to π) to each
  longeron of the standard 3-longeron mast, on top of the full 7D Bessa
  cross-section search, to see whether twisting the legs could beat the
  75.1 kPa/longeron study floor.
- **Origin:** common sense mechanistic hypothesis (not a literature
  citation) — the idea that a pre-twisted leg might exploit a shorter
  effective pitch and reach a higher coiling-mode eigenvalue.
- **Stats:** n=46 → 6 coil → 0 riks → 0 good (Stage 2 never run this campaign)
  p50/p90/p100 — σ_crit (coilable only): 7.3/43.6/65.3 · mcs: not tracked · mls: not tracked
  (every coilable design at or below the twist=0 baseline, 65.31 kPa)
  cleared: none (0 decided) &middot; novel: untested — Stage 2 never ran this campaign
  best good: none (0/46 passed every criterion)
- **Verdict:** INCONCLUSIVE · DEAD-END<br>
  The mechanism does not work — pre-twist destroys
  coilability rather than helping it. The registered test technically
  fell short of its own ≥80-eval bar (a license-server outage killed 26 of
  the planned runs), so the formal status is INCONCLUSIVE, not FALSIFIED,
  but the completed 46 evals point the same direction with no ambiguity:
  this is a dead end, not a promising family.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/gifs/D1_pretwisted_negative_native.gif" class="max-h-72 rounded shadow-lg" />
  <div class="text-xs opacity-60 mt-2 px-4 text-center">D003's coilable design (twist_angle=76&deg;), re-run fresh — see notes.</div>
</div>

<!--
**Chart provenance:** re-run fresh against the same generalized-cross-section+twist Stage-1
script, since the original 2026-06-29 delegation's ODBs no longer exist on scratch (ephemeral
sandbox cleanup, not a fabrication) — undeformed mesh, then its actual lowest mode.

**Input space:** twist_angle&isin;[0,&pi;]. ratio_area&isin;[1.17e-5,4.1e-3], ratio_Ixx&isin;
[1e-7,1.4e-6], ratio_Iyy&isin;[1e-7,1.4e-6], ratio_J&isin;[1e-6,7.77e-6] — generalized
cross-section moments (Bessa's own 7D parametrization). ratio_pitch&isin;[.25,1.5],
ratio_top_diameter&isin;[0,.8], ratio_shear_modulus&isin;[.334,.45]. Fixed: n_longerons=3.

**Seed:** BARREN — technically underpowered (46/80 evals, license outage) but the trend among
coilable designs is monotonically decreasing with twist (30°→52.93 kPa, 90°→15.69 kPa, then
zero coilable beyond that), and a separately-powered test of twist on a different cross-section
family found the same direction — completing the missing 34 evals would not change the sign.

**Deferred:** Full status history: prior 0.6 → 0.35 after the literature-review
downgrade → 0.25 after a second literature check → briefly closed FALSIFIED by the
strategizer, then the validator flagged that the registered falsification criterion
required ≥80 evaluations and only 46 completed (26 Abaqus runs failed to
license-server errors during delegation D003) → corrected to INCONCLUSIVE per the
study's own charter §3 (an inadequate test cannot force a closed FALSIFIED verdict,
however suggestive).

**Timeline:** Stats-migration note (2026-08-04): the twist-angle trend among coilable
designs is monotonically decreasing (30°&rarr;52.93 kPa, 90°&rarr;15.69 kPa, all
coilable=0 beyond that) — preserved here since a single quartile triplet doesn't show
a trend. A related but distinct idea (twist applied to a DIFFERENT, non-Bessa
cross-section family, "twisted-strip beam") was separately properly-powered this
session (2026-08-04, 3-phase zoom) and reached a real but still-far-short-of-target
14.4% of its own family's target — consistent with twist not being a productive
lever in general, though that's a different cross-section, not a re-test of this
exact idea. This is H1 of run `20260629T145434` (proposed with zero evals that run —
the actual 46-eval anchor sweep + LHS ran the following run, `20260629T191754`, as
that run's own H1, delegation D003). Per this deck's rule 1 ("one slide per genuinely
new idea, earned at the run where it first appears"), the idea's full slide is placed
here at its origination run; the numbers above are pulled forward from the run that
actually resolved it, exactly as the tapered-longeron format-example slide does.
Physical mechanism (per the run's own D002 literature review, Drozdov-Rabin 2000 +
Gomez-Lauga 2024): path-twist has no theoretical reason to raise the critical
buckling load for a near-circular cross-section (ν=I2/I1≈1); Gomez-Lauga's own
analysis shows helical path-twist actually REDUCES effective bending stiffness. This
is consistent with what the sweep found.

**Infra:** No ODB exists for this family because no design was ever
coilable+competitive enough to be worth resimulating and archiving — this is one of
only two ideas in the whole 25-idea "genuinely new" list with no ODB by design, not
by omission (the other is the elliptical cross-section, later this same run-range).
The tape-spring idea was a third member of this group while its run was still
executing; it has since closed with its own ODB archived — see its own slide,
elsewhere in this deck.
-->

---
layout: end
---

# Backlog & full evidence

This deck is now the primary provenance record for the study — every genuinely new
idea and every run's own summary, anti-chronological. `PROBLEM_STATEMENT.md`'s own
"Backlog from previous runs" section still tracks open threads not yet resolved by a
later run; for full per-hypothesis detail beyond what's in any slide's speaker notes,
see `runs/*/debug/strategizer_notes/hypotheses.json`.

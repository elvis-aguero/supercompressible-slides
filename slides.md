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
DECK FORMAT CONTRACT (advisor-specified, agreed 2026-07-29) — durable
reference for any future edit session. This comment is not a slide; it is
not meant to render. Read this before adding or editing any slide.
============================================================================

1. ONE SLIDE PER GENUINELY NEW IDEA.
   A new full slide is earned only by a genuinely new design idea that has
   never had its own slide before. A hypothesis that is just a minor
   resizing/retry/refinement of an idea that ALREADY got its own slide in an
   earlier run does NOT get a new slide — it folds into that later run's
   run-summary slide instead, as one bullet point (one line, "idea X:
   retried/refined, result Y"), with any detailed stats for that bullet
   living in the run-summary slide's own speaker notes, not its main body.

2. H1-AS-ORACLE-WIRING-CHECK IS EXCLUDED FROM THE DECK, ENTIRELY, ALWAYS.
   Several runs' H1 is not a design hypothesis at all — it is the run's
   one-time oracle-wiring sanity check (re-solve a known anchor, confirm the
   simulator reproduces it within tolerance; see PROBLEM_STATEMENT.md's
   "Confirmed anchors" policy). That kind of H1 gets NO slide, NO
   run-summary bullet, and NO speaker-note mention anywhere in this deck,
   ever — it is infrastructure self-check, not a research result. (This
   does NOT mean every hypothesis literally numbered "H1" is excluded —
   plenty of runs' H1 is a real, substantive design test. Check what the
   hypothesis actually claims, not its number.)

3. BULLET TEMPLATE AND ORDER (exactly 4 bullets, left column of a
   two-column layout — no more prose on the main slide):
     (a) What      — precisely what was tried.
     (b) Origin    — where the idea came from: a real, specific citation, or
                      the honest "common sense / resize of family X" if
                      that's actually what it was. Never fabricate a
                      literature grounding that isn't real.
     (c) Stats     — how many designs were evaluated / how many feasible,
                      plus the key physical numbers (σ_cr,nd, compression
                      achieved, strain, slenderness, etc.).
     (d) Verdict   — one direct sentence: did the mechanism work as
                      hypothesized; is this a good idea; confirmed valid /
                      falsified / inconclusive, and briefly why. State
                      negative results as plainly and confidently as
                      positive ones — do not hedge a clean falsification
                      into vagueness.
   Everything else — reasoning, caveats, provenance history, full parameter
   dumps, technical asides — goes in the slide's Slidev speaker notes (an
   HTML comment immediately after the slide content, before the next
   `---`), never in the slide body. (Do not write that comment's own open/
   close delimiters literally inside THIS contract comment — a literal
   closing sequence anywhere in this text terminates the contract comment
   itself early, dumping the rest of it as visible text on whichever slide
   holds it. This exact bug shipped once, 2026-07-31 — found by rendering
   the actual cover slide, not by reading the source.)

   HARD CHARACTER BUDGET, measured not guessed (2026-07-31): this deck's
   canvas is 980x552px. Rendered headlessly (playwright, real DOM, real
   font metrics) at `layout: two-cols-header` + a `text-sm leading-snug`
   wrapper on the bullet list, the left column has 416px of usable height
   below the header, at a measured line-height of 25.2px -> a hard ceiling
   of ~16.5 lines total across all 4 bullets before the column overflows
   the canvas (verified: content taller than this clips silently, no
   scroll, no auto-shrink — Slidev does not fit content to the frame).
   Measured wrap rate in the deck's actual body font at this size is ~62
   characters/line in the ~419px-wide left column. Target ~14-15 lines
   total (small margin under the 16.5-line ceiling for cross-browser font
   rendering variance) => a working budget of ~190 characters PER BULLET,
   INCLUDING the bold label ("**Stats:** "). This is a target, not a
   license — a bullet at exactly 190 characters with 3 other bullets also
   at 190 will overflow; distribute the ~14-15 line total across the 4
   bullets by how much each one actually needs, and cut real content into
   speaker notes rather than let any slide clip. Re-verify after edits: the
   only trustworthy check is rendering the built deck and measuring
   `scrollHeight` vs the 552px canvas — reading the markdown is not
   sufficient, wrapping depends on real font metrics.

4. GIF REQUIREMENT: NATIVE ABAQUS/CAE VIEWER EXPORT ONLY.
   The right half of the two-column layout is one image or GIF exported
   NATIVELY from Abaqus/CAE's own Viewer/visualization module
   (session.viewports[...].odbDisplay, session.printToFile per frame) —
   never the matplotlib/COORD-field-reconstruction pipeline used elsewhere
   in this repo (presentation/render/extract_odb.py + render_frames.py).
   The point is source truth directly from the simulation tool, with no
   custom re-derivation of geometry between the ODB and the image. The
   renderer lives at presentation/render/render_odb.py. Known gotchas,
   solved once and documented here so nobody has to rediscover them a third
   time:
     1. `vp.setValues(displayedObject=odb)` raises "TypeError:
        displayedObject; found Odb, expecting StubType" unless
        `from viewerModules import *` is imported first — that import
        registers the visualization kernel plugin that recognizes an Odb as
        a displayable stub. Opening the odb and reading data from it works
        fine without this import; only *displaying* it needs it.
     2. This study's rings have NO solid geometry at all — each is a 0-D
        reference point (see PROBLEM_STATEMENT.md's Simulator behaviour
        section) — and the model's `ANALYTICAL_SURF` instance is an
        oversized, idealized rigid plane used only for the Riks boundary
        condition/coupling, not physical ring geometry; left visible it
        fills the frame and hides the actual longerons. Fix: restrict the
        display group to the actual structural (beam-element) instance via
        `displayGroupOdbToolset.LeafFromPartInstance`. We also checked
        whether the model's bare reference-point nodes could stand in as an
        honest "here's the ring" marker — they can't: they sit well outside
        the mast's own z-extent (load-application points, not ring-plane
        markers), so we don't render them. If a future ODB genuinely has no
        faithful way to show ring position, say so in the speaker notes
        rather than fabricate ring geometry that isn't in the simulation.
     3. `renderStyle=FEATURE` is not a valid Abaqus constant — use `SHADED`.
     4. B31 beam elements render as bare centerline wireframe unless
        `vp.odbDisplay.basicOptions.setValues(renderBeamProfiles=ON)` is
        set — note `basicOptions`, not `commonOptions`.
     5. Colour the model by a physically meaningful field, not an
        unexplained default — this study lives or dies on local bending
        strain, so contour on `E`, component `E11`
        (`setPrimaryVariable(variableLabel='E',
        outputPosition=INTEGRATION_POINT, refinement=(COMPONENT, 'E11'))`),
        with the legend left ON (`viewportAnnotationOptions(legend=ON)`). If
        colour carries no data meaning, turn it off entirely — never leave
        it unexplained. CONFIRMED on a second family (2026-07-30, the tape-spring
        S4R shell ODB, `data/idea_odbs/20260730T020245_H2_tape_spring/`):
        that ODB has no `E` field output at all — only `LE` (plus `S`,
        RF/RM/U/UR, COORD, contact vars, since self-contact is enabled for
        this family). The script's existing try-E-else-LE fallback (already
        built for the pin-jointed tensegrity truss, which has no bending
        strain field either) picked `LE11` automatically with zero code
        change and rendered correctly. So this is not strictly a
        beam-vs-shell split — it's whichever field the family's own
        pre/post-processor actually requested — but it's now exercised by
        two structurally different families, which is why the fallback
        stays generic (probe the ODB's own fieldOutputs, never hardcode by
        element type). If colour carries no data meaning at all, turn it
        off entirely — never leave an unexplained colour on a research
        slide.
     6. Camera: Abaqus's generic `session.views['Iso']` preset does NOT
        reliably give a usable angle for this mast geometry (it can render
        nearly edge-on). Compute an explicit camera from the structural
        instance's own bounding box — an elevated 3/4 view (elev=22°,
        azim=-50°, z-up, parallel projection) matches the look of this
        deck's existing matplotlib gifs and reliably reads the rings as
        near-horizontal arcs. Held fixed across all frames (fit once on the
        first/undeformed frame) so any visible rotation in the gif is the
        structure's own real coiling motion, not an artificial orbiting
        camera.
     7. Legend placement/size: the default legend renders bottom-left-of-
        center at full size and overlaps the model. Move it clear of the
        geometry into the top-right corner with
        `viewportAnnotationOptions.setValues(legendPosition=(x, y))` (x/y
        are percent of the viewport; tune per canvas aspect so the box
        doesn't clip off the edge — e.g. (60, 97) worked for a 2:3 portrait
        canvas) and shrink it to fit
        (`contourOptions.setValues(numIntervals=6)`, a smaller
        `legendFont`, `legendNumberFormat=SCIENTIFIC`,
        `legendDecimalPlaces=2`). Trap: several of these `setValues()` calls
        succeed silently even when a value/kwarg is subtly wrong for the
        current view — a call not raising is not proof the pixels moved.
        Always re-render and LOOK at the PNG after any legend/camera tweak.
     8. Portrait canvas: this sits in the right half of a two-column slide,
        and the mast is tall and thin, so render portrait (~2:3
        width:height, e.g. 600x900), not square — set the viewport's own
        `width`/`height` (matching the target aspect) BEFORE calling
        `fitView()`, and set `session.pngOptions.setValues(imageSize=...)`
        to the same aspect, or Abaqus letterboxes/distorts the frame.
     9. Ring annotation: this study's rings have NO simulated geometry to
        natively render (gotcha 2) — but we DO know which longeron end
        nodes are each ring's joints (identified once from the undeformed
        mesh: the nodes at the structural instance's own z-min/z-max). A
        smooth circle drawn through those joints' CURRENT positions is an
        honest schematic, not fabricated output, because every point it
        passes through is a real, currently-solved node position. Draw it
        entirely OUTSIDE Abaqus, in a PIL post-process pass over each
        exported PNG (never mixed into the ODB's own displayGroup), as a
        thin DASHED, semi-transparent, neutral-gray circle with an explicit
        "ring (schematic)" text label — visually nothing like the solid
        shaded/strain-colored beam profiles, so it can never be mistaken for
        simulated output. To make the overlay line up with Abaqus's own
        render, replay its camera: read back
        `vp.view.width`/`.cameraPosition`/`.cameraTarget`/`.cameraUpVector`
        (readable attributes after any view change, incl. after
        `fitView()`) and build a standard orthographic camera basis
        (forward = normalize(target-position); right =
        normalize(cross(forward, upVector)); screenUp = cross(right,
        forward)).
        — **A WRONG FIRST ATTEMPT, recorded precisely so it isn't repeated:**
        the first version computed each ring's 3-D circle ONCE outside the
        frame loop, from `inst.nodes[i].coordinates`, then reused that same
        static geometry for every output frame. `node.coordinates` is
        ALWAYS the UNDEFORMED mesh position — calling
        `vp.odbDisplay.setFrame(...)` changes what Abaqus's viewport
        DISPLAYS, it does not change what a direct node-coordinate query
        returns. Result: the ring silently stayed frozen at the structure's
        initial position for the whole animation while the real,
        natively-rendered longeron geometry visibly coiled and compressed —
        invisible in early frames (little deformation yet), obviously wrong
        by mid/late compression, and exactly the kind of bug that looks fine
        in a spot-check of frame 0 and wrong to a user looking at the actual
        gif. THE FIX: read each frame's `fieldOutputs['COORD']` (current
        nodal position — the same technique used elsewhere in this study's
        ODB analyses) for the joint node labels, INSIDE the per-frame loop,
        and refit the ring's center/in-plane orientation/radius from those
        current positions every single frame (a best-fit circle through the
        current joint points via their centroid + a normal from two edge
        vectors, not a rigid horizontal circle — a ring can translate,
        rotate and tilt between frames). Do not assume which ring (if
        either) is fixed: check via COORD. In this model the bottom ring
        turned out to stay exactly fixed (a Riks BC artifact of this
        particular model, not a general rule) while the top ring
        translates, rotates, and its z can cross past the bottom ring's
        plane by full compression — both are still recomputed from COORD
        every frame regardless, on principle, not because we assumed one
        was static. General rule worth keeping: for ANY animated overlay
        that isn't Abaqus's own native per-frame render, recompute its
        geometry from field-output data inside the frame loop — never from
        a node/mesh attribute read once outside it.
   No-winner convention: always show a faithful native-Abaqus image of a
   TYPICAL (not necessarily the single best) design from that idea's
   search — never leave an empty image slot for a negative result.

5. FULL-REBUILD ORDERING: anti-chronological, most recent run first. Done.

6. LAYOUT DIRECTIVE: `layout: two-cols-header`, NOT `layout: two-cols`.
   Under plain `two-cols`, the `# Title` line lives inside the split and
   only spans the LEFT column's half-width — a real bug found 2026-07-31
   (title rendered squeezed into ~45% of the slide). `two-cols-header`
   gives the title its own full-width row above the split; the body below
   still needs explicit `::left::` then `::right::` markers (unlike plain
   `two-cols`, which treats everything before `::right::` as the left
   column implicitly). Wrap the left column's bullet list in
   `<div class="text-sm leading-snug">...</div>` — this is the font size
   the character budget in rule 3 is calibrated against; do not silently
   change the font size class without re-measuring the budget (see rule 3).
============================================================================
-->

# Supercompressible Metamaterial
## Full provenance, in order

Every idea, every run, in the order it actually happened — 23 runs, 25 genuinely new ideas tested

<div class="text-sm opacity-70 mt-8">
No mechanics background assumed — every idea described in plain terms
</div>

---
layout: two-cols-header
class: baseline-slide
---

# The Bessa baseline — what a valid design looks like

::left::

<div class="text-sm leading-snug">

Every target in this deck is stated as a multiple of this design — the reference
point for what "good" looks like, before the anti-chronological history below.

- **Design:** circular longeron cross-section, 3 longerons, 1 storey — the best
  feasible point Bessa, Glowacki &amp; Houlder (2019) found in that family.
- **Geometry:** ratio_d=0.02005, ratio_pitch=0.25, ratio_top_diameter=0.2505.
- **Result:** &sigma;_cr,nd=0.1306 kPa/longeron, mls=0.0198 (inside the 2% cap),
  fully reversible coiling.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/bessa_baseline_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Bessa point, re-solved 2026-07-31 for this deck.</div>
</div>

<!--
Re-solved 2026-07-31 via the exact same two-stage NO-CONTACT pipeline
test_nocontact_anchors.py uses for this anchor (energy-free StaticRiksStep,
supercompressible_lin_buckle_pretwist.py -> supercompressible_riks_pretwist.py),
specifically to render a native-Abaqus gif for this lead slide -- no ODB for this
exact point existed in the permanent archive before now. Solved sigma_crit=0.1306
kPa (expected 0.1306, exact match to 4 sig figs), mls=0.019795. ODB archived at
data/idea_odbs/bessa_baseline/ (PROVENANCE.txt has full inputs and the solve
recipe). See PROBLEM_STATEMENT.md lines 133-137 for the original definition of
this point and why it's the study's reference floor.

Deliberately NOT following the 4-bullet What/Origin/Stats/Verdict idea-slide
template -- this is not a hypothesis this study tested, it's an external
reference point, so there is no verdict to render. Per explicit user instruction:
describe the design and show the gif, no reasoning/justification needed.
-->

---
layout: two-cols-header
class: idea-slide
---

# Thin-walled open circular-arc ("tape-spring") longeron

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the solid B31 longeron with a thin-walled, open-arc S4R
  **shell** section, hypothesizing a *localized elastic fold* (`t/2R_tape`)
  could escape the mast-scale coiling curvature capping every beam family.
- **Origin:** Calladine inextensional-fold theory + Seffen–Pellegrino
  tape-spring mechanics (real citation) — first shell-longeron capability
  built in this study.
- **Stats:** 407 evals, 4 corridors, 0/406 feasible. Best mesh-confirmed
  strain 0.027053 (1.35× cap) at σ_cr,nd=0.634 kPa; 0/7 checked sections
  transversely flattened.
- **Verdict:** FALSIFIED by direct kinematic observation — no folded regime
  exists here. Strain tracks extreme-fibre bending (ratio 0.946), not the
  fold scale (2.566). Baseline stays 0.7704 kPa (`run17_rectangle`).


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/tape_spring_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
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
  slenderness floor was merely a simulator-validity limit rather than a
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

# Run `20260730T020245` — summary

<div class="text-sm leading-snug">

- H3: RIVAL — strain set by global coiling curvature × extreme-fibre distance (κ_coil·c), not fold localization → INCONCLUSIVE (magnitude ratio 0.946 and kinematics favour it, but both registered correlation clauses miss: ρ=0.358 vs. 0.5 bar; fold-scale law fits better, r=0.826 vs. 0.545)
- H4: metric-comparability gate for shell λ_cr → INCONCLUSIVE (imperfection-amplitude sweep not executable — hardcoded module constant, not a design param; off-ledger knockdown 0.646–1.113, not uniformly ≥0.8 → every shell σ_crit is an upper bound only)
- H5: wide, shallow ribbon (arc_depth≤0.5mm) escapes the B31 slenderness floor via shells → FALSIFIED, folds into the tape-spring slide (kappa·arc_depth underpredicts strain ~13.5×; local plate/free-edge instability preempts coiling in 60% of designs)
- H6: true strain minimum lies in the unsampled intermediate corridor (arc_depth 0.6–1.8mm) → FALSIFIED, folds into the tape-spring slide (min converged mls=0.0464, between both flanks; 65% local-mode preemption)
- H7: deep-corridor near-misses partly a measurement artifact, one clears 2% once corrected → FALSIFIED, folds into the tape-spring slide (correction bidirectional: one design +9%, one −25%; none reached the cap)
- H8: dense local sweep around the closest near-miss (design C) for ≤2% → FALSIFIED, folds into the tape-spring slide (51-eval LHS + mesh confirmation; best mesh-confirmed mls=0.027053, still 1.35× the cap)

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
class: summary-slide
---

# Run `20260729T012952` — summary

<div class="text-sm leading-snug">

- H2: split the single-ring chiral brace's compliance into N≥3 parallel, independent circumferential ligaments → OPEN, deprioritized — folds into the chiral-brace idea's slide (literature review found only a weak N^-1/3 scaling at best, and one directly relevant corpus finding suggesting identical parallel elements reach their strain threshold simultaneously, not distributed — the opposite of the needed mechanism; no delegation ever tested it)
- H3: distributing bistable arch segments at multiple locations along the full longeron (vs. one segment near the bottom ring) lowers peak local strain further → INCONCLUSIVE — folds into the bistable-arch idea's slide (confounded: the required joint-discontinuity strain-underestimation check via validation/warping_check, at each segment transition, was never performed, and multi-segment configs have MORE such transition joints than the single-segment precedent)
- H4: a graded/staggered chain of K=3 non-identical bistable arch segments lowers peak local strain further, per Palathingal-Ananthasuresh sizing → FALSIFIED — folds into the bistable-arch idea's slide (reversal-count evidence does not support the staggering-specific mechanism; reversal signals cluster at the segment nearest the bottom ring at every K, consistent with curvature demand being set by the boundary condition itself, not by staggering)

</div>

<!--
Run stats: GATED, evals_used=93. H1 (oracle re-confirm, -0.0062% deviation)
excluded from this deck entirely per the format contract.

This is the smallest-budget run in this batch (93 evals) and produced no new
idea — all three substantive hypotheses are refinements of ideas that
already have their own slides (chiral-brace, bistable-arch), consistent with
the study's search space converging on a small number of well-characterized
mechanism families by this point.

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

- H2: peak local bending strain (mls) at high σ is a near-invariant kinematic property of coiling, only reducible by a compound (aperiodic-bracing + strain-clearing) mechanism → FALSIFIED (conjunctive claim; the bracing-lowers-strain conjunct holds, but the strain-clears-2%-wall conjunct is decisively contradicted — 0/280 designs clear the wall across 3 campaigns)
- H3: a quasi-periodic (aperiodic, golden-ratio-derived spacing), multi-level inter-longeron elastic bracing network beats the single periodic ring/helix brace already exhausted → FALSIFIED — folds into the chiral-brace idea's slide (280-eval, 3-campaign investigation; aperiodic bracing genuinely lowers peak per-member ligament strain at matched material, e.g. 6.03% vs. 13.92% periodic, but the mcs≥0.80 and ligament-strain≤2% regions are disjoint, zero overlap)
- H4: across every family tried, peak local bending strain in a continuously-loaded elastic member is structurally coupled to that member's cross-sectional size/stiffness → SUPPORTED (positive size-strain relationship confirmed WITHIN each of 3 independent sub-campaigns, not just pooled: ρ=0.534/0.512/0.690, all clearing the pre-registered ρ>0.5, p<0.01 bar)
- H5: tapering the brace ligament along its own length relieves ligament strain the same way host-longeron tapering decouples area from strain → INCONCLUSIVE — folds into the chiral-brace idea's slide (a 10-point diagnostic, not the registered full CEI-BO campaign, found a worsening trade-off: strain fell only 14.3% while σ fell 22.4% over the same taper range)

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
layout: two-cols-header
class: idea-slide
---

# Single bistable shallow-arch snap segment near the ring joint

::left::

<div class="text-sm leading-snug">

- **What:** Spliced one bistable, shallow-arched snap-through segment near
  the bottom ring, jointly re-optimized with the base cross-section, to
  reinvest local-strain headroom into higher σ_cr,nd than 0.7704 kPa.
- **Origin:** elastic-instability/bistable-mechanism metamaterials
  literature; follow-on to a same-run hypothesis whose single-arch strain
  cut (mean ~7%, max 12.3%) fell short of a pre-registered 20% bar.
- **Stats:** initial reported design — σ_cr,nd=0.850864 kPa, max_local_strain
  =0.0196 (just inside the 2% wall), all criteria nominally met at gating.
- **Verdict:** SUPPORTED at gate time, then RETRACTED. A continuum submodel
  of the arch-to-longeron joint (control-tested against the Bessa point)
  found real local strain 2.7×+ over the beam-reported value, still rising
  with mesh refinement — likely exceeds the 2% criterion. Baseline stays
  0.7704 kPa (`run17_rectangle`).


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/bistable_arch_headline_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
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

# Run `20260727T011550` — summary

- H2: a bistable shallow-arch snap-through segment near the bottom ring lowers peak local bending strain (mls) by ≥20% relative, at matched compression → FALSIFIED as registered (real effect found — 16/24 feasible points, max 12.3%, mean ~7% reduction — but short of the pre-registered 20% bar)
- H3: mls is a near-invariant kinematic property of beam-type coiling, independent of cross-section or added compliant segments → SUPPORTED at the registered bar (same 24-point grid; no design cleared the 20% refutation threshold)
- H4: reinvest the real mls headroom from H2 via joint cross-section+arch re-optimization to beat 0.7704 kPa → SUPPORTED, then RETRACTED post-hoc → own slide, this deck
- H5: a second, independently-snapping arch at the top ring further lowers mls → FALSIFIED on its stated mechanism (the top segment never actually snaps; folds into H4's slide, same design point)

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
class: summary-slide
---

# Run `20260724T012622` — summary

- H2: continuously rotating the rectangle's cross-section principal axes along its own arc-length ("twisted-strip" beam) → INCONCLUSIVE — folds into `run17_rectangle`'s slide (existence-search prong stopped at 43/~100-110 planned evals, 1/43 feasible, short of its own pre-registered power bar)
- H3: is the local-bending-strain wall a purely kinematic property of coiling's total curvature demand, not a fixable cross-section problem? → SUPPORTED (8-point matched-pair twist sweep 0-120° at the winning rectangle: mls only rises, 1.99%→5.01%, with twist; σ stays twist-invariant, <0.07% drift)
- H4: hierarchically self-similar ("fractal-order") longeron centerline perturbation lowers peak local bending strain → FALSIFIED — folds into the meander/serpentine idea's slide (matched quad, order 0-3, mls flat-to-slightly-increasing across every order)
- H5: swap the single-ring chiral brace's planform for a true helical coil ("chiral_helix") → INCONCLUSIVE — folds into the chiral-brace idea's slide (213 evals across 4 delegations; at the exact seed producing the old disputed 1.2457 kPa design, ligament strain falls from 9.05% to 6.00%, still 3x over the 2% limit, and not this run's own closest approach)

<!--
Run stats: all-Sonnet, 12h, GATED, evals_used=272, $26.83. Baseline unchanged
at 0.7704 kPa. H1 (oracle re-confirm, bit-consistent re-solve) excluded from
this deck entirely per the format contract.

H2 detail: existence-search prong self-corrected from an initial over-eager
FALSIFIED back to INCONCLUSIVE once the validator flagged the campaign as
short of its own pre-registered power bar.

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
layout: two-cols-header
class: idea-slide
---

# Chained mild pre-curved ("sub-bistable") arch-segment longeron

::left::

<div class="text-sm leading-snug">

- **What:** Chain of N alternating-sign pre-curved shallow-arch segments,
  rise-to-thickness ratio (Q) kept *below* the bistability floor (Q≈2.31) —
  mild repeating curvature, not genuine snap-through.
- **Origin:** follow-up to the same run's H2 (*true* bistable, Q≥2.31
  chain), which hit a Riks numerical wall in 71/72 cases; asks whether
  backing off avoids the wall while still beating baseline.
- **Stats:** one confirmed counterexample (circular=11, 3 segments,
  arch_rise_ratio=0.10): σ_cr,nd=0.7765 kPa, mcs=1.0325, mls=0.0194,
  slenderness=10.25, ring-passthrough clear.
- **Verdict:** falsified as an absence claim — one genuine 5-criteria
  counterexample beats the 0.7704 kPa baseline. Valid, but a mild curvature
  perturbation, not the true bistable mechanism originally proposed.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/chained_bistable_arch_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Full context:

- Registered as H3 of run `20260723T010834` (GATED, evals_used=206). H1 of
  this run is the oracle-wiring sanity check and is excluded from this deck
  entirely, per the format contract. H2 (chain of TRUE bistable, Q>=2.31,
  segments) is a refinement of this same chained-arch idea and is FALSIFIED
  on a numerical-convergence wall (72 evals, 23/72 coilable, only 1/72
  reaching mcs>=0.80, and that one a near-degenerate cross-section at
  sigma=2.97e-5 kPa — not a real candidate); it does not get its own slide,
  see this run's summary slide.
- 0.7765 kPa (this idea) is marginally above the 0.7704 kPa rectangle
  baseline (+0.8%) — a real but very thin margin, not a decisive win.
- IMPORTANT — continuum-verification caveat: per PROBLEM_STATEMENT.md's
  "More background" section and `bo/confirmed_anchors.json`'s `_README`,
  only `run17_rectangle` has been re-checked with the decisive cut-distance
  continuum-FE convergence study (Round 6) and reconfirmed valid (~1.05x
  local-strain amplification, well inside the 2% ceiling). `chained_arch`
  (this design) was explicitly NOT re-checked with that method — its
  0.019394 beam-reported max_local_strain (a hair under the 2% wall) has
  never been independently verified against a continuum joint model. Treat
  it as an unconfirmed-but-not-yet-falsified counterexample, not a
  fully-cleared "beats baseline" claim, until it receives the same
  treatment run17_rectangle got.
- ODB: `data/idea_odbs/20260723T010834_H3_chained_bistable_arch/` (archived
  from scratch riks_adedcff397644c99a451e61cb6127f1b). Rendered fresh this
  session; no native gif existed for this idea before (an old-pipeline
  gif with a similar name does not exist under this slug — `bistable_winner.gif`
  and `dual_arch_winner.gif` in the gifs directory belong to the different,
  later single-arch idea below, not this chained-segment idea).
-->

---
class: summary-slide
---

# Run `20260723T010834` — summary

- H2: chain of true-bistable (Q≥2.31) snap-through arch segments → FALSIFIED — a solve-completion wall, not a strain wall (72 evals, 23/72 coilable, only 1/72 reached mcs≥0.80, and that one a near-degenerate, physically meaningless cross-section)
- H3: chained mild pre-curved (sub-bistable) arch segments → FALSIFIED as an absence claim, but a real counterexample was found → own slide, this deck

<!--
Run stats: GATED, evals_used=206. H1 (oracle-wiring re-confirm) excluded from
this deck entirely per the format contract.

H2 detail: mechanistically-explained wall, not noise — the same Riks-stall
failure (arc-length solver cannot traverse the sequential snap-through
equilibrium path) recurs across n_segments=2..6 and across 2+ orders of
magnitude in cross-section size, matching a priori literature risk flagged
during the run's own literature review (arXiv:2010.07850: snap-through is
rate-dependent/delayed-bifurcation even in the ideal quasi-static elastic
case). 6 matched energy-free/stabilized retry pairs in the data: stabilization
never rescued convergence, made mcs worse or negligibly different every time.
The one "success" (mcs>=0.80) is a near-degenerate cross-section
(ratio_a=0.004616, ratio_b=0.00059) at sigma=2.97e-5 kPa, ~26,000x below the
0.7704 kPa target — not a real candidate.

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

# Doubly-symmetric cruciform/I-beam cross-section

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
- **Stats:** 91 evaluated (Monte-Carlo-verified design box), **0/91 feasible**
  — max compressive strain and max local strain are strongly positively
  correlated (r=0.76) even in the highest-mcs subset.
- **Verdict:** falsified. This is not a sampling-coverage gap: the
  correlation is consistent with classical flexural-torsional theory rather
  than a search-power shortfall, so the cross-section family itself does not
  escape the sigma/strain trade-off.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/cruciform_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Full context:

- Registered as H2 of run `20260721T201733` (all-Sonnet, 14h, GATED,
  evals_used=867, $59.50 for the whole run). Same run's H1 (properly-powered
  128-eval re-test of the tapered-longeron family, best feasible 0.362763 kPa
  = 2.78x Bessa but only 47% of the 0.7704 kPa rectangle baseline) is a
  refinement of an idea that already has its own slide from an earlier run,
  so it is NOT repeated here — see this run's own summary slide for its
  one-line status.
- ODB used for this render: `data/idea_odbs/20260721T201733_H2_cruciform_ibeam/`
  (archived from scratch riks_de8c7e06e10b40e2a80fd6146e69eeee). Best
  *infeasible* sigma found in the campaign was ~0.68 kPa, below the 0.7704 kPa
  baseline even before the strain-correlation problem is considered.
- Do not re-attempt this exact cruciform/I-beam family expecting a different
  result: PROBLEM_STATEMENT.md explicitly lists it as a settled null result
  (0/91 feasible, r=0.76 mcs/mls correlation even in the best-mcs subset).
- GIF: native Abaqus/CAE Viewer render via `presentation/render/render_odb.py`
  (E11 strain coloring, top-right legend, schematic dashed-circle ring
  overlay recomputed from COORD every frame, portrait 480-wide canvas), same
  pipeline as the rest of this deck. Rendered fresh this session directly
  from the archived ODB (no native gif existed for this idea before).
-->

---
class: summary-slide
---

# Run `20260721T201733` — summary

<div class="text-sm leading-snug">

- H1: properly-powered 128-eval re-test of the smoothly-tapered longeron family → FALSIFIED vs. the 0.7704 kPa baseline (best 0.362763 kPa = 2.78x Bessa, itself a valid standalone design, but only 47% of baseline, flat trend)
- H2: doubly-symmetric cruciform/I-beam cross-section → FALSIFIED (own slide, this deck)
- H3: continuous elastic chiral/auxetic bracing at a fixed host anchor → INCONCLUSIVE (mechanism genuinely elastic, but only 2/120 evals Riks-converged near the boundary — underpowered, not contradicted)
- H4: jointly optimize host cross-section + chiral brace together → SUPPORTED on its literally-registered (host-only) criteria, but NOT citable as a result — every winning design's brace ligament strains 7.7-9.1%, the same apples-to-apples violation as tensegrity
- H5: bistable snap-through segment near the ring joints (proposal) → OPEN, ran out of budget this run (tested the following run as its own idea)
- H6: among H4's numerically-passing designs, does any also keep the brace ligament elastic? → FALSIFIED for this exact topology, properly powered (440 evals across 3 campaigns); closest miss σ=0.336844 kPa (2.58x Bessa) at ligament strain 2.15%, just 0.15 points over the 2% limit
- H7: does n_longerons materially change per-longeron σ? → SUPPORTED (confirms this run's oracle carries no n_longerons scaling bug)
- H8: longer/more convoluted multi-loop chiral-brace ligament path → FALSIFIED (349 evals, only 1/349 meets all 6 criteria at 19% of baseline)

</div>

<!--
Run stats: all-Sonnet, 14h, GATED, evals_used=867, $59.50. Baseline unchanged
at 0.7704 kPa this run. Explicitly steered toward genuinely novel mechanisms
rather than resizing the known rectangle.

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

<div class="text-xs opacity-50 mb-2">Run 20260718T132852</div>

# Class-1 tensegrity strut-and-cable longeron replacement

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the bending longeron with a pin-jointed, prestressed
  Class-1 tensegrity assembly — stiffness from prestress/geometry, not
  beam bending.
- **Origin:** Amendola et al. (2018) tensegrity prestress-stiffness theory,
  contrasted with Meng (2012)/Sorrentino (2021) on bending-family
  strain-stiffness coupling.
- **Stats:** &sigma;_cr,nd=220.89 kPa (287&times; the 0.7704 kPa baseline),
  fully feasible; re-verified via direct ODB mode-1 extraction
  (6&times;10<sup>-10</sup> rad match).
- **Verdict:** SUPPORTED at face value (largest &sigma;_cr,nd in the study)
  but demoted by the apples-to-apples criterion — pin-jointed/prestress
  isn't comparable elastic bending, real but uncounted.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/tensegrity_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Colour = LE11 (axial log strain) — this pure truss/cable model has no beam bending strain field.</div>
</div>

<!--
Full context:

- This is hypothesis H3 of run `20260718T132852`, delegation D005 for the initial
  search plus D013 for a dedicated verification-only follow-up (0 new oracle evals --
  direct inspection of already-archived Stage-1 ODBs). D013 settled an adversarial
  review's MAJOR finding: is the shared `coilable` flag (computed from the analytical
  reference point's UR3 rotation) a genuinely meaningful signal for the tensegrity
  topology, given its joint-to-ring coupling ties only translations (u1=u2=u3=ON,
  ur1=ur2=ur3=OFF)? D013 extracted the actual mode-1 displacement of the 3 physical
  strut-top nodes directly and fit a rotation angle independently of the UR3 field:
  winning design's fitted theta matched the reported UR3 to 5.8e-10 rad absolute
  difference (and a non-coiling control case matched to 1.5e-9 rad) -- the flag is
  confirmed genuine, not a reference-point artifact.
- DEMOTION, per project record (this study's "Artifact vs physical" / "Apples-to-apples
  criterion" policy): a comparable, apples-to-apples design must be (a) elastic, no
  folding/mechanism collapse, (b) a comparable stress measure, and (c) printable/
  realizable as a single continuous member family. A pin-jointed, prestress-driven
  tensegrity assembly fails (a) and (c) by construction (it is a mechanism assembly
  with rigid-body joint rotations, not a single continuously-bending elastic beam) --
  so despite being a real, reproducible, fully-feasible 220.89 kPa design, it is
  excluded from this study's beam-family headline comparisons.
- WHY "fully feasible" IS trustworthy despite a real gate bug found mid-run: D009
  (implementer, flagged) discovered the mls<=0.02 feasibility gate was computing a
  field that does not exist in this ODB and silently returning 0.0 for every one of
  94 designs evaluated so far -- meaning the gate had never actually been enforced.
  D010 fixed the oracle (added the missing LE field request) and D011 then
  DELIBERATELY discarded all pre-fix ledger rows and re-ran the full campaign fresh
  against the corrected oracle (explicitly removing D009's own reuse/idempotency
  logic so no stale mls=0.0 row could leak back in). The reported 220.89 kPa /
  fully-feasible result is from that corrected, post-fix campaign. Separately, the
  critic flagged the 287x-over-baseline magnitude itself as CRITICAL-severity
  implausible against this study's own commissioned literature review; the
  strategizer spent two further bounded delegations (D012 sweep, D013 mode-shape
  verification above) specifically to settle that concern with new evidence rather
  than soften the claim or drop it under time pressure (strategizer's own closing
  retrospective).
- GIF NOTE: this ODB (data/idea_odbs/20260718T132852_H3_tensegrity/tensegrity_RIKS.odb)
  has no 'E' (beam bending strain) field output at all -- physically correct, since
  T3D2 truss/cable elements have no bending strain concept. The render script's
  primary contour variable was extended with a principled fallback (try E/E11 first;
  if absent, use LE/LE11, axial logarithmic strain -- the truss-family analogue of the
  same physical quantity) rather than leaving color off or fabricating a bending-strain
  field that does not exist for this topology. Only 10 frames were available in this
  ODB's Riks step (vs up to 30 elsewhere); all 10 rendered cleanly.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T132852 — summary</div>

# Run `20260718T132852` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** distributed N-cell (N&ge;3) flexure-hinge chain &rarr; folds
  into the flexure-hinge idea's slide (falsified).
- **H2:** smooth continuous taper vs. the piecewise "waisted" family &rarr;
  folds into the waisted-tapered idea's slide (inconclusive).
- **H3:** Class-1 tensegrity strut-and-cable replacement (new idea, own
  slide) &rarr; supported (220.89 kPa; later demoted via the
  apples-to-apples criterion).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see the idea slide above and
this slide's speaker notes for full detail.
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
- H3: see idea slide above.
-->
---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T071133</div>

# Laced/battened two-parallel-chord built-up longeron

::left::

<div class="text-sm leading-snug">

- **What:** Replaced each solid longeron with two parallel slender chords
  separated by a fixed gap (a laced/battened built-up member), aiming to
  set global bending stiffness by chord separation while peak local strain
  stays governed by each chord's own small radius.
- **Origin:** common-sense mechanistic hypothesis grounded in the
  parallel-axis theorem (2&middot;A_f&middot;(h/2)&sup2;), not a
  literature citation.
- **Stats:** a 50-eval CEI-BO campaign found only 1/50 fully feasible, at
  &sigma;_cr,nd=0.00079 kPa — three orders of magnitude below the 0.7704
  kPa target, with zero new feasible points in the final two of five
  rounds.
- **Verdict:** inconclusive — the search barely found the feasible
  manifold at all (2% feasible rate), too underpowered to certify the
  mechanism's absence, but the one point found is nowhere near
  competitive.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/built_up_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Full context:

- This is hypothesis H2 of run `20260718T071133`, delegation D005 (50-eval CEI-BO
  campaign over the laced/battened two-chord longeron). Correction per the verdict
  validator's critique: with feasibility this sparse (2%), this is not a
  well-populated feasible region whose objective trend plateaued -- it is a search
  that struggled to find feasibility at all, which per the study's Charter Sec.2 lacks
  the demonstrated search power to support a negative existence claim of this
  magnitude. Left INCONCLUSIVE rather than FALSIFIED.
- ODB: data/idea_odbs/20260718T071133_H2_laced_built_up/SUPERCOMPRESSIBLE_RIKS.odb,
  sourced from presentation/resim/built_up/riks_4a8e6e6a4c504a5abfa2ef1b0d5f21c1.
  Rendered cleanly through the full native pipeline; the twin-chord (two-parallel-rod)
  construction of each longeron and its coiling motion are clearly visible.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T071133 — summary</div>

# Run `20260718T071133` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** mine the Bessa 7D generalized-cross-section dataset for a real,
  realizable profile &rarr; folds into the extended-J hollow-tube idea's
  slide (inconclusive — 0 of the coilable rows pass all four criteria at
  once).
- **H2:** laced/battened two-parallel-chord built-up longeron (new idea,
  own slide) &rarr; inconclusive.
- **H3:** 2-storey mast reduces peak local strain &rarr; folds into the
  multi-storey idea's slide (inconclusive).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see the idea slide above and
this slide's speaker notes for full detail.
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
- H2: see idea slide above.
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

<div class="text-xs opacity-50 mb-2">Run 20260718T031519</div>

# In-plane serpentine/meander longeron centerline

::left::

<div class="text-sm leading-snug">

- **What:** Perturbed each longeron's centerline into a periodic,
  small-amplitude in-plane serpentine (meander) wave instead of a straight
  line, aiming to distribute bending curvature along the member's length
  rather than concentrate it at one region.
- **Origin:** common-sense mechanistic hypothesis (a curvature-distribution
  argument), not drawn from an outside literature source.
- **Stats:** a 17-point 2D sweep (amplitude &times; n_periods); of 8
  trustworthy converged points, local strain correlated *positively* with
  both amplitude (+0.42) and periods (+0.53) — the opposite of the
  hypothesized direction; best feasible point stayed at the fixed-cross-
  section 0.7704 kPa control (no meandered design exceeded it).
- **Verdict:** negative — meandering raises, not lowers, peak local strain,
  so it does not unlock a feasible window above baseline; recorded
  inconclusive only because the trustworthy sample (8 of 17 points) is
  thin, but the observed direction is unambiguous.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/meander_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Full context:

- This is hypothesis H2 of run `20260718T031519`, delegation D007. Final correction
  (per a third critic pass): earlier-cited correlations of +0.522/+0.593 had included
  D003's unledgered pre-registration regression check (an amplitude=0 "control" point
  that was never re-solved through get_evaluator(), same convention issue as this
  run's H1). Recomputed using ONLY genuine ledgered D007 rows, trust-gated
  (converged==True AND stabilization_energy_ratio<0.05, n=8 of 17 tested points -- 9
  points never produced a trustworthy read at all): corr(amplitude, mls)=+0.419,
  corr(n_periods, mls)=+0.530. Both remain clearly positive (unfavorable direction).
- This idea later got a hierarchical/fractal-order refinement in run `20260724T012622`
  (H4), also falsified -- not in this batch's scope, noted here for continuity only.
- ODB: data/idea_odbs/20260718T031519_H2_meander_serpentine/SUPERCOMPRESSIBLE_RIKS.odb,
  sourced from presentation/resim/meander/riks_545d6f9df95a45a195e0991a7c74a888.
  Rendered cleanly through the full native pipeline; the meander perturbation is subtle
  at this (small, per-hypothesis) amplitude but visible along each longeron's length.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260718T031519 — summary</div>

# Run `20260718T031519` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** elliptical top/bottom rings with phase offset, re-tested &rarr;
  folds into the elliptical-rings idea's slide (falsified — every point in
  a 30-point sweep plus 2 boundary probes was non-coilable).
- **H2:** in-plane serpentine/meander centerline perturbation (new idea,
  own slide) &rarr; inconclusive.


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see the idea slide above and
this slide's speaker notes for full detail.
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
- H2: see idea slide above.
-->

---
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260717T192331</div>

# Smoothly radially-tapered ("waisted") longeron

::left::

<div class="text-sm leading-snug">

- **What:** Tapered a longeron's radial thickness along its arc-length —
  thick at both ring ends, waisted at mid-span — a fixed-volume
  optimal-column shape, not a uniform section.
- **Origin:** classical Lagrange-Keller / Tadjbakhsh-Keller optimal-column
  result, adapted to this study's longeron geometry.
- **Stats:** initial 0.877 kPa headline (beating 0.7704 kPa) proved invalid:
  corrected slenderness (ratio_pitch/(2&middot;ratio_b)) gave 8.35, below
  the &ge;10 floor; only 2/30 follow-up points feasible under correction.
- **Verdict:** inconclusive — the mis-specified (waist-based) constraint
  never searched the real feasible region; the headline fails corrected.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/waisted_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">A typical member of the search, not the (later-invalidated) 0.877 kPa point.</div>
</div>

<!--
Full context:

- This is hypothesis H3 of run `20260717T192331`. The waist-based slenderness
  mis-specification bug was caught by a later ledger audit (this run's own H4, and
  independently re-confirmed in run `20260718T132852`'s H2): the study's slenderness
  criterion is defined on the tangential half-width ratio_b (ratio_pitch/(2*ratio_b)),
  which a purely-radial taper does not touch -- so the taper family's self-reported
  "slenderness" (computed off the tapered/waisted radial dimension, 33.7 for the 0.877
  kPa point) was the wrong quantity entirely; recomputed correctly it is 8.351, failing
  the >=10 floor.
- FINAL SETTLEMENT (quoted from the run's own hypothesis log): "Settling here
  permanently (no further reversal), accepting the validator's final point: D006's
  CEI-BO search was guided by constraints built on the (my own mis-specified)
  waist-based slenderness, so it never searched FOR feasibility under the corrected,
  problem-statement-faithful ratio_b-based slenderness -- a search not aimed at the
  real constraint is not an adequate test of it, regardless of what a post-hoc
  recompute of the same data shows."
- The rendered ODB (data/idea_odbs/20260717T192331_H3_waisted_tapered/
  SUPERCOMPRESSIBLE_RIKS.odb, sourced from presentation/resim/waisted/
  riks_b25001089f5c4baa82473915d82f8736) is a typical member of this family's search --
  per the format contract's no-winner convention, not necessarily the single best (and
  specifically NOT the later-invalidated 0.877 kPa point). Rendered cleanly through the
  full native pipeline; the radial taper toward each longeron's mid-span waist is
  visible even in the undeformed frame.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260717T192331 — summary</div>

# Run `20260717T192331` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** extend the rectangle search beyond the known corner &rarr; folds
  into the rectangle-anchor idea's slide (supported — reconfirms 0.7704
  kPa bit-identically).
- **H2:** extend the Kresling psi ceiling &rarr; folds into the Kresling
  idea's slide (falsified — no design in [0,60&deg;] beat the 0.711 kPa
  anchor).
- **H3:** smoothly radially-tapered ("waisted") longeron (new idea, own
  slide) &rarr; inconclusive.
- **H4:** local refinement around the waisted 0.877 kPa point &rarr; folds
  into the waisted idea's slide (inconclusive — that point was later found
  invalid under the corrected slenderness formula).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see the idea slide above and
this slide's speaker notes for full detail.
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
- H3: see idea slide above.
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

<div class="text-xs opacity-50 mb-2">Run 20260717T014507</div>

# Kresling/TCO two-segment bar-hinge longeron

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
- **Stats:** a 45-eval CEI-BO campaign found a genuine feasible design at
  psi=30&deg;, &sigma;_cr,nd=0.7106 kPa (1.8&times; the 0.3918 kPa target),
  coilable=1, mcs=1.0, mls=0.0199, slenderness&ge;10; later extension runs
  found no further improvement beyond ~0.711 kPa.
- **Verdict:** INCONCLUSIVE — a genuinely feasible design existed and once
  cleared all four original criteria, but was later rejected on a separate
  ring-passthrough criterion (see notes); not a validated winner.

</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/kresling_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Full context:

- This is hypothesis H3 of run `20260717T014507`, delegation D007 (45 real, ledgered
  evals: 1 stabilized anchor re-run + fixed-geometry psi-sweep + 26-pt global
  LHS/EI-lite BO + 16-pt local trust-region refinement, all slenderness>=10
  pre-screened, meeting the registered >=30-eval budget). Best feasible design:
  psi_kresling=30deg, sigma_cr,nd=0.7110618 kPa.
- The run's own gate critic FINAL SETTLEMENT (quoted): "the honest path... is to
  settle H3 at its last validator-endorsed INCONCLUSIVE and stop re-litigating" --
  reverting a subsequent (disputed) FALSIFIED flip back to the last validator-endorsed
  status, on the same D007 evidence, and stopping there.
- REJECTION, reported per the manifest/PROVENANCE.txt: this exact feasible design
  (psi=30deg, sigma=0.711 kPa) was later REJECTED in bo/confirmed_anchors.json
  (`_rejected.kresling_snap`) for failing criterion 5 (ring-passthrough) -- the
  bar-hinge kink lets the longeron's mid-span node pass through the ring's 0-D plane
  undetected during coiling, a failure mode this study's beam-only feasibility
  criteria (coilable/mcs/mls/slenderness) do not check for. So this idea passed every
  criterion it was originally tested against, then failed a criterion added later in
  the study -- an honest, still-open example of criteria evolving mid-study, not a
  contradiction.
- ODB: data/idea_odbs/20260717T014507_H3_kresling_bar_hinge/SUPERCOMPRESSIBLE_RIKS.odb,
  sourced from presentation/resim/kresling_run17/riks_93eadc4e3f4f4c5fa20d3e80954e6b60.
  Rendered cleanly through the full native pipeline; the bar-hinge kink partway up
  each longeron is visible in the animation.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260717T014507 — summary</div>

# Run `20260717T014507` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** existence &ge;0.3918 kPa in the rectangle family &rarr; folds
  into the rectangle-anchor idea's slide (supported — 0.7704 kPa found,
  becomes the canonical anchor for the rest of the study).
- **H2:** pretensioned diagonal cable-stay bracing &rarr; folds into the
  chiral-bracing idea's slide (inconclusive, 0/45 feasible — only the
  no-brace control was feasible).
- **H3:** Kresling/TCO bar-hinge longeron (new idea, own slide) &rarr;
  inconclusive.


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see the idea slide above and
this slide's speaker notes for full detail.
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
- H3: see idea slide above.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260715T191329 — summary (no new idea this run)</div>

# Run `20260715T191329` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** rectangle family ceiling vs the 3&times;-Bessa target &rarr;
  folds into the rectangle-anchor idea's slide (inconclusive).
- **H2:** broad existence claim — does ANY novel family (serpentine
  centerline, auxiliary bracing, and others) decouple buckling stiffness
  from radial bending strain? &rarr; inconclusive, bounded negative across
  five families tested on the first trustworthy converged oracle.


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No new genuinely-new idea originated this run (both hypotheses are a
refinement and a cross-cutting/meta claim) — no idea slide, per format
convention. See speaker notes for detail.
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
layout: two-cols-header
class: idea-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260715T002538</div>

# Helical (chiral) longeron path

::left::

<div class="text-sm leading-snug">

- **What:** Bent each longeron into a helix winding around the mast axis
  (a `helix_wrap` parameter), rather than a straight line, hypothesizing a
  spring-like geometry predisposed to reversible coiling.
- **Origin:** common-sense mechanistic hypothesis, explicitly distinguished
  from pre-twist (which rotates the cross-section) and radial bowing
  (which is planar) — both tried and falsified in earlier runs. Not drawn
  from an outside literature source.
- **Stats:** a 28-eval existence search found only the degenerate
  `helix_wrap=0` point feasible (&sigma;=0.0057 kPa); a matched-pair causal
  sweep at wrap=0.6 showed &sigma; rising to 2.31 kPa but max local strain
  exploding to 19.1% (vs the 2% limit).
- **Verdict:** falsified — helical wrap raises critical buckling stress
  but destroys local-strain feasibility even faster, the opposite of the
  hypothesized reversible-coiling benefit.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/helical_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Full context:

- This is hypothesis H2 of run `20260715T002538`, delegation D007 (28-eval existence
  search) plus an independent matched-pair causal sweep at wrap=0.0/0.6. The registered
  falsification criterion was specifically the MECHANISM branch: "if no feasible
  helical design even exceeds the ~0.06 kPa rectangular ceiling, the helical mechanism
  confers no advantage." Only 1/28 designs was feasible at all, and it was the
  degenerate wrap=0 (i.e. straight) case -- no genuinely-helical design was feasible,
  so none exceeded the ceiling. The matched-pair sweep independently confirms the
  causal direction: at wrap=0.6, sigma_cr,nd=2.306 kPa (well above ceiling) but
  max_local_strain=0.191 (19.1%, vs the wrap=0 control's max_compressive_strain=0.976,
  max_local_strain=0.0209 at the same cross-section) -- the helical mechanism trades a
  large stiffness gain for a catastrophic strain penalty.
- ODB: data/idea_odbs/20260715T002538_H2_helical_longeron_path/SUPERCOMPRESSIBLE_RIKS.odb,
  sourced from presentation/resim/helical/riks_helical_76b431f83394417ea38e227d26171b56.
  Rendered cleanly through the full 30-frame native pipeline (no COORD field output
  gaps, no divergent nodes) -- both schematic rings and the coiling helix motion are
  visible throughout the animation.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260715T002538 — summary</div>

# Run `20260715T002538` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** closed thin-walled box cross-section at slenderness&ge;10 &rarr;
  folds into the box/hollow-tube idea's slide (inconclusive — mechanism
  confirmed, coilability fails).
- **H2:** helical (chiral) longeron path (new idea, own slide) &rarr;
  falsified.
- **H3:** feasible &sigma; bound by the 2% local-strain limit (rectangle
  family) &rarr; falsified as an absence claim — a knife-edge bifurcation,
  not a feasible window.
- **H4:** 2-storey escape from the &sigma;&harr;feasibility barrier &rarr;
  folds into the multi-storey idea's slide (inconclusive — barrier holds).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see this slide's speaker notes
for full detail.
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
- H2: see idea slide above.
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

<div class="text-xs opacity-50 mb-2">Run 20260714T020739</div>

# Diagonal chiral-bracing lattice

::left::

<div class="text-sm leading-snug">

- **What:** Added a diagonal chiral-bracing lattice of short auxiliary beam
  struts between adjacent longerons, layered on the slenderness-valid
  rectangular family (two verified CEI-BO campaigns; see notes).
- **Origin:** common-sense — an alternative stiff load path to offload
  torsional/bending demand from the longerons (a later refinement drew a
  cable-stayed precedent, Gurfinkel & Krishnan 2017; see notes).
- **Stats:** 42 verified evals, 0/42 fully feasible; braced designs failed
  max_compressive_strain in 30/30 (100%) vs 34/46 (74%) unbraced control.
- **Verdict:** INCONCLUSIVE as an existence claim; directional signal is
  clear — bracing blocks coiling rather than helping it.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/chiral_brace_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Undeformed configuration only — see speaker notes.</div>
</div>

<!--
Full context:

- This is hypothesis H2 of run `20260714T020739` (delegations D005+D006). It folds
  together every later bracing variant tried in this study (cable-stayed, chiral-ring,
  aperiodic/golden-ratio, multi-turn helical-coil) -- all are one "auxiliary bracing"
  mechanism family per the manifest's boundary rule. ODB provenance: the permanent
  archive at data/idea_odbs/20260721T201733_H4_chiral_brace/ (folder named for a later
  run because that is where the best-known illustrative bracing point's ODB was
  recovered from; PROVENANCE.txt is explicit that this is "an illustrative bracing
  point, not bit-identical to the H4 optimum" -- the exact 8D optimum's parameters were
  never recoverable from that later run's own text). That later run's H4 (sigma=1.2457
  kPa) was a more elaborate joint host+brace optimization that never passed full
  apples-to-apples (its own H6 found the brace ligament itself over-strains) -- so the
  mechanism's overall arc across the study stayed negative/inconclusive despite that
  one nominally-positive number.
- GIF LIMITATION, reported honestly per this task's instructions rather than skipped
  or faked: the archived ODB (data/idea_odbs/20260721T201733_H4_chiral_brace/
  SUPERCOMPRESSIBLE_RIKS.odb) has a genuine, ODB-specific rendering blocker. Two of its
  2610 LONGERONS-instance nodes (labels 562, 1369 -- both endpoints of two T3D2
  brace/truss elements, 554-555 and 1363-1364) carry an Abaqus invalid/sentinel
  displacement value (magnitude 1e23-1e36) in the U field output from increment 1
  onward (frame 0 is clean; every later frame checked -- 1,2,3,5,10,29,50,97 -- shows
  the identical two-node fault, so it is not a transient blip). Excluding those two
  elements from the display group (a native, non-fabricating fix -- same technique
  already used elsewhere in this pipeline to hide the non-structural ANALYTICAL_SURF
  instance) stopped the crash risk but did NOT restore the visible geometry: every
  frame after 0 still rendered fully blank (confirmed with contour off, with per-frame
  camera re-assertion, and with node-averaging disabled -- none fixed it), and
  rendering the same frame in plain wireframe (renderBeamProfiles=OFF) segfaults
  Abaqus/Viewer outright (signal 11) for this specific ODB. This appears to be a Mesa
  software-rendering depth/precision failure triggered by those two divergent nodes'
  astronomical coordinates propagating into the viewport's internal state even when
  the offending elements are excluded from display -- not something fixable within
  this pass without deeper Abaqus-internals investigation. Per this task's explicit
  instructions ("if you hit a genuine blocker... report that specifically rather than
  skip it silently"), the image shown is a genuine native Abaqus/CAE render of this
  same ODB's undeformed (frame 0) configuration only -- a real, unfabricated render,
  just not an animation. A full animated re-render of this idea remains open work.
- Two small general-purpose fixes were made to the shared presentation/render/render_odb.py
  during this investigation (kept, since they are principled and harmless for every
  other ODB in this deck): (1) `_current_positions` now falls back to
  undeformed-coordinates + U when an ODB has no COORD field output at all (needed for
  this same bracing ODB's ring-schematic overlay, which DOES render correctly in every
  frame); (2) a `_divergent_element_labels` helper excludes from display any element
  touching a node with a >1e30-magnitude field value in any rendered frame, general
  robustness for any future ODB with a similar localized divergence, not a
  chiral-brace-specific hack.
-->

---
layout: two-cols-header
class: summary-slide
---

<div class="text-xs opacity-50 mb-2">Run 20260714T020739 — summary</div>

# Run `20260714T020739` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** hard slenderness&ge;10 floor on the rectangle family vs the 2.34
  kPa target &rarr; inconclusive (best feasible 0.058 kPa, trend still
  rising when the campaign stopped).
- **H2:** diagonal chiral-bracing lattice (new idea, own slide) &rarr;
  inconclusive — bracing consistently blocks full coiling compression
  (0/42 feasible).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center px-4">
No image for a run-summary slide by format convention — see the idea slide above and
this slide's speaker notes for full detail.
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
- H2: see the idea slide above for full detail. Two delegations: D005 (48-eval main
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
class: summary-slide
---

# Run `20260712T192155` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** fresh joint 4D Bayesian search over the rectangle-anchor family
  (all of ratio_a/ratio_b/ratio_pitch/ratio_top_diameter simultaneously) →
  folds into the run17-rectangle-anchor idea slide, FALSIFIED — a
  repeatable counterexample was found (σ_cr,nd = 2.5656 kPa, coilable=1,
  max_compressive_strain=0.9998, max_local_strain=0.0199), clearing the
  2.3376 kPa floor while meeting all three feasibility criteria: more than
  double the run's own prior best (1.1688 kPa) and >7× the original
  0.3644 kPa anchor.
- **H2:** 2-storey mast with an independently-set tangential dimension per
  storey → folds into the multi-storey idea slide, INCONCLUSIVE (zero
  confirmed-feasible designs, but a persistent NaN gap in the Riks solves
  means this isn't a fully clean negative either).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
This run's H1 counterexample (2.5656 kPa) is this whole batch's best
confirmed valid design — a refinement of the run17-rectangle-anchor idea,
not a new mechanism, so it earns a bullet here rather than its own slide.
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
layout: two-cols-header
class: idea-slide
---

# Open thin-walled L-profile (shear-centre offset)

::left::

<div class="text-sm leading-snug">

- **What:** An open thin-walled longeron cross-section with an inherent
  shear-centre-to-centroid offset (Abaqus `LProfile`) — a DOF the Bessa
  parametrization fixes to zero, never accessed by any prior family.
- **Origin:** parametric-space extension, tempered by a literature review
  (Zahn & Iwankiw 1989 flexural-torsional buckling theory) predicting
  AGAINST the mechanism beforehand (see notes).
- **Stats:** 60-eval campaign (45 geometrically valid), slenderness≥10
  gated, zero feasible; best σ_cr,nd ≈0.0489 kPa, ~24× below the 1.1688 kPa
  baseline; GP surrogate CV R²=0.881 (above chance — the flat landscape is real).
- **Verdict:** FALSIFIED — matches the theoretical prior, now with
  adequate empirical confirmation; not competitive with the 2.3376 kPa floor.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/offset_shear_lprofile_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H1 of run `20260709T024901`, delegations D002 (literature review) + D005
  (search). ODB: data/idea_odbs/20260709T024901_H1_offset_shear_Lprofile/ (source:
  SCRATCH path /oscar/scratch/eaguerov/supercompressible_oracle/
  riks_a581638a45ad4424b5da6a66baa0cf06).
- D002's literature quote: "the lowest root is always less than either of the Euler
  flexural buckling stresses... and the pure torsional buckling stress about the
  shear center" — the coupling this hypothesis needed is a bug in classical FT
  buckling theory, not a feature, and open sections also have inherently low
  torsional constant J relative to closed/solid sections, trading away the dominant
  sigma_crit lever this study has repeatedly found (per Bessa's own sensitivity
  analysis) to gain a coupling term theory says can only hurt.
- Verdict-history nuance: the strategizer's first pass called this INCONCLUSIVE
  (deprioritizing given the slenderness gate's potential to have excluded a narrow
  feasible region), but the validator corrected this: the registered falsification
  criterion explicitly specified the slenderness≥10 gate as part of the claim being
  tested, so the test as run WAS exactly the registered one, and the result (zero
  feasible, adequate coverage, above-chance surrogate) mandates FALSIFIED.
- GIF: native Abaqus/CAE Viewer export, standard pipeline, no ODB-specific gotchas.
  The open L-shaped cross-section's asymmetric profile is directly visible in the
  rendered beam geometry; the partial, incomplete coiling shown (max mcs=0.579
  observed across the family) is a faithful, typical (not cherry-picked) result.
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260709T024901` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** open thin-walled L-profile (shear-centre offset) → own idea
  slide (above), FALSIFIED.
- **H2:** n_longerons variation within the rectangle-anchor family
  (proposed, zero evals this run) → folds into the n=5-longerons idea
  (tested later, outside this batch, in run `20260721T201733` as its own
  H7).
- **H3:** the rectangle-anchor family's optimum is bending-strain-limited
  (both Riks criteria already sit at their ceilings at 1.1688 kPa) →
  meta/analytical, SUPPORTED.


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
One new family tested and cleanly falsified; the run's real finding is
analytical (H3) — the current best design is already strain-capped, not
just under-searched.
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

# Flexure-hinge (piecewise stiff/thin) longeron

::left::

<div class="text-sm leading-snug">

- **What:** A spatially-varying longeron: thick `RectangularProfile` ends
  near both rings (global stiffness) with a deliberately thin mid-span
  "hinge" segment to cap peak bending strain.
- **Origin:** common sense — decouple average stiffness (thick ends) from
  peak local fibre strain (thin hinge), a DOF no uniform family could access.
- **Stats:** 56 evals (3 delegations), only 1/56 feasible, σ_cr,nd=0.1391
  kPa — BELOW the 0.3644 kPa uniform-section baseline; hinge_fraction vs.
  strain shows a scattered negative trend (r=-0.53, n=45), no sweet spot.
- **Verdict:** INCONCLUSIVE by the study's strict adequacy bar, but the raw
  signal is a clear dead end — underperforms the baseline, not just the floor.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/flexure_hinge_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H1 of run `20260708T021335`, delegations D002+D005+D006 (search) + D008
  (post-hoc CV adequacy check). ODB: data/idea_odbs/20260708T021335_H1_flexure_hinge/
  (source: presentation/resim/flexure/riks_5d90665da6d54585b4b429f4c5d17007).
- D005's first attempt died silently after only 12/50 planned evals — traced to a
  genuine `cei_core.py` NaN-handling bug (not a process crash), fixed and verified
  before D006's corrected continuation.
- D008's CV (Charter §2 adequacy check): sigma_crit objective GP is strongly above
  chance (R²=0.940), but max_compressive_strain (R²=-0.461) and the coilable
  classifier (identical to a majority-class dummy on every fold) are not — the same
  binding-constraint-surrogate failure mode this run's own H2/H3 also hit.
- GIF: native Abaqus/CAE Viewer export, standard pipeline. The alternating
  thick/thin segments along each leg's length are directly visible in the rendered
  beam profiles (renderBeamProfiles=ON) — the coiled, fully-collapsed frame shown
  is the one feasible design found (σ_cr,nd=0.1391 kPa).
-->

---
layout: two-cols-header
class: idea-slide
---

# BoxProfile hollow-tube cross-section

::left::

<div class="text-sm leading-snug">

- **What:** A closed, thin-walled rectangular hollow-tube (`BoxProfile`)
  longeron, motivated by mining the 50,000-point Bessa 7D dataset for
  high-torsion/bending-stiffness combinations no solid family could reach.
- **Origin:** dataset-mining common sense — a least-squares fit of
  high-performing 7D rows to box geometries had poor residuals (~98%
  relative L2 error), so the family was built and searched directly.
- **Stats:** 51-eval constrained-BO search, only 4/51 feasible, best
  σ_cr,nd=0.3123 kPa — below the 0.3644 kPa solid-rectangle baseline.
- **Verdict:** INCONCLUSIVE by the strict adequacy bar, but a clear
  negative signal — a genuinely different (mode-switching) failure mode
  than the solid rectangle, yet the same practical conclusion: underperforms.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/box_hollow_tube_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H2 of run `20260708T021335`, delegations D004 (build+validate) + D007
  (search). ODB: data/idea_odbs/20260708T021335_H2_box_hollow_tube/ (source:
  presentation/resim/box/riks_c6f5fdb729c549fd93c5ddb53065dde3).
- The outer-tangential-dimension sweep found feasible windows at ratio_b_out=0.02 and
  0.054 but infeasible at 6 of 8 other swept points — a genuinely different mechanical
  behavior from the solid-rectangle family's clean, monotonic collapse (this run's H4,
  which folds into the run17-rectangle-anchor idea), even though the net practical
  result (underperforms) matches.
- GIF: native Abaqus/CAE Viewer export, standard pipeline. The hollow box's
  rectangular tube profile is directly visible in the rendered beam cross-sections.
-->

---
layout: two-cols-header
class: idea-slide
---

# Heterogeneous (2 stiff + 1 compliant) longerons

::left::

<div class="text-sm leading-snug">

- **What:** Made the 3 longerons non-identical: 2 stiff `RectangularProfile`
  + 1 compliant `RectangularProfile`, same radial dimension, unchanged
  rings.
- **Origin:** common sense — the compliant longeron absorbs large
  rotations, "rescuing" compressibility while the stiff ones carry
  buckling load.
- **Stats:** 45-eval constrained-BO (46 incl. a degenerate anchor); 1/46
  feasible (stiff=compliant, σ_cr,nd=0.3644 kPa, matching not exceeding
  baseline). Ratio vs. max strain: weak, non-monotonic (r=0.124, ρ=0.296,
  n=32).
- **Verdict:** INCONCLUSIVE by the study's adequacy bar, but the mechanism
  is contradicted: mild heterogeneity does NOT preserve compressibility
  (ratio=0.951 stalled at mcs=0.160 vs. ratio=1.0's mcs=0.9999) — no
  improvement over uniform found anywhere.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/heterogeneous_longerons_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H3 of run `20260708T021335`, delegations D010 (build+validate, exact
  degenerate reproduction of the known baseline) + D011 (45-eval search) + D012
  (post-hoc CV). ODB: data/idea_odbs/20260708T021335_H3_heterogeneous_longerons/
  (source: presentation/resim/heterogeneous/riks_fb818885227f43fe888ec53eafa44a17,
  representative point solved at sigma=0.867; the family's actual near-degenerate
  best-found point was ~0.3644, i.e. the baseline itself).
- D012's CV shows the same recurring pattern as this run's H1/H2: sigma_crit is
  strongly learnable (R²=0.920), max_compressive_strain is moderately learnable
  (R²=0.418, above chance but noisier).
- GIF: native Abaqus/CAE Viewer export, standard pipeline. The visibly different
  cross-section sizes among the three legs (two thick, one thin) are directly
  visible in the rendered beam profiles — the asymmetric coiling behavior this
  produces is real, not a rendering artifact.
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260708T021335` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** flexure-hinge (piecewise stiff/thin) longeron → own idea slide
  (above), INCONCLUSIVE (strong negative signal, underpowered surrogates).
- **H2:** BoxProfile hollow-tube cross-section → own idea slide (above),
  INCONCLUSIVE (underperforms baseline).
- **H3:** heterogeneous (2 stiff + 1 compliant) longerons → own idea slide
  (above), INCONCLUSIVE (no improvement found).
- **H4:** increase only the tangential dimension of the rectangle-anchor
  family (no pitch co-scaling) → folds into the run17-rectangle-anchor
  idea slide, SUPPORTED — new best-found design, 1.1688 kPa (3.2× the
  0.3644 kPa anchor).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
Three new cross-section families tried this run, all dead ends — but the
run's one refinement (H4) delivers the biggest single headline jump of
this batch, more than tripling the established anchor's performance.
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

# Elliptical top/bottom rings, phase offset

::left::

<div class="text-sm leading-snug">

- **What:** Replaced the mast's circular top and bottom rings with
  independently-parametrized ellipses plus a phase offset between the top
  and bottom ring's major-axis orientation, to break the rotational
  symmetry that forces every longeron to undergo identical peak curvature.
- **Origin:** common sense structural-symmetry-breaking hypothesis, not a
  literature citation.
- **Stats:** D008's dense local grid found a sharp cliff — max compressive
  strain collapses from 0.9999 to 0.398 at the very first non-circular
  step tested, and coilable=0 at every nonzero phase offset down to
  0.15 rad; a broader 48-eval joint search (D010) found only 2/48 coilable
  and 0/48 feasible.
- **Verdict:** INCONCLUSIVE by the study's own strict adequacy bar (the
  guiding constraint surrogates were not demonstrably above chance, so a
  closed non-existence verdict isn't licensed) — but the raw picture is
  about as close to a clean dead end as this deck sees short of a formal
  FALSIFIED: elliptical rings very sharply destroy coilability rather than
  redistributing strain as hypothesized.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/elliptical_rings_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H3 of run `20260706T204732`. ODB: data/idea_odbs/20260706T204732_H3_elliptical_rings/
  (source: presentation/resim/elliptical/riks_ellring_48e398830e1c4b4ca2e491e4da1e547d).
- Verdict history: the strategizer initially closed this FALSIFIED given the sharp
  cliff and zero-feasible broad search; the validator flagged (per Charter §2) that
  the guiding constraint surrogates (max_compressive_strain, max_local_strain,
  coilable) were NOT above chance (mean-fold R²=-0.036/-0.050, classifier below
  majority baseline) — Charter §2 requires ANY guiding surrogate to predict above
  chance before a non-existence verdict can close, and "near-chance surrogate
  performance is what you'd expect near an empty region anyway" is exactly the
  post-hoc plausibility argument the charter forecloses. Retracted to INCONCLUSIVE.
- This idea was re-tested once more, outside this deck's batch range, in run
  `20260718T031519` H1 (elliptical rings w/ phase offset re-test, FALSIFIED) — that
  refinement folds into this same idea, but belongs to a later batch's summary slide.
- GIF: native Abaqus/CAE Viewer export, standard pipeline. The rendered design shows
  visibly incomplete/partial coiling (a mid-strain frame, not the collapsed cliff
  case) — a representative, still-somewhat-coiling point from the family, per the
  format contract's "typical, not necessarily best" no-winner convention.
-->

---
layout: two-cols-header
class: idea-slide
---

# Radially bowed (pre-curved) longerons

::left::

<div class="text-sm leading-snug">

- **What:** Gave each longeron a smooth radial offset by height — zero at
  both rings, max inward bow at mid-height — to geometrically pre-condition
  the coiling path and retain high compressive strain.
- **Origin:** common sense geometric hypothesis, not a literature citation.
- **Stats:** confound-free single-variable dose-response sweep
  (bow_amplitude ∈ {0,0.05,0.10,0.15}, fixed ratio_b=0.03) shows
  max_compressive_strain DECREASING monotonically with bow — 48% drop at
  ratio_b=0.03 (0.5846→0.3040), 0.9999→0.5007 at the winning cross-section.
- **Verdict:** FALSIFIED, cleanly. Bowing does the opposite of hypothesized
  — it collapses compressive strain rather than protecting it; no benefit
  found in a follow-up 48-eval joint search either.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/bowed_longerons_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H5 of run `20260706T204732`, delegation D011 (mechanism dose-response) +
  D012 (48-eval joint 5D existence follow-up). ODB: data/idea_odbs/
  20260706T204732_H5_bowed_longerons/ (source: presentation/resim/bowed/
  riks_bow_86c0a1b0a97a46e480420304ad196708).
- This is one of the deck's clean mechanism falsifications, analogous in kind to the
  format-example twisted-strip slide's claim (a): a single-variable, matched-
  conditions, causal dose-response sweep is adequate on its own terms (no CV/surrogate
  check needed) because it is a designed experiment directly testing the causal claim,
  not a surrogate-guided search whose adequacy depends on above-chance CV.
- GIF: native Abaqus/CAE Viewer export, standard pipeline. The visible outward bow of
  each leg before compression begins (frame 0) is the mechanism itself, not a
  rendering artifact.
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260706T204732` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** relax the rectangle-anchor family's slenderness floor to ≥8 →
  folds into the run17-rectangle-anchor idea slide, INCONCLUSIVE
  (constraint surrogates not above chance; raw result was worse than the
  ≥10 baseline anyway, 0.3130 kPa).
- **H2:** add pretwist to the rectangle-anchor family → folds into the
  run17-rectangle-anchor idea slide, INCONCLUSIVE (same surrogate-adequacy
  standard applied consistently with H1/H3).
- **H3:** elliptical top/bottom rings with phase offset → own idea slide
  (above), INCONCLUSIVE (strongly suggestive dead end).
- **H4:** scale ratio_b and pitch together at fixed slenderness=10 →
  folds into the run17-rectangle-anchor idea slide, FALSIFIED (feasibility
  collapses almost immediately past the smallest tested width).
- **H5:** radially bowed longerons → own idea slide (above), FALSIFIED.


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
Every hypothesis this run either fails outright or is blocked by the same
recurring issue: the Riks compressive-strain constraint surrogate is
consistently unreliable in the sparse-feasible regions this run searched.
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

# Elliptical cross-section

::left::

<div class="text-sm leading-snug">

- **What:** Proposed an elliptical longeron cross-section (Abaqus-native
  `EllipticalProfile`, `DURING_ANALYSIS` section integration), oriented so
  its short semi-axis lies in the plane of dominant coiling-induced
  bending, to raise torsional stiffness beyond the circular family's
  strain-limited ceiling.
- **Origin:** direct mechanistic extension of the SCLF (circular) family —
  common sense, not a literature citation.
- **Stats:** zero evaluations possible — none exist to report.
- **Verdict:** INCONCLUSIVE, and genuinely so: the hypothesis as literally
  registered is untestable with the available infrastructure, not
  falsified. `model.EllipticalProfile` does not exist in the installed
  Abaqus 2024 kernel, and `GeneralizedProfile` + `DURING_ANALYSIS` is
  rejected at `.inp`-write time. This is a hard software-capability gap,
  not a negative physics result — a genuinely different question
  (substituting `RectangularProfile` as the closest available real
  geometry) was registered separately as its own hypothesis rather than
  silently reinterpreting this one.


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
Fuller context:

- This is H4 of run `20260705T181941`, delegation D005 (introspection: confirmed
  `model.EllipticalProfile` absent; `GeneralizedProfile(..., integration=DURING_ANALYSIS)`
  rejected at input-file-write time). Originally the strategizer briefly closed this
  FALSIFIED before the validator/Charter §4 correction: an untestable literal claim
  cannot be falsified, only marked untestable.
- The substituted, actually-tested idea (anisotropic RectangularProfile, radial-long/
  tangential-short orientation) is registered as this same run's H6 — FALSIFIED (D010's
  two decorrelated 1D sweeps show max_local_strain tracking sigma_crit almost
  proportionally along the radial axis, the opposite of the intended decoupling) — and
  folds into the run17_rectangle_anchor idea's story below, since the REVERSED
  orientation tested next (H7/H8) is what actually becomes the study's anchor family.
- This is one of only two ideas in the whole 25-idea "genuinely new" list with no ODB
  by design (the other: pretwisted longerons, earlier this run-range). The tape-spring
  idea (`20260730T020245` H2) previously belonged in this no-ODB group while that run
  was still executing; it has since closed and its own ODB was archived — see its own
  slide, elsewhere in this deck.
-->

---
layout: two-cols-header
class: idea-slide
---

# Square (isotropic) cross-section

::left::

<div class="text-sm leading-snug">

- **What:** Tested a square longeron cross-section — at matched
  half-width/fiber-distance, a square carries ~1.7× a circle's moment of
  inertia (I_square/I_circle=64/(12π)), bend axis on a flat side not a
  diagonal.
- **Origin:** common sense, basic section-property comparison — not a
  literature citation.
- **Stats:** 50-eval constrained-BO, 18% joint-feasible (surrogates above
  chance: σ_crit CV R²=0.999, mls CV R²=0.545); 0/50 cleared the 0.196 kPa
  floor (2× the 0.1306 kPa baseline) — best feasible σ_cr,nd=0.1600 kPa,
  18.4% short.
- **Verdict:** FALSIFIED, plainly — contradicted by an adequate,
  above-chance-surrogate search. (Square does edge circular in σ_crit at
  matched strain, 0.16-0.19 vs ~0.13-0.22, but the floor-clearing
  prediction still failed.)


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/square_section_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H5 of run `20260705T181941`, delegations D011 (search) + D012 (surrogate
  CV adequacy check). ODB: data/idea_odbs/20260705T181941_H5_square_section/ (source:
  presentation/resim/square/riks_c91bd5835aaf40f99dc06a3228aa4411).
- This run's H2 (SCLF family ceiling, meta/analytical) established the underlying
  physical trade-off this idea (and every subsequent cross-section variant) runs
  into: buckling stiffness scales with cross-section radius^4 while coiling-induced
  local bending strain scales only linearly with radius×curvature — 90 evaluations
  (D003+D006+D008, cross-validated by D009) found no circular-family design that
  breaks this trade-off, and the square-section test is essentially the same
  trade-off restated for a different section shape.
- GIF: native Abaqus/CAE Viewer export, standard pipeline, no ODB-specific gotchas.
  The square cross-section's flat-sided profile is visible in the rendered beam
  geometry (renderBeamProfiles=ON), distinguishing it visually from the circular
  SCLF renders elsewhere in this deck.
-->

---
layout: two-cols-header
class: idea-slide
---

# Anisotropic rectangle, reversed orientation (run17 anchor)

::left::

<div class="text-sm leading-snug">

- **What:** Anisotropic `RectangularProfile` longeron, radial SHORT /
  tangential LONG — reverse of this run's earlier falsified orientation,
  at slenderness≥10, testing whether max_local_strain and sigma_crit
  decouple.
- **Origin:** direct extension of the elliptical-substitution idea above —
  mirror of this run's own H6, common sense, not a literature citation.
- **Stats:** 3 distinct designs land in this valid-slenderness,
  floor-clearing region; headline design reaches σ_cr,nd=0.3644 kPa at
  slenderness=16.04, clearing the 0.196 kPa floor (2× baseline) with
  coilable=1, Riks strain=90%+, mls≤2%.
- **Verdict:** SUPPORTED — real, repeatable, non-fluke. This design
  becomes "run17_rectangle," the canonical anchor baseline reused
  throughout the rest of this deck.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/run17_rectangle_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H8 of run `20260705T181941` (the clean, minimal existence claim), following
  H6 (original orientation, FALSIFIED — max_local_strain rises 4× with the radial
  axis, tracking sigma_crit almost proportionally, the opposite of decoupling; D010's
  two decorrelated 1D sweeps) and H7 (reversed orientation, but an over-specific
  compound prediction demanding "multiple designs with meaningful margin" —
  INCONCLUSIVE, since only 1/46 valid-slenderness evals cleared the floor, too little
  data to confirm or deny the compound claim). H8 registers only the clean, supported
  half of H7's claim: existence of at least one valid design.
- ODB: data/idea_odbs/20260705T181941_H8_run17_rectangle_anchor/ (source: SCRATCH
  path /oscar/scratch/eaguerov/supercompressible_oracle/riks_09377e3040e64b82be337fcb827bd32e,
  gold-verified in bo/confirmed_anchors.json).
- The three distinct qualifying designs: D014's row 308 (ratio_a=0.00774,
  ratio_b=0.01417, slenderness=10.52, sigma_crit=0.2712 — found incidentally in a
  broader unconstrained sweep, before the two slenderness-gated searches ran), D016's
  design (slenderness=16.04, sigma_crit=0.3644, the headline, rendered here), and
  D017's design (slenderness=15.85, sigma_crit=0.2287).
- This family keeps improving across later runs, none of which earn a new idea
  slide (all fold into this one per the deck's rule 1): run `20260706T204732` tests
  relaxing the slenderness floor to ≥8 (INCONCLUSIVE) and adding pretwist
  (INCONCLUSIVE), run `20260708T021335` H4 raises the tangential dimension alone to a
  new best of 1.1688 kPa (SUPPORTED), and run `20260712T192155` H1 eventually finds a
  repeatable 2.5656 kPa counterexample (FALSIFIED against a tighter 2.3376 kPa floor
  introduced by then) — see those runs' own summary slides for detail.
- GIF: native Abaqus/CAE Viewer export, standard pipeline. This gif was re-rendered
  fresh for this batch (an earlier square-canvas, unlabeled-legend version existed
  from a prior rendering pass and has been replaced with the current
  portrait/top-right-legend/schematic-ring pipeline to match this deck's contract).
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260705T181941` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** re-tested "thick SCLF" under the new local-strain criterion →
  SCLF slide, SUPPORTED (mls=24.7%, invalidating it).
- **H2:** SCLF family ceiling / stiffness-vs-strain trade-off (analytical,
  meta) → SUPPORTED — no circular-family design breaks the trade-off across
  95 evaluations with above-chance surrogates.
- **H3:** n_storeys=2 curvature-reduction test → folds into multi-storey
  slide, INCONCLUSIVE (mechanism runs BACKWARDS — strain rose 13.5%).
- **H4:** elliptical cross-section → own idea slide (above), INCONCLUSIVE
  (untestable — Abaqus 2024 lacks EllipticalProfile).
- **H5:** square cross-section → own idea slide (above), FALSIFIED.
- **H6:** anisotropic rectangle, original orientation → folds into
  run17-rectangle-anchor, FALSIFIED.
- **H7:** anisotropic rectangle, reversed (compound claim) → folds into
  run17-rectangle-anchor, INCONCLUSIVE (under-powered).
- **H8:** anisotropic rectangle, reversed (clean existence claim) → own
  idea slide (above), SUPPORTED — becomes the study's canonical anchor.

</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
The run that broke the SCLF "486 kPa" headline (real physics, invalid
strain) and replaced it with a smaller but genuinely valid anchor
(0.3644 kPa) that the rest of the study builds on.
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

# Solid Circular Longeron Family (SCLF), thick variant

::left::

<div class="text-sm leading-snug">

- **What:** Constrained the cross-section to a solid circle (ratio_d ∈
  [0.08,0.16], else free) after the generalized Bessa optimum failed
  Stage 2 categorically — testing whether J/I=2 is what Stage 2 needs.
- **Origin:** follow-up to this run's H1 (generalized optimum: 9.23% Riks
  strain, not 90%) — circular is the shape closest to Bessa 2019's own
  demonstration.
- **Stats:** 40-pt LHS + Riks on best candidates; thick design
  (ratio_d=0.1333, ratio_pitch=0.93, ratio_top_diameter=0.5978) reached
  σ_cr,nd=485.996 kPa (~3720× Bessa 0.1306 kPa) at 90.06% Riks strain —
  clears both stages (83 increments, no divergence).
- **Verdict:** SUPPORTED as existence at the time — circular passes both
  stages, generalized doesn't. **But later invalidated** (next run's H1):
  peak local strain 24.7%, 12× the 2% PLA limit — the mechanism insight
  stands, the headline number doesn't.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/sclf_thick_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H2 (existence) and H4 (this specific thick design) of run `20260630T164908`,
  delegations D005/D008. H3 (shorter pitch, FALSIFIED — best 50.91% strain, pitch=0.30
  not even coilable) and H5 (smaller top ring, FALSIFIED — top_diam=0.50 gives
  strain=83.68%, WORSE than the original 0.5978, because a smaller top ring produces a
  LARGER geometric coiling limit h_min, opposite of what was predicted) are both
  refinements of this same idea, folded in here.
- ODB: data/idea_odbs/20260630T164908_H4_SCLF_thick/ (source:
  presentation/resim/thick_sclf/riks_6944016ddcca48608b995e9d6a4cbdfd).
- H1 this run (generalized Bessa optimum Stage-2 test, J=6.65e-6/Ixx=1.35e-6,
  sigma=65.31kPa): max compressive strain only 9.23% (RF3 peak -1165N then snap-back
  to -170N, not a coiling collapse) — this is what motivated the whole SCLF pivot and
  folds into the extended-J hollow-tube idea's story (same "generalized sections fail
  Stage 2" finding as H6/H7 of the prior run).
- The invalidation (run `20260705T181941` H1, delegation D001): max_local_strain=
  0.24719 (24.7%), max_compressive_strain=0.89534 (barely below the 0.90 Stage-2
  threshold too, at these exact Riks settings) — fails TWO of the three criteria, not
  just one. This finding is what motivated the study's own formal adoption of the
  three-criteria feasibility contract (coilable, Riks strain≥90%, local strain≤2%)
  used in every subsequent run.
- GIF: native Abaqus/CAE Viewer export, thick circular tube visibly coiling into a
  tight double-helix, strain colored (E11), dashed schematic rings, portrait canvas —
  standard pipeline, no gotchas specific to this ODB.
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260630T164908` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** generalized Bessa-optimum Stage-2 Riks test (J=6.65e-6) → folds
  into the extended-J hollow-tube idea's story, FALSIFIED (9.23% strain,
  not 90%; motivates the SCLF pivot).
- **H2:** Solid Circular Longeron Family, existence test → own idea slide
  (above), SUPPORTED (486 kPa, 90.06% strain).
- **H3:** shorter-pitch SCLF (ratio_pitch=0.30–0.40) → folds into the SCLF
  idea slide, FALSIFIED (best 50.91% strain; pitch=0.30 not even coilable).
- **H4:** SCLF thick design (ratio_d=0.1333, pitch≥0.93) → same idea as
  H2/its own idea slide, SUPPORTED then later invalidated (see idea slide).
- **H5:** smaller top-ring SCLF variant → folds into the SCLF idea slide,
  FALSIFIED (83.68% strain — smaller ring makes h_min LARGER, opposite of
  predicted).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
The run that discovered circular cross-sections can pass Stage 2 where
generalized sections categorically cannot — but its own headline design
would not survive the local-strain criterion introduced the very next run.
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

# Multi-storey topology (n_storeys=2)

::left::

<div class="text-sm leading-snug">

- **What:** Split the mast into two stacked storeys — an intermediate rigid
  ring at mid-height, still 3 continuous longerons per storey — instead of
  Bessa's single-storey topology, to see if a shorter per-segment coiling
  path could beat the Bessa 2019 paper optimum (65.3 kPa/longeron).
- **Origin:** common sense topology extension of the Bessa rocking-mast
  concept, not drawn from an outside literature source.
- **Stats:** 32/48 registered-criterion evaluations completed; best
  coilable design (a kinked helix, twist=0.1, ratio_pitch=0.327 half-pitch,
  Bessa-optimal cross-section) reached 64.9989 kPa — 99.5% of the
  single-storey Bessa optimum, but not above it.
- **Verdict:** INCONCLUSIVE — the topology recovers almost all of the
  single-storey performance without losing coilability, which is itself
  informative, but the specific prediction (beats 65.3 kPa) was not met and
  the highest-potential untested point (max-J cross-section at this
  half-pitch) was never evaluated before budget moved to other hypotheses.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <img src="/gifs/multistorey_n2_native.gif" class="max-h-100 rounded shadow-lg" />
</div>

<!--
Fuller context:

- This is H2 of run `20260629T191754`, delegation D004 (32/48 planned evals). ODB:
  data/idea_odbs/20260629T191754_H2_multistorey_n2/ (source:
  presentation/resim/twostorey/riks_9a82d64e16d34b71ac1e541263cd92bf; illustrative
  rectangular-family point, not bit-identical to the original run's anchor A5, but
  representative of the n_storeys=2 mechanism).
- Linear-scaling extrapolation predicted the untested max-J-at-half-pitch point could
  reach ~75.9 kPa, potentially clearing BOTH the 65.3 kPa and 75.1 kPa floors — this
  was flagged as the natural next step and picked up by a later delegation testing
  max-J at n_storeys=1 (B1 anchor) before committing further n_storeys=2 budget.
- This idea keeps reappearing across later runs as a refinement target (an
  independent per-storey ratio_b variant in run `20260712T192155` H2, a strain-barrier
  escape attempt in run `20260715T002538` H4, a peak-local-strain reduction test in
  run `20260718T071133` H3) — all fold into this same slide per the deck's rule 1, none
  earn their own slide.
- Run `20260718T071133` H3, why INCONCLUSIVE (not FALSIFIED as first drafted): the
  strategizer's first pass marked H3 FALSIFIED on the delegation's own self-reported
  "4/36 feasible, best=0.1085 kPa, clear plateau" (diagnostics.jsonl VERDICT_SUBSTANCE_FLAG,
  2026-07-18T11:38:07). A critic pass (retrospective, critic node, 2026-07-18T13:07:02)
  caught two compounding problems by re-querying the ledger directly rather than
  trusting the report: (1) a slenderness-formula bug meant the true feasible count was
  3/36, not 4/36 -- one of the "feasible" rows didn't actually clear criterion 4; (2)
  more importantly, ALL of the rows counted as feasible had `converged=False` -- they
  were non-converged salvaged reads, not genuine Riks solutions. The strategizer's own
  closing retrospective (2026-07-18T13:23:20) calls this out directly: a sparse,
  non-converged-only "feasible" set cannot support a falsification claim per the
  Charter, and the verdict was downgraded to INCONCLUSIVE. Kept here rather than
  fixed silently, because it's a real instance of the adversarial-critic layer
  catching a genuine science-integrity error the automated validator did not flag on
  its own axis (it flagged sparsity; the critic separately caught the convergence
  issue).
- GIF: native Abaqus/CAE Viewer export (presentation/render/render_odb.py). Only 5-6
  Riks increments are present in this archived ODB (a relatively shallow coiling test
  at this twist/pitch combination), so the animation is short; the legs show very low
  strain throughout (E11 range roughly ±1.6e-3), consistent with this being a modest,
  not-yet-optimized point in the family rather than its best-found design. Structural
  (beam-element) instance only, dashed schematic top/bottom ring annotation per the
  format-contract convention (this render script draws only the true top/bottom rings
  from the structural instance's own z-min/z-max — it does not know about or annotate
  the intermediate mid-height ring specific to this n_storeys=2 topology, since that
  ring is likewise a 0-D reference point with no solid geometry to render).
-->

---
layout: two-cols-header
class: idea-slide
---

# n_longerons = 5 (extended topology)

::left::

<div class="text-sm leading-snug">

- **What:** Increased the mast's rotational symmetry from Bessa's fixed 3
  longerons to 4, 5, and 6, at the same (near-optimal) 7D cross-section, to
  test whether more legs raise the per-longeron critical load.
- **Origin:** common sense topology extension — Bessa's own parametrization
  never varies longeron count, fixing it at 3 throughout the 2019 paper.
- **Stats:** 48-evaluation campaign; n=4, 5, 6 with a max-torsion
  cross-section all achieved σ_cr,nd = 65.31–71.59 kPa (n=5 specifically:
  71.59 kPa), all exceeding the registered 65.3 kPa prediction threshold.
- **Verdict:** SUPPORTED as registered — but with an important nuance: none
  of n=4/5/6 reached the study's actual 75.1 kPa floor, and per-longeron
  σ_cr,nd turned out to be empirically independent of n_longerons at fixed
  cross-section (λ_cr ∝ n×J, and the /n normalization exactly cancels it) —
  so this axis alone does not open a new performance regime, it is
  orthogonal to it.


</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/n5_longerons_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Native Abaqus render — no strain coloring (see notes).</div>
</div>

<!--
Fuller context:

- This is H3 of run `20260629T191754`, delegation D005. ODB: data/idea_odbs/
  20260629T191754_H3_n5_longerons/ (source: presentation/resim/n5_longerons/
  riks_60c367f12e3a4903839e9afe3127aa00). n_longerons=5 topology variant of the
  extended-J Bessa-7D family; Stage-1 sigma_cr,nd=71.59 kPa, matching the original
  finding, Riks re-solved fresh for this archive.
- RENDERING BLOCKER, reported per this batch's instructions rather than skipped: this
  archived ODB's Riks step only recorded RF/RM/U/UR field output — no `E` (strain)
  field was ever requested when the resim was originally run. render_odb.py's
  strain-coloring step (`setPrimaryVariable(variableLabel='E', ...)`) therefore fails
  with "Primary Variable not available: 'E' at integration points" on this specific
  ODB. This is a genuine data-provenance gap in the earlier resim pipeline for this
  one family (confirmed identical in the un-archived source copy too, so it is not an
  archiving mistake), not a bug in render_odb.py itself, and not something fixable
  without a fresh Abaqus solve (out of scope for this rendering-only batch). The gif
  shown is therefore rendered WITHOUT strain coloring (uniform shaded beam profiles,
  no legend) — an explicit, honest degradation per the format contract's gotcha 5
  ("if colour carries no data meaning, turn it off entirely"), not a fabricated
  E11 contour. The same limitation affects one other idea in this batch (the
  extended-J hollow-tube longeron, next).
- Critical insight carried forward: this run's finding that σ per longeron is
  independent of n_longerons at matched cross-section directly motivated the
  extended-J search (H4/H5 next) as the actual lever for beating the Bessa optimum.
-->

---
layout: two-cols-header
class: idea-slide
---

# Extended-J hollow/cellular longeron

::left::

<div class="text-sm leading-snug">

- **What:** Pushed torsional-stiffness ratio_J beyond the Bessa 7D
  dataset's own max (7.77e-6) — hollow/cellular cross-sections (e.g. a
  hollow tube) unreachable by any solid Bessa-parametrized material.
- **Origin:** common-sense extrapolation of the Bessa family's torsion
  axis — σ_cr,nd scales with GJ, and the Bessa optimum sits at only 86%
  of max ratio_J.
- **Stats:** 16-design sweep beyond ratio_J=7.77e-6; 5/16 cleared 75.1 kPa.
  Best (D4) reached σ_cr,nd=83.66 kPa (+28% vs Bessa) but hit only 32% max
  strain (vs the 90% bar); C4 reached just 9%.
- **Verdict:** Stage-1 existence SUPPORTED (mechanism real, floor
  clearable), but Stage-2 FAILS both candidates — the same GJ that clears
  the floor blocks deep coiling. Not a usable design as tested.

</div>

::right::

<div class="flex flex-col items-center justify-center h-full gap-1">
  <img src="/gifs/hollow_tube_D4_native.gif" class="max-h-85 rounded shadow-lg" />
  <div class="text-xs opacity-50 text-center">Native Abaqus render — no strain coloring (see notes). D4 design, Stage-2 diverges at 32% strain.</div>
</div>

<!--
Fuller context:

- This is H5 of run `20260629T191754`, delegation D006 (Stage-1 existence), with
  Stage-2 Riks tests as H4 (max-J single-longeron anchor, FALSIFIED, this same run),
  H6 (D4, FALSIFIED at 32% strain, delegation D007) and H7 (C4, FALSIFIED at 9%
  strain, delegation D008, run `20260630T164908`'s own H1 later reconfirms this
  9%-strain failure pattern is categorical for ANY generalized-section design, not
  just this one). ODB: data/idea_odbs/20260629T191754_H5_extended_J_hollow_tube_D4/
  (source: presentation/resim/hollow_tube/riks_6b8f4808e5e2404fb8b7d33e75b28015),
  the D4 design specifically: n_longerons=3, twist=0, ratio_J=1.2e-5,
  ratio_Ixx=ratio_Iyy=1.4e-6, ratio_pitch=0.5, ratio_top_diameter=0.445325,
  ratio_shear_modulus=0.449.
- Key finding: coilability at J≥9.0e-6 REQUIRES max Iyy=1.4e-6 — lower-Iyy
  ("Set A") designs at the same J lost coilability entirely.
- Same rendering blocker as the n=5-longerons idea above: this ODB's Riks step
  recorded no `E` field output (only RF/RM/U/UR), so render_odb.py's strain-coloring
  step cannot run; rendered here without color as an honest degradation (format
  contract gotcha 5), not fabricated. Both affected ODBs come from the same era of
  the resim pipeline (2026-07-20), before `E` was added to the standard field-output
  request list used by later resims.
- This idea directly set up run `20260630T164908`'s H1 (generalized-section optimum
  fails Stage 2 categorically, 9.23% strain) and motivated the pivot to the Solid
  Circular Longeron Family (next run) as the family that can actually pass Stage 2.
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260629T191754` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** pre-twist family, 46-eval anchor sweep → folds into the
  pretwisted-longerons slide (INCONCLUSIVE, suggestive negative).
- **H2:** multi-storey topology (n_storeys=2) → own idea slide (above),
  INCONCLUSIVE.
- **H3:** n_longerons=5 (extended topology) → own idea slide (above),
  SUPPORTED (mechanism exceeds 65.3 kPa but not the 75.1 kPa floor).
- **H4:** max-torsion single-longeron anchor (n_longerons=3, twist=0) →
  folds into the extended-J slide, FALSIFIED (71.59 kPa, below the
  75.1 kPa floor; motivated H5's search).
- **H5:** extended-J hollow/cellular longeron → own idea slide (above),
  SUPPORTED at Stage 1 (83.66 kPa).
- **H6:** Stage-2 Riks test of the H5 D4 design → folds into the
  extended-J slide, FALSIFIED (32% strain, not 90%).
- **H7:** Stage-2 Riks test of the H5 C4 design → folds into the
  extended-J slide, FALSIFIED (9% strain, even worse).

</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-70 text-center">
Three genuinely new mechanisms this run (multi-storey, n=5 longerons,
extended-J hollow tube) — the extended-J family clears the Stage-1 sigma
floor but categorically fails to actually coil (Stage 2), a pattern that
reshapes every subsequent run's strategy toward circular cross-sections.
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

# Pretwisted longerons

::left::

<div class="text-sm leading-snug">

- **What:** Added a helical pre-twist (twist_angle from π/6 up to π) to each
  longeron of the standard 3-longeron mast, on top of the full 7D Bessa
  cross-section search, to see whether twisting the legs could beat the
  75.1 kPa/longeron study floor.
- **Origin:** common sense mechanistic hypothesis (not a literature
  citation) — the idea that a pre-twisted leg might exploit a shorter
  effective pitch and reach a higher coiling-mode eigenvalue.
- **Stats:** a 46-evaluation anchor sweep (8 twist angles × the
  Bessa-optimal cross-section, plus LHS) — only 6/46 designs stayed
  coilable (13%), and every coilable one was at or below the twist=0
  baseline (65.31 kPa); sigma_cr,nd fell monotonically with twist
  (30° → 52.93 kPa, 90° → 15.69 kPa, all coilable=0 beyond that).
- **Verdict:** the mechanism does not work — pre-twist destroys
  coilability rather than helping it. The registered test technically
  fell short of its own ≥80-eval bar (a license-server outage killed 26 of
  the planned runs), so the formal status is INCONCLUSIVE, not FALSIFIED,
  but the completed 46 evals point the same direction with no ambiguity:
  this is a dead end, not a promising family.


</div>

::right::

<div class="flex items-center justify-center h-full">
  <div class="border-2 border-dashed border-gray-400 rounded-lg p-8 text-center opacity-70 max-w-xs mx-auto">
    <div class="text-3xl mb-2">–</div>
    <div class="text-sm">No ODB: this is a negative result — no design in the pre-twist family
    ever cleared the coilability bar worth preserving, so there is no
    winning geometry to render.</div>
  </div>
</div>

<!--
Fuller context:

- This is H1 of run `20260629T145434` (proposed with zero evals that run — the actual
  46-eval anchor sweep + LHS ran the following run, `20260629T191754`, as that run's
  own H1, delegation D003). Per this deck's rule 1 ("one slide per genuinely new idea,
  earned at the run where it first appears"), the idea's full slide is placed here at
  its origination run; the numbers above are pulled forward from the run that actually
  resolved it, exactly as the tapered-longeron format-example slide does.
- Physical mechanism (per the run's own D002 literature review, Drozdov-Rabin 2000 +
  Gomez-Lauga 2024): path-twist has no theoretical reason to raise the critical
  buckling load for a near-circular cross-section (ν=I2/I1≈1); Gomez-Lauga's own
  analysis shows helical path-twist actually REDUCES effective bending stiffness.
  This is consistent with what the sweep found.
- Full status history: prior 0.6 → 0.35 after the literature-review downgrade → 0.25
  after a second literature check → briefly closed FALSIFIED by the strategizer, then
  the validator flagged that the registered falsification criterion required ≥80
  evaluations and only 46 completed (26 Abaqus runs failed to license-server errors
  during delegation D003) → corrected to INCONCLUSIVE per the study's own charter
  §3 (an inadequate test cannot force a closed FALSIFIED verdict, however suggestive).
- No ODB exists for this family because no design was ever coilable+competitive enough
  to be worth resimulating and archiving — this is one of only two ideas in the whole
  25-idea "genuinely new" list with no ODB by design, not by omission (the other is the
  elliptical cross-section, later this same run-range). The tape-spring idea was a third
  member of this group while its run was still executing; it has since closed with its
  own ODB archived — see its own slide, elsewhere in this deck.
-->

---
layout: two-cols-header
class: summary-slide
---

# Run `20260629T145434` — summary

::left::

<div class="text-sm leading-snug">

- **H1:** pre-twisted longerons proposed as a new mechanism, twist_angle ∈
  [π/6, π] → own idea slide (above); resolved next run, INCONCLUSIVE
  (strongly suggestive negative, underpowered test).
- **H2:** n_longerons ∈ {4, 5} topology axis proposed as a way past Bessa's
  fixed 3-longeron design → folds into the n=5 longerons idea (resolved
  next run as its own H3).


</div>

::right::

<div class="flex items-center justify-center h-full text-sm opacity-60 text-center">
This run proposed two new mechanisms (pre-twist, longeron count) but
completed zero oracle evaluations of its own — both hypotheses were
tested in the following run.
</div>

<!--
Per-hypothesis detail:

- H1 (pre-twisted longerons): statement "twist_angle ∈ [π/6, π] with optimized 7D
  cross-section achieves ≥75.1 kPa/longeron"; prior 0.6; proposed 2026-06-29T15:03:13Z;
  zero evaluations this run (status stayed OPEN at run close). See idea slide above for
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
layout: end
---

# Backlog & full evidence

This deck is now the primary provenance record for the study — every genuinely new
idea and every run's own summary, anti-chronological. `PROBLEM_STATEMENT.md`'s own
"Backlog from previous runs" section still tracks open threads not yet resolved by a
later run; for full per-hypothesis detail beyond what's in any slide's speaker notes,
see `runs/*/debug/strategizer_notes/hypotheses.json`.

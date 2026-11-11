# Wave research

Research date: 2026-11-10. Scope: Part 1 only. No game files changed.

## Sources

Evidence labels distinguish retrieved source text from search-index excerpts. Search summaries are not treated as authoritative measurements.

1. **GD Creator School, Creating Gameplay**, mesoionosphere and contributors:
   [guide](https://www.gdcreatorschool.com/docs/guides/gameplay-1/creating-gameplay/),
   [retrieved source](https://raw.githubusercontent.com/komatic5/gdcs2/main/content/docs/guides/gameplay-1/creating-gameplay.md).
   Directly retrieved. Recommends matching the song's pace and mood, click-pattern-first construction, varied musical motifs, and preparing movement before transitions. Explicitly distinguishes motifs from lazy copy-paste.
2. **GD Creator School, Testing Levels**, illusion2 and contributors:
   [retrieved source](https://raw.githubusercontent.com/komatic5/gdcs2/main/content/docs/guides/the-editor/testing-levels.md).
   Directly retrieved. Discusses trajectory traces, StartPos, music playback and hitboxes; warns that editor physics can differ and recommends testing in normal play too.
3. **Official Geometry Dash Wiki, Portals**:
   [reference](https://geometrydash.wiki.gg/wiki/Portals).
   Direct fetch failed; search-index excerpts retrieved. Wave description states normal vertical speed matches horizontal speed and mini vertical speed is double horizontal speed. Lists ground, ceiling and D-block interactions. Exact collision details and hitbox dimensions could not be independently retrieved.
4. **Geometry Dash Wiki, Portals**:
   [reference](https://geometry-dash.fandom.com/wiki/Portals).
   Search-index corroboration only. Not an independent engine measurement.
5. **Geometry Dash Creators Wiki, Gameplay**:
   [reference](https://geometry-dash-creators.fandom.com/wiki/Gameplay).
   Search-index guidance on readable gameplay and transitions; use as design advice, not a physics specification.
6. **Official Geometry Dash Wiki, Tidal Wave**:
   [reference](https://geometrydash.wiki.gg/wiki/Tidal_Wave);
   [User Levels Wiki entry](https://geometry-dash-user-levels.fandom.com/wiki/Tidal_Wave_(OniLinkGD)).
   Search results identify wave-heavy demanding gameplay. Detailed claims about exact click counts, frame-perfect counts, dual sections and particular obstacles were not independently verified and are intentionally excluded.
7. **Wave Fix, Geode**:
   [reference](https://geode-sdk.org/mods/imes.wavefix).
   Search results suggest version-dependent angle/collision quirks. Direct retrieval failed; insufficient evidence to reproduce those quirks.

### Research limitations

Web browsing was available, but multiple wiki/domain fetches failed. Two Creator School source documents were retrieved successfully. Exact native Wave hitbox dimensions, mini sprite scale, speed-portal velocity table and slope-contact rules remain unconfirmed. Search summaries contradicted one another on these points; no contradictory numeric claim is promoted to fact.

Tidal Wave, Bloodbath, Nine Circles and Sonic Wave are inspiration references, not layout templates. This report does not attribute unverified specific mechanics to individual parts or creators. Bloodbath is a collaboration reference, not evidence that every Extreme Demon is wave-centric. No existing level geometry, names, songs, artwork or source code will be reproduced.

## Real wave physics (with confidence levels)

| Property | Finding | Confidence / evidence |
|---|---|---|
| Normal angle | Vertical speed magnitude equals horizontal speed: a 1:1 slope, therefore 45 degrees relative to horizontal. | High for ratio from wiki search excerpt; angle is a mathematical consequence. Direct wiki retrieval unavailable. |
| Direction changes | Hold travels against current gravity; release travels with it. Direction changes directly, without ballistic gravity integration or accumulated momentum. | High for basic mechanic; not a claim about exact input polling latency in every game version. |
| Mini angle | Vertical magnitude is twice horizontal: slope 2:1, angle arctan(2), approximately 63.435 degrees. | High for ratio from wiki excerpt; angle is calculated, not an independently measured engine constant. |
| Mini size | Mini reduces visual/collision size while increasing vertical coverage relative to horizontal. It is not simply a slower normal Wave. | Medium for qualitative behavior; exact size scale unverified. |
| Gravity portals | Inversion reverses which diagonal hold/release selects; no momentum needs preserving. | High qualitative confidence. |
| Horizontal speed | Automatic horizontal velocity is constant between speed changes; both vertical and horizontal magnitudes scale together so the angle stays fixed. | High qualitative confidence. |
| Portal labels | Slow/normal/double/triple/quadruple labels are categorical names. Do not assume 0.5x/1x/2x/3x/4x are literal numeric multipliers. | Exact velocity table unverified. An early search summary incorrectly asserted literal multiplication; rejected. |
| Hitbox | Collision must be independent of icon artwork and trail glow. A smaller-than-sprite collision proxy is appropriate for this project. | Exact authentic ratio unresolved. Current project ratio 0.52 is a local tuning value, NOT a researched native ratio. |
| Global floor/ceiling | Wiki excerpts distinguish these from ordinary blocks and mention D-blocks. Native Wave can travel along level boundaries; do not model contact as an automatic diagonal bounce. | Medium; reproduce boundary behavior only after a focused verification test. Current project kills on both boundaries. |
| Ordinary blocks | Ordinary solid obstacles are dangerous to Wave; safe rideable surfaces require special handling rather than generic Cube landing rules. | Medium-high qualitative confidence; exact side/contact exceptions unverified. |
| Spikes and saws | Hazard collision is fatal; decoration/glow must not enlarge collision. | High qualitative confidence; exact native hazard hitboxes unverified. |
| Slopes / D-blocks | Special collision treatment exists; a drawn slope must agree with actual collision. | Low for detailed native contact rules. Do not claim all 45-degree slopes are automatically safe or implement unverified slope sliding. |
| Trail | Continuous bright angular line follows the actual path and forms sharp corners at direction changes. Glow surrounds a narrow core; it is not a hazard or hitbox. | High qualitative confidence; exact native width/lifetime unverified. |
| Frame rate | This project should use its existing 120 Hz fixed simulation and render interpolation; decisions must not depend on render FPS. | Project requirement, not a claim that every GD version is perfectly refresh-rate independent. |

### Explicit estimates and implementation decisions for Part 2

- Preserve the current 0.52 collision-to-sprite scale provisionally unless stronger evidence supports replacement. Label it an estimate; do not claim perfect hitbox authenticity.
- Preserve the project's mini visual scale provisionally, separately from the verified mini slope ratio of 2.
- Obtain a reliable speed table before claiming authentic numeric portal speeds. If unavailable, label a project approximation explicitly.
- Fairness thresholds (tier gaps, timing margins, lookahead) are project design choices, not discovered native constants.
- Slopes, D-blocks and dual icons are missing surfaces in the current implementation; they require explicit collision/state integration and tests, not decorative stand-ins.

### Existing implementation mismatch

The existing CONFIG uses `waveSpeed: .72`, a Wave-only horizontal multiplier `.86`, and mini vertical factor `.94`. Its resulting normal slope is .72 (about 35.75 degrees), and mini slope .6768 (about 34.09 degrees): neither matches the researched ratios. The Wave hitbox scale is .52, mini sprite scale .65, and speed categories currently use [.8, 1, 1.2, 1.6]. Physics already assigns Wave vertical velocity directly each fixed step. Floor/ceiling contacts currently kill. Existing challenge routes are authored for the old slopes and must be regenerated with any physics change, not merely reused.

## Segment-type catalogue

These are original construction categories, not copied level parts. Tiers T1-T5 are proposed project tiers, not official GD ratings: T1 controlled foundation/breather, T2 demanding, T3 hard precision, T4 intense, T5 peak precision/endurance. Tier depends on actual speed, width, timing and duration, not just the name.

| Name | Description | Skill tested | Tier |
|---|---|---|---|
| Rising diagonal | Long open upward line | Hold duration | T1-T2 |
| Falling diagonal | Long descending line | Release duration | T1-T2 |
| Hold-release arch | Two long opposing diagonals | Controlled reversal | T2 |
| Offset long holds | Unequal rising/falling distances | Asymmetric timing | T2-T3 |
| Needle click | Brief ascent between long descents | Short isolated press | T3-T4 |
| Needle release | Brief descent between long ascents | Short isolated release | T3-T4 |
| Short spam burst | Short finite alternating run | Tap cadence | T3-T4 |
| Sustained spam | Longer rhythmic alternation, then recovery | Consistency/endurance | T4-T5 |
| Straight precision lane | Narrow diagonal band | Hold/release accuracy | T3-T5 |
| Wide slalom | Broad alternating turns | Flow and anticipation | T1-T2 |
| Staircase up | Offset apertures gaining height | Position planning | T2-T3 |
| Staircase down | Offset apertures losing height | Release control | T2-T3 |
| Slope chase | Visible diagonal wall borders route | Parallel-path precision | T3-T4 |
| Slope reversal | Two opposing diagonal borders | Corner timing | T3-T4 |
| Even zigzag | Regular alternating route | Stable rhythm | T2-T3 |
| Swing zigzag | Long-short alternating lengths | Rhythm differentiation | T3-T4 |
| Broken triplets | Three turns then a hold | Grouped inputs | T3-T4 |
| Funnel entry | Wide entrance narrows gradually | Accurate setup | T2-T4 |
| Funnel exit | Narrow start opens to recovery | Sustained control then release | T2-T4 |
| Pillar slalom | Clearly separated vertical columns | Early altitude changes | T2-T4 |
| Diamond pocket | Diagonal enclosure with readable exit | Turn placement | T3-T4 |
| Hourglass neck | Spacious ends and narrow midpoint | Centering | T3-T5 |
| Spike-lined channel | Spikes visibly define safe route | Margin control | T3-T5 |
| Floating islands | Blocks partition open air | Route selection | T2-T4 |
| Saw necklace | Static saws define diagonal windows | Circular-hitbox clearance | T3-T5 |
| Orbit saw crossing | Predictable moving saws cross nearby | Phase anticipation | T4-T5 |
| Moving wall passage | Slow wall motion with protected entry | Motion reading | T3-T4 |
| Moving gate | Visible periodic opening | Phase timing | T4-T5 |
| Pulse aperture | Bounded rhythmic gap variation | Beat/clearance awareness | T3-T4 |
| Gravity inversion | Portal swaps input interpretation | Control inversion | T2-T4 |
| Inversion echo | Reversed motif with different rhythm | Adaptation | T3-T4 |
| Mini precision | Steeper mini flight in small apertures | Vertical sensitivity | T3-T5 |
| Mini-to-normal | Size changes in an open chamber | Slope recalibration | T2-T4 |
| Fast 2x category | Faster readable diagonals | Anticipation | T3-T4 |
| Fast 3x category | Shorter reaction budget | Timing consistency | T4-T5 |
| Fast 4x category | Peak-speed finite run | Precision under speed | T5 |
| Speed step | Telegraph speed increase before route | Adaptation | T3-T4 |
| Speed recovery | Speed decreases into breather | Restraint | T1-T2 |
| Mirrored dual | Two visible compatible paths, one input | Shared timing | T3-T4 |
| Asymmetric dual | Different paths with a common solution | Split attention | T4-T5 |
| Wave-to-Ship handoff | Clear exit into centered flight | Momentum-mode transition | T2-T4 |
| Wave-to-Cube handoff | Clear exit to safe landing/run-up | Landing setup | T2-T4 |
| Drum phrase | Turns align to selected drum accents | Audio timing | T2-T4 |
| Syncopated phrase | Rests and off-beats interrupt regular taps | Rhythm learning | T3-T5 |
| Endurance weave | Related motifs develop over a long phrase | Consistency | T4-T5 |
| Low-noise colour drop | Palette changes; collision stays stable | Visual adaptation | T2-T3 |
| Fog-free silhouette peak | Strong outlines over decorative motion | Focus | T3-T4 |
| Recovery balcony | Wide route after intensity | Controlled recovery | T1 |

## Difficulty and pacing principles

1. Build an input rhythm, simulate its real fixed-angle trajectory, then construct visible geometry with clearance. A bot witness proves a route exists, not that humans can learn it.
2. Require timing slack at 60 FPS. Test early and late inputs, not only a perfect tape. A proposed floor is at least three consecutive 60 Hz input placements for required clicks; report the tested window rather than claiming fairness from gap width alone.
3. Measure a corridor normal to its local direction as well as vertically. Diagonal corners, player extent, speed and mini slope all affect usable slack.
4. Maintain at least 0.5 seconds of unobscured lookahead at the current maximum local speed, including after camera, speed, size and gravity changes.
5. Separate precision, cadence and endurance. A hard section can demand accurate long holds; difficulty need not mean maximal clicks per second.
6. Use six musical phases: intro, build-up, drop, breakdown, harder second drop, finale. Peak intensity belongs in the final third, with recovery after sustained T4/T5 sequences.
7. Make Medium demanding predominantly through T2/T3 control. Hard uses T3/T4 and bounded T5 peaks, not unbroken maximum difficulty.
8. Place mode/size/gravity transitions in clear space. Test incoming trajectories and outgoing recovery, not only the middle of a segment.
9. Keep collision readable during drops and visual changes. High contrast and reduce-flashing must preserve exactly the same physical route.
10. Playtest full runs and isolated parts; fixed-step witnesses do not measure frustration, attempt counts or enjoyment.

### Collab-style variety without copying collaborators

Use three or four original designer profiles per Wave level. Profiles change geometry, rhythm vocabulary and palette together, while a shared specification controls hitbox, fairness, musical beat grid and transitions.

- **Precision:** isolated clicks, narrow diagonals and clean angular outlines.
- **Flow:** long asymmetric holds, wide sweeps and curved decorative backgrounds.
- **Pulse:** short rhythmic bursts, accents and high-contrast gate silhouettes.
- **Endurance/Gimmick:** extended motifs, mini/gravity changes and one predictable moving mechanic.

Assign whole musical phrases to profiles rather than randomly swapping every obstacle. Give each profile its own motif vocabulary and one variation; retain a unifying palette accent and music loop. Validate handoff height, slope, gravity, size, speed, held-input state and preview distance at every seam. A shared tier budget prevents a collaborator-style section from becoming an accidental difficulty spike. These are proposed project design principles, not verified claims about how any named real collaboration was managed.

Each level also needs one signature mechanic independent of profile: for example phased saw clearances, alternating mini sensitivity, diagonal precision gates, or inversion-and-rest rhythms. Repeated motifs must change meaningful gameplay, not just colour.

## Pitfalls to avoid

- Literal interpretation of speed-portal labels as numeric multipliers.
- Presenting an estimated hitbox or mini scale as a confirmed engine value.
- Confusing decoration, trail glow or a saw's visual rays with collision.
- Assuming floor/ceiling, ordinary blocks and special D-block surfaces behave identically.
- Frame-perfect gates, FPS-dependent input sampling, or variable-timestep collision.
- Constant high-frequency spam disguised as segment variety.
- Hidden/fake hazards, unsupported slope collision, or visual noise masking the route.
- Random moving hazards whose safe phase depends on unrelated timing.
- Hard transitions immediately after portals without incoming-state validation.
- Copy-pasted section geometry with only a palette change.
- A perfect bot tape used as the sole claim of human fairness.
- Claiming named levels contain particular sequences or exact timing counts without confirming them.
- Enforcing ten distinct types on a 12-second four-segment challenge without clarifying whether micro-patterns or challenge exceptions satisfy that requirement. This must be resolved before Part 2 generation rules are finalized.

## WAVE DESIGN CHECKLIST

Mark each rule PASS/FAIL per rebuilt level in the later audit. These are acceptance criteria, not claims that the current game already passes.

1. [ ] Normal Wave has absolute vertical/horizontal ratio 1 within numeric tolerance.
2. [ ] Mini Wave has ratio 2; scale and hitbox assumptions are documented.
3. [ ] Press/release changes direction in one fixed step with no momentum.
4. [ ] Gravity inversion swaps directions without changing slope magnitude.
5. [ ] Speed categories use a sourced table or are explicitly labelled approximations; both axes scale together.
6. [ ] Measured trajectories and survival agree at 60/120/144 Hz rendering.
7. [ ] Sprite, trail, hitbox and collision-debug display remain separate and consistent.
8. [ ] Floor, ceiling, block, spike, saw and slope/special-surface rules are explicit and tested.
9. [ ] Every segment has name, tier, skill, supported speeds and hazard metadata.
10. [ ] At least 40 genuinely distinct segments exist across the library.
11. [ ] Each full Wave level contains at least ten distinct types; short-challenge policy is explicitly resolved.
12. [ ] No adjacent repeat; no type more than twice per finite level; repeats change gameplay.
13. [ ] Every level uses three or four visibly and mechanically distinct designer profiles.
14. [ ] Every level has an original signature mechanic, palette and generated loop.
15. [ ] All required hazards/portals are readable at least 0.5 seconds ahead at local speed.
16. [ ] Tightest usable clearance meets configured tier margins, including mini and diagonal corners.
17. [ ] Required inputs have tested early/late slack at 60 Hz; no one-frame-only solution.
18. [ ] Real-physics witnesses survive all segments, full levels and transition seams.
19. [ ] Long holds, short clicks, rests and spam bursts have deliberate varied distributions.
20. [ ] Intense stretches have shorter breathers; difficulty rises and peaks in the final third.
21. [ ] Musical phase/beat alignment is checked using actual travel times, including speed changes.
22. [ ] Dual paths share a verified input solution; neither icon or route is decorative-only.
23. [ ] Endless uses reproducible seeds, five-segment memory, tier ramp, breathers and 20-30 second style changes.
24. [ ] Reduce-flashing/high-contrast preserve collision and readability; moving hazards have deterministic phases.
25. [ ] Reports include clearance, longest hold/spam, distinct types, repeats, similar runs and tier curve; human playtesting limitations are stated.

## Part 1 stop

Research complete within the evidence limitations above. Part 2 has not started. Wait for the user's explicit "continue"; then follow steps A-F and timed check-ins. Before changing physics, resolve how the ten-type rule applies to existing short Extreme Wave challenges and keep unverified numeric choices labelled as estimates.

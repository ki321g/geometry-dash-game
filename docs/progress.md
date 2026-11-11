# Wave revision progress

## Repository setup

- START: 07:49:26 (2026-11-11, terminal local time).
- Scope: Repository/deployment files only; game code and behaviour unchanged.
- Inspection: Root index.html and three docs files; scripts/styles are inline.
  No apparent secrets, private data, environment files or absolute asset paths
  found. No existing Git repository. Existing Git author configuration is set.
- Files added: .gitignore and README.md. Vercel config is unnecessary for this
  static root-index layout. No licence, package manifest or build step added.
- Publishing blocker: GitHub CLI is not installed; gh auth status could not run.
  Do not use alternate credentials or API tools to bypass this blocker.
- Current time: 07:50:59. Initialised main and reviewed six staged files:
  .gitignore, README.md, index.html and all three existing docs. No remote.
  Configured the user-requested commit email locally without changing global
  settings. Original index.html SHA256 remains
  E639015FFDB389FA3001A178795831E8669F9BE044C18DE49198E3B66A689C3B.
- Next action: Create the requested initial local commit, verify clean status,
  then hand over manual publication to an empty geometry-dash-game repository
  in the user's intended GitHub account. GitHub CLI is absent, so repository-name
  availability and remote publication remain unverified. No Vercel deployment
  has been attempted. Broader game work is not authorised by this setup task.
- Prior Wave overhaul remains paused; known Speed trial timing failures remain.

- START: 14:24:39 (2026-11-10, terminal local time).
- New task START: 15:15:52 (2026-11-10). User requested a special fun endless seed `67-67`; prior Wave audit remains paused. This request authorizes only the special-seed work, not the unfinished audit.
- Special-seed implementation: `67-67` enables FLOW PARTY, an orb-rich profile with predictable three-sector mode medleys, normal-size icons, slower gravity changes, capped scroll speed, regular recovery sectors and T1-T3 Wave routes excluding dual/mini patterns. Selected single-mode filters are preserved. Other seeds retain existing generation. Files changed: index.html and docs/progress.md. Validation next: actual witness replay, repeatability, restart/cache and every mode filter.
- Last approved work start: 15:15:52 (new special-seed request only; broader Wave work still paused).
- Current time: 15:20:28; special-seed work finished within the approved interval.
- Scope: Special seed `67-67` implemented; no resumption of the paused A-F audit.
- Completed: Read existing Wave CONFIG, physics, collisions and trail surfaces. Retrieved Creator School gameplay/playtesting source documents; reviewed wiki search excerpts. Wrote docs/wave-research.md with sources, confidence-labelled mechanics, 48 segment categories, pacing/collab profiles, pitfalls and 25 acceptance rules. Verified unchanged index.html embedded JavaScript parses; no standalone .js files were found.
- Special-seed validation: PASS embedded JavaScript syntax, actual full input-tape replay over 26 sectors for All modes and all seven single-mode filters, deterministic cached restarts, normal-size and capped-speed assertions, all seven modes represented in the medley, T1-T3 non-dual Wave sectors, and adjacent seed `67-68` using ordinary generation. Mixed run: 69 orbs / 38.1 per minute; non-Wave filters about 39-41 per minute. Wave continues to ignore decorative orbs, unchanged. Profile music, generated hazard tempo and HUD use the same 132 BPM level metadata. Existing full regression launched; result pending at this timestamp.
- Completion: Existing full gameplay regression exited successfully (shell 63, exit 0). Special-seed targeted tests and all-mode regression pass. No background commands remain. Browser play-feel was not tested; "fun" is a design intention, not a measured outcome. Prior Wave Speed timing audit remains paused and unresolved.
- User decision: Keep four full sections in the short Extreme Wave challenge, with at least ten distinct micro-patterns inside them; do not exempt it from variety.
- Files changed so far: index.html, docs/progress.md, docs/wave-research.md, docs/wave-config-changes.md; session-only revisions-test.cjs.
- Known problems: Direct wiki fetches failed. Exact native hitbox ratio, mini size, portal speed table and slope/D-block contact details remain unverified and are explicitly marked. User supplied the previously missing instructions. Ten-type-per-level rule conflicts with the existing four-segment, sub-20-second Wave challenge unless micro-patterns or an exception are approved.
- Completed since continuation: Normal Wave slope 1, mini slope 2; removed Wave horizontal slowdown; direct icon angle; boundary clamping; slope-aware challenge routes; Settings > Visuals > WAVE TEST course. Added direct mechanics tests and documented all CONFIG changes.
- Known validation problems: Legacy coarse 80 ms Wave controller fails Medium at x=13433.6 and Hard at x=4130.1. All finite perfect witnesses and exact mechanics tests passed. This proxy predates authentic slope changes; timing-window validation and demanding fair layouts remain Step B/F work. Native hitbox/speed/slopes uncertainties remain as documented.
- Completed since continuation: Added explicit T1-T5 gaps, speed/player-aware timing clearance, tier curves/breathers, 75 ms minimum mini challenge input duration and 0.5-second preview checks. Added PHASE.validateWave: both Wave trials and VECTOR LAB pass all tested +/-25 ms protected-corridor input perturbations. Added Wave refresh-rate/boundary assertions. Existing challenge gap constant no longer drives Wave clearance; waveGap does.
- Known validation problems: The general harness was interrupted by a legacy challenge assertion requiring multiple 50 ms mistakes to kill; Wave fairness intentionally increased that slack. Updated Wave challenge destructive perturbations to 100 ms, pending rerun. Coarse 80 ms beginner-control test is opt-in only. Native speed/hitbox uncertainties remain explicit. Full audit not yet run.
- Completed since continuation: Expanded Wave data to 48 descriptors with tier, skill, supported speed categories, hazards, geometry, mini and rhythm metadata. Replaced sine-following Wave control with authored hold/click rhythms; added four visible designer palettes and style-biased selection; moving/pulse channels, geometric width variations and meaningful rhythm changes on repeats. All-mode regression suite now passes. Both rebuilt Wave trials pass all tested +/-25 ms timing perturbations.
- Remaining Step C work: Dual descriptors are named but dual-icon collision/rendering is NOT implemented yet; do not claim these segments complete. Further geometry/profile differentiation and complete catalogue coverage checks remain. Five-category speed data exists but still needs wiring. Ten-types-per-short-challenge policy still needs confirmation. Steps D-F remain pending.
- Completed since continuation: Real mirrored/offset dual Wave icons, both-player hazard/block collision, both route outlines and trails, dual portal; provisional five speed-category wiring; 12 distinct micro-patterns inside four short challenge sections. Added PELAGIC ODYSSEY Marathon (172.975 seconds) and CHROMATIC OVERDRIVE Speed trial (60.775 seconds); six-phase structure scales over their lengths. Endless Wave uses five-entry recent memory and style changes by 24-second world-time buckets. Added per-entry witnesses for all 48 patterns and a real second-icon collision test.
- Validation findings: Medium Wave trial, Hard Wave trial and Marathon PASS every tested +/-25 ms corridor-edge perturbation. Speed trial FAILS: speed-step 12/26, mini-precision 15/34, offset-holds 1/22, speed-recovery 11/22 timing perturbations (first four reports). Perfect witnesses still pass. Do not describe the Speed trial as human-fair until corrected.
- Exact next action: Wait for user feedback on FLOW PARTY. To resume the broader task, wait for "continue" and record a fresh approved time; fix fast-mini clearance/corner timing windows in CHROMATIC OVERDRIVE without changing authentic slopes. Then complete supported-setting audits and docs/wave-audit.md.
- Check-in rule: Before each new work batch run Get-Date -Format "HH:mm:ss". Current special-seed deadline is 15:20:52. If still working at that time, stop safely and ask "Five minutes have passed. Do you want me to continue?" A user-approved continuation resets the last approved check-in.
- Validation: PASS embedded game syntax and node --check session script. Latest targeted Wave regression passed, including all 48 individual pattern witnesses, real dual collision, refresh-rate identity, short challenge micro-variety and new level perfect witnesses. Medium/Hard/Marathon timing audits pass; Speed timing audit fails as above. Full all-mode regression after newest changes remains pending. No background commands remain running. Game runs from index.html, no partial functions or stubs.

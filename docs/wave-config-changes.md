# Wave CONFIG changes

Step A checkpoint, 2026-11-10.

| Value | Old | New | Reason |
|---|---|---|---|
| waveSpeed | 0.72 | 1 | Normal Wave uses a 1:1 diagonal (45 degrees). |
| waveMiniSlope | absent (inline factor 0.94 times waveSpeed) | 2 | Mini uses twice the horizontal velocity vertically (approximately 63.435 degrees). |
| tuning[2].speed | 0.86 | 1 | Remove mode-specific horizontal slowdown; shared scroll/speed scaling applies consistently. |
| waveSpeedCategories | absent | [.806, 1, 1.243, 1.502, 1.849] | Explicit provisional approximation for five named categories; not yet wired to level generation and not claimed exact native values. |
| waveTierGap | absent | [240, 204, 172, 144, 120] pixels | T1-T5 vertical clearance floors before dynamic player/speed allowances. |
| waveTimingMargin | absent | .05 seconds | Dynamic clearance reserves timing slack at actual vertical speed. |
| waveMinPreview | absent | .5 seconds | Minimum visible lookahead acceptance threshold. |
| waveMinInputDuration | absent | .075 seconds | Prevent mini challenge click lengths collapsing to frame-perfect inputs. |

Step B checkpoint: added `validateWave(level)` to PHASE. It replays real physics and tests each protected-corridor direction change 25 ms early and late. Both Wave trials and VECTOR LAB pass these perturbations with tiered gaps. The old 80 ms ease controller is now opt-in via `--legacy-wave-input`; it is not the acceptance test for demanding Wave behavior.

Later integration: five provisional Wave speed categories are now wired to fast/recovery patterns and the Speed trial. They remain explicit approximations, not confirmed engine constants. Other modes keep their existing speed behavior. Added 48 authored-rhythm descriptors, dual collision/rendering, Marathon and Speed trials. Marathon passes timing perturbations at 172.975 seconds; the Speed trial still has fast-mini timing failures and is not yet accepted as fair. Final audit pending.

Unchanged provisional estimates: Wave hitbox scale 0.52, mini visual scale 0.65. Neither is claimed to be a confirmed native engine ratio. The existing [.8, 1, 1.2, 1.6] project speed categories remain unchanged; an authentic five-category mapping is not implemented or claimed.

Related behavior changes: Wave global floor/ceiling contact clamps to the boundary rather than killing; ordinary blocks and hazards remain fatal. Wave icon rotation now follows the actual diagonal rather than multiplying its angle by 0.65. Challenge trajectories regenerate at the current mini/normal slope instead of reusing paths authored for the previous physics.

Debug course: Settings > Visuals > WAVE TEST launches VECTOR LAB with fixed authored corridors and normal/mini transitions. It is not a scored selectable campaign level.

Validation at this checkpoint: exact normal/mini ratios, all four current speeds, both gravities, immediate reversals and debug-course witness pass. All finite-level perfect witnesses pass. The legacy 80 ms coarse Wave controller fails both trials under the authentic physics; it was written for the previous easier Wave and is not the final human-window validator. Step B/F must replace this proxy with measured timing slack; do not report the entire legacy suite as passing.

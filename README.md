# PHASE / Neon Run

An original Geometry Dash-inspired rhythm platformer built with plain HTML, CSS
and vanilla JavaScript. Canvas draws the game and menus, while Web Audio generates
music and sound effects. The self-contained game includes portals, jump orbs,
customisable skins, settings and local progress saving, with no external assets,
dependencies or build step.

Live demo: (add your Vercel URL here)

## Controls

- Click, tap, **Space** or **Up Arrow** to act; hold for continuous input where the
  current mode supports it.
- Press near an orb to activate it; holding does not automatically activate orbs.
  Wave ignores orbs.
- **P** or **Escape** pauses/resumes play.
- The jump key can be changed in Settings.

## Modes and levels

Seven modes: **Cube, Ship, Wave, Ball, UFO, Robot and Spider**.

### Campaign

| Medium | Hard |
| --- | --- |
| Prism Engine | Violet Velocity |
| Tidal Circuit | Hotline Shift |
| Chroma Relay | Solar Fracture |

### Mode Trials

Each of the seven modes has a **Trial I (Medium)** and **Trial II (Hard)**:
Cube Trial, Ship Trial, Wave Trial, Ball Trial, UFO Trial, Robot Trial and
Spider Trial.

Two additional Hard Wave trials are **Pelagic Odyssey** (Marathon) and
**Chromatic Overdrive** (Speed).

### Challenges

Eight short **Extreme** challenges, capped at 20 seconds:
**Triple Threat**, **Ion Needle**, **Razor Signal**, **Polarity Panic**,
**Hop Overload**, **Vault Breaker**, **Snap Judgement** and **Extreme Relay**.

### Endless and debug course

**Infinite Signal** provides seeded procedural endless play with all modes or a
single-mode filter. Seed **67-67** unlocks **Flow Party**, with extra orbs,
controlled speeds and regular breathers.

**Vector Lab** is the debug Wave test course, available through Settings >
Visuals > Wave Test.

## Run locally

Open `index.html` directly in a modern browser. Alternatively, open this folder
in Visual Studio Code and use the Live Server extension to serve `index.html`.
No installation or build command is needed. Interact with the game to enable
browser audio.

## Deploy

Deploy with **Vercel as a static site**:

1. Sign in to Vercel with GitHub and select **Add New > Project**.
2. Import this repository.
3. Set **Framework Preset** to **Other** and **Root Directory** to the repository
   root.
4. Leave **Build Command** unset and use the root (`.`) as **Output Directory**.
   No install command or environment variables are required.
5. Deploy, then replace the live demo placeholder above with your Vercel URL.

No `vercel.json` is required: `index.html` is already at the repository root.

## Development notes

Research and implementation history are retained in `docs/`. The Wave overhaul
audit is unfinished; known fast-mini timing-margin failures in Chromatic
Overdrive are recorded in `docs/progress.md`. Repository setup does not change
game code or resolve those gameplay issues.

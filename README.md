# The Lost Blade — Indie Pixel Platformer

**Created by Djamel**

A horizontal, medieval pixel-platformer prototype built for Defold and prepared for Android.

## What changed in v1.1

### Character controller
- Deterministic 60 Hz gameplay loop.
- Acceleration/deceleration instead of instant movement.
- Air control.
- Coyote time for forgiving jumps.
- Jump buffering so a jump pressed just before landing still registers.
- Fall-speed cap.
- One-way platform collision with stable landing resolution.
- Moving platforms with sine-wave motion.
- Slide/roll with a lower body height and speed burst.
- Death sequence before respawn.
- Checkpoint respawn.

### Character animation state machine
- Idle.
- Run: 6 supplied frames.
- Jump.
- Fall.
- Landing.
- Slide.
- Death: 3 staged frames + rotation.
- Bored/idle-too-long animation.
- Sword-carry animation for the ending.

The supplied knight frames remain the core visual identity; the additional states are deliberately restrained rather than adding glossy procedural effects.

### Presentation
- Rebuilt 320×180 pixel-art backgrounds and nearest-neighbour scaling for a chunky indie look.
- Green watchtower descent.
- Broken crypt with masonry, candles and arches.
- Dragonfall cavern with bones, lava channels and an altar.
- Crisp nearest texture filtering.
- Sprite subpixels disabled.
- Fixed-fit projection to avoid stretching across unusual aspect ratios.
- Safe-area aware GUI.
- Landscape-first 1280×720 design.

Defold recommends nearest filtering for pixel-perfect graphics and supports fixed-fit projections for maintaining the designed aspect ratio across different screens. See the official Defold documentation for texture filtering and screen-size adaptation. 

### Mobile controls
- Left.
- Right.
- Jump.
- Roll.
- Pause.
- Large touch targets intended for landscape phones.
- Mouse input also works for desktop testing.

### Audio
- Menu music.
- Separate music tracks for all three chapters.
- Jump, death, checkpoint, collect, sword, slide, landing, secret and UI feedback sounds.

### Game systems
- 3 chapters.
- Multiple checkpoints in later chapters.
- Moving-platform routes.
- Optional secret relic in every chapter.
- Endless-lives code: `Djamelistheking`.
- Cutscenes and chapter transitions.
- Final sword pickup/carry moment.
- Dragon-skull ending.

## Controls

### Keyboard
- A / Left Arrow — move left
- D / Right Arrow — move right
- Space / W — jump
- S / Down Arrow / Shift — roll/slide
- Esc — pause
- R — restart chapter
- M — menu

### Mobile
Use the on-screen buttons in landscape mode.

## Android notes

Package: `com.djamel.thelostblade`

Version: `1.1.0` / version code `2`

The project is source-ready for a Defold Android build. A signed release APK still needs the normal Defold/Android SDK + signing step on the machine/CI that performs the build.

## Project structure

- `main/` — collections, factories and game objects
- `scripts/` — controller and GUI logic
- `assets/` — pixel art and animation frames
- `sound/` — music and SFX
- `input/` — controls

## Important implementation note

The player movement is a deterministic custom 2D controller. Defold's physics settings are also configured for a fixed 60 Hz timestep, but level collision is resolved by the controller so the platforming feel remains predictable and consistent across mobile frame rates.

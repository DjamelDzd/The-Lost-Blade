# The Lost Blade — Indie Pixel Platformer

**Created by Djamel**

A horizontal, medieval pixel-platformer prototype built for Defold and prepared for Android.

## Open in Defold

1. Install Defold 1.13.1 or a newer stable editor.
2. Open this repository folder in Defold and select `game.project`.
3. Use **Project → Build** for a desktop debug build, or **Project → Bundle → Android Application** for a phone build.

The project is fixed to a 1280×720 landscape design. Dynamic orientation is disabled so a phone does not rotate the game into portrait mode. Defold's fixed-fit projection and safe-area-aware GUI keep the 16:9 design usable on wider phone aspect ratios.

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

## GitHub Actions Android builds

The repository includes `.github/workflows/android.yml`.

- **Push to `main`**: builds a debug APK automatically.
- **Manual build**: open **GitHub → Actions → Android Build → Run workflow**, then choose `debug` or `release`.
- **GitHub Release**: publishing a release/tag runs the workflow and attaches `The-Lost-Blade-Android.apk` to that release.

The workflow downloads the pinned official Defold Bob builder (`1.13.1`), uses Java 25, builds for `arm64-android`, and uploads the APK as an Actions artifact. A release request without signing secrets safely falls back to a debug APK; it never claims to have produced a signed release APK.

For a signed release build, add these GitHub Actions secrets:

- `ANDROID_KEYSTORE_BASE64` — base64-encoded `.keystore` file
- `ANDROID_KEYSTORE_PASSWORD` — keystore password
- `ANDROID_KEY_ALIAS` — signing key alias
- `ANDROID_KEY_PASSWORD` — signing key password

Do not commit the keystore or any of these values. Debug builds do not require signing secrets.

### Build an APK from GitHub

1. Push the project to GitHub.
2. Open the repository's **Actions** tab and select **Android Build**.
3. Select **Run workflow**, choose `debug`, and run it.
4. Open the completed workflow run and download the `The-Lost-Blade-Android-debug` artifact.

For a signed distributable build, configure the four secrets first, then choose `release`. To publish the APK on a release page, create and publish a tag-backed GitHub Release such as `v1.1.0`. The release workflow uploads the APK only after Bob completes successfully.

## Project structure

- `main/` — collections, factories and game objects
- `scripts/` — controller and GUI logic
- `assets/` — pixel art and animation frames
- `sound/` — music and SFX
- `input/` — controls
- `.github/workflows/android.yml` — reproducible debug/release Android builds

## Important implementation note

The player movement is a deterministic custom 2D controller. Defold's physics settings are also configured for a fixed 60 Hz timestep, but level collision is resolved by the controller so the platforming feel remains predictable and consistent across mobile frame rates.

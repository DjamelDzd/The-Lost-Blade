# The Lost Blade — QA / Device Compatibility Checklist

## Reference rendering
- Logical resolution: 1280×720
- Orientation: landscape
- Texture filtering: nearest
- Sprite subpixels: disabled
- Safe area: both
- VSync: enabled
- Update target: 60 Hz

## Aspect ratios to simulate in Defold
1. 1280×720 — 16:9 baseline
2. 1600×900 — 16:9 large screen
3. 1920×1080 — 16:9 desktop / tablet
4. 2340×1080 — 19.5:9 phone
5. 2400×1080 — 20:9 phone
6. 2520×1080 — 21:9 phone

## What to verify
- Game remains landscape.
- HUD stays inside the safe area.
- Touch buttons remain tappable near notches/cutouts.
- No important level geometry is clipped by aspect-ratio changes.
- Pixel art remains crisp.
- Player cannot tunnel through the top of a platform during a normal jump.
- Landing does not jitter.
- Coyote time works at platform edges.
- Jump buffering works just before landing.
- Slide lowers the player body and ends cleanly.
- Moving platforms remain deterministic.
- Death always returns to the latest checkpoint unless lives are exhausted.
- `Djamelistheking` keeps lives infinite.
- Menu, pause, chapter transitions and ending remain responsive.

## Release checklist
- Test debug build on a physical Android phone.
- Test release APK/AAB with a real signing key.
- Test cold start, resume, pause and orientation lock.
- Test audio after background/foreground transitions.
- Verify package name: `com.djamel.thelostblade`.
- Replace the temporary/default application icon before store distribution.

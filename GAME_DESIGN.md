# THE LOST BLADE — Game Design / Polish Pass

## Identity

**Genre:** 2D medieval pixel-platformer / parkour

**Orientation:** Landscape

**Visual target:** High-pixelated indie game — restrained palette, readable silhouettes, chunky pixels, minimal glow and no excessive AI-like decoration.

**Creator:** Djamel

## Core fantasy

You are a nameless knight whose sword disappears into a deep underground descent. The kingdom believes the blade was lost in battle. The player slowly discovers that the fall leads somewhere much older.

The final scene shows the recovered blade resting above a dragon skull. The knight lifts it. The legend is born: everyone will assume the dragon was slain by one heroic blow. The game ends before the player learns whether that story is true.

## Character states

1. Idle
2. Run
3. Jump
4. Fall
5. Landing
6. Roll / Slide
7. Death
8. Bored idle
9. Sword carry

Animation changes are state-driven, not random. The original six knight frames are reserved for the main run cycle; derivative frames are used for non-running states.

## Movement feel

- 60 Hz fixed gameplay step.
- Acceleration gives weight to the knight.
- Friction produces a controlled stop.
- Coyote time makes edge jumps fair.
- Jump buffering prevents missed inputs at landing.
- Air control is weaker than ground control.
- Slide lowers the collision body and gives a short burst.
- Fall speed is capped for predictable recovery.

## Level philosophy

Every chapter teaches one new idea and then combines it with earlier ideas.

### Chapter I — The Green Descent
- Safe opening platforms.
- First spikes.
- High secret route.
- First moving platforms.
- Raven Relic.

### Chapter II — The Broken Crypt
- More vertical routing.
- Narrower platforms.
- Candle-lit visual landmarks.
- Two checkpoints.
- Crypt Sigil.
- Moving platforms form optional shortcuts.

### Chapter III — Dragonfall
- Longer jumps.
- Lava/bone atmosphere.
- Multiple moving-platform choices.
- Two checkpoints.
- Dragon Oath.
- Lost Blade and dragon skull finale.

## Secrets

Each chapter contains one secret relic. Secrets are positioned away from the obvious route and are intended to reward exploration rather than raw speed.

## Mobile design

- 1280×720 logical landscape reference.
- Safe-area aware GUI.
- Fixed-fit rendering to reduce stretching on wide/tall aspect ratios.
- Large touch buttons with separation between movement and jump/roll.
- Immersive Android mode.

## Audio direction

Menu: quiet medieval atmosphere.

Chapter I: open medieval adventure.

Chapter II: darker crypt ambience.

Chapter III: tense subterranean/dragon atmosphere.

Effects should stay short and dry rather than becoming cinematic trailer effects.

## Anti-AI aesthetic rules

- Do not add random neon effects.
- Avoid excessive bloom.
- Keep the palette chapter-specific.
- Use deliberate pixel clusters.
- Reuse motifs: banners, stone, grass, candles, bones, old wood.
- UI uses simple dark plates and typography rather than glossy gradients.
- Animation is readable first and decorative second.

# Times Table Battle Arena — V2 Game Feel Upgrade

## Goal
Turn the functional multiplication prototype into a real mobile game where maths powers the action instead of replacing it. In the first 10 seconds the player should already see moving enemies, soldiers firing, projectiles, hits, score feedback and usable combat UI.

## Core loop
1. Enemies continuously advance toward the base across three lanes.
2. Soldiers auto-fire while the player taps enemies to focus fire.
3. Supply crates appear between questions and can be tapped for energy.
4. Maths challenges appear roughly every 20–30 seconds; battle slows but does not fully stop.
5. Correct answers add soldiers, energy, combo, power and score. Wrong answers trigger an enemy rush and immediate corrective feedback.
6. Energy is spent on Power Shot, Shield and Bomb skills.
7. A multi-phase Boss arrives late in the run while normal minions continue spawning.
8. Results open with animated loot, coin rain and XP/reward feedback.

## Must-have 1–10 implementation

### 1. Continuous enemies
Small, medium and large enemies continuously spawn, move toward the base and deal different damage. Difficulty rises through the run.

### 2. Soldiers visibly fight
Soldiers are rendered as animated characters on the battlefield. They continuously fire visible projectiles. Hits create particles, HP changes and floating score text.

### 3. Strong correct-answer feedback
Correct answers trigger green screen feedback, combo pop-up, particles, SFX, extra soldiers, energy gain and stronger firepower. Boss shields can be broken by a correct answer.

### 4. Strong wrong-answer feedback
Wrong answers trigger red feedback, corrective answer text and an immediate temporary enemy rush instead of a passive score penalty.

### 5. Play between questions
The player can tap enemies to choose a focus target, collect supply crates, decide when to spend energy and watch/affect the live battle between maths interactions.

### 6. Three skills
- Power Shot — 25 energy: large single-target critical hit.
- Shield — 35 energy: strongly reduces base damage for 8 seconds.
- Bomb — 60 energy: large area damage with screen flash and explosions.

### 7. Multi-phase Boss
Boss arrives with a warning cinematic and dedicated HP bar. It has three phases, restores its shield on phase changes and summons additional minions. Normal enemies continue attacking during the Boss fight.

### 8. Colourful stage themes
Each run selects one of four themes: Meadow Rush, Desert Dash, Ice Citadel or Lava Fort. Background, terrain, particles and enemy colour treatment change by stage.

### 9. More characterful visuals
The battle now uses a canvas renderer for soldiers, enemies, Bosses, projectiles, focus rings, shields, supplies, explosions, floating score text and screen shake instead of static emoji rows.

### 10. Reward / loot feel
End-of-run sequence includes a bouncing/opening gift, coin rain, XP animation and a random bonus collectible reward. Existing coins, XP, collection and progress systems remain.

## Learning design retained
- 1×1 through 10×10.
- Adaptive weak-fact weighting.
- Multiple mini-game question types: lanes, monsters, bridges, balloons, keypad and inverse questions.
- English / Traditional Chinese.
- Questions deliberately remain intermittent, not constant.
- Wrong answers are re-weighted to reappear later.

## Social design retained
- No student account required.
- Nickname-based play.
- Shareable challenge code / QR flow.
- Same seeded run for challenges.
- Local classboard import.

## Mobile UX
- Designed around landscape mobile browser play.
- Portrait rotation reminder.
- Large touch targets.
- Tap-first controls; no tiny joystick.
- Skill buttons remain at least 55px high in tested landscape layout.

## QA before publishing
Automated Chromium/Playwright run covers:
- game start and continuous enemy spawning;
- visible projectile activity;
- correct-answer soldier and energy gain;
- wrong-answer enemy rush and red feedback;
- supply collection;
- all three skills;
- Boss spawn, minions, shield break and later phase shield restoration;
- end-of-run loot screen;
- challenge-code encode/decode;
- English/Traditional Chinese switching;
- collection, progress and classboard navigation;
- mobile touch target sizes;
- JavaScript syntax validation;
- zero captured browser runtime errors in the QA run.
# Times Table Battle Arena — V3 Implementation Instructions

## Product goal
Turn the existing functional maths battle into a mobile-first arcade defence game that stays fun between questions. Multiplication (1×1 to 10×10) powers the battle rather than replacing the battle.

## Art direction
Original **Neon Idol Hunters** aesthetic: colourful K-pop stage energy + fantasy demon hunting. Do not copy any existing movie/series characters, logos, costumes, or compositions. Use original chibi idol-hunter heroes, expressive cute demons, neon magic, layered concert/fantasy environments, bold outlines, readable silhouettes and high contrast for mobile landscape.

## V3 non-negotiable gameplay rules
1. Split troops into **Frontline** and **Reserve**.
2. Frontline cap: 36. Start: 18 frontline + 20 reserve.
3. Correct answer gives **exactly the numerical answer in soldiers**. Example 7×8=56 => +56 total soldiers.
4. Wrong answer deducts **exactly the number the student selected/typed**, reserve first, then frontline. Example selected 48 => -48 total soldiers, capped at current total (never negative).
5. Reserve auto-deploys into empty frontline slots every ~0.28s, 1–3 units at a time.
6. Questions appear roughly every 20–30s; first one earlier (~12s). Battlefield slows but never fully stops.
7. Overall battle must be easier than V2: slower early spawns, lower enemy HP, stronger troop DPS, boss in final ~60s.
8. Wrong answer still triggers a short demon rush, but no additional arbitrary soldier penalty beyond the selected answer.
9. Correct answers also grant energy/combo/score, but those are secondary to exact soldier reward.
10. Boss shield can be broken faster by correct answers.

## Battle loop
- Continuous enemy movement and attacks.
- Frontline units visibly run/deploy, attack and can be knocked out.
- Enemies that reach the defence line fight frontline soldiers; only hit the base when no frontline remains or during boss attacks.
- Player can tap an enemy to focus fire.
- Supply crates periodically appear and can be tapped for energy + reserve.
- Skills: Power Shot (25 energy), Shield (35), Stage Burst/Bomb (60).
- Boss has warning, shield and three phases; minions keep spawning during boss.

## Visual / animation requirements
### Friendly units
Four visually distinct original chibi classes:
- Neon Blade Hunter
- Beat Blaster
- Shield Dancer
- Star Cannon

Each needs readable hair/face/outfit/weapon silhouette, idle/run/attack/hit/spawn motion and shadow. Avoid placeholder circles/rectangles as the final visible character.

### Enemies
- Imp: small, fast, mischievous face/horns
- Bat Demon: winged, mid-speed
- Neon Brute: armoured large enemy
- Shadow Wolf: fast elite
- Boss: original Demon Stage Monarch / Diva-like fantasy boss, large silhouette, crown/horns, cloak/wings, phase glow

### Background themes
Use layered parallax-style scenery and ambient particles:
1. Neon City Arena — skyline, holographic billboards, spotlights, stage floor
2. Moon Shrine — giant moon, torii/shrine silhouettes, lanterns, petals
3. Ice Star Stage — crystal mountains, aurora, snow, reflective stage
4. Lava Demon Dome — volcano skyline, lava fissures, embers, dark arena

## HUD
Show simultaneously:
- Base HP
- Frontline count
- Reserve count
- Energy
- Combo
- Score
- Timer

Correct feedback example: `+56 REINFORCEMENTS!`
Wrong feedback example: `-48 SOLDIERS!`

## Learning logic
- 1×1 through 10×10.
- Adaptive weighting toward weak facts.
- Multiple presentation modes: 2-choice, inverse, keypad, visual themed variants.
- Wrong fact is marked weak and reappears more often.
- Correct fact reduces weakness weight.
- EN / Traditional Chinese UI.

## Social / persistence
Keep nickname-only local profile, challenge code/QR, same-seed challenge, local classboard, coins/XP/streak, collection and weak-fact progress. No unrestricted chat.

## Mobile requirements
- Landscape-first responsive design.
- Portrait rotation reminder.
- Touch targets >= 44 CSS px.
- 60fps target on modern mobile browsers; cap rendered frontline units at 36 and recycle/simple arrays for particles/projectiles.

## QA gate before publishing
Must pass all:
- JS syntax check.
- Runtime with zero uncaught errors.
- Correct answer changes total troops by exactly answer value.
- Wrong answer changes total troops by exactly selected wrong value (unless fewer troops remain, then total becomes zero).
- Frontline never exceeds 36; reserve deployment preserves total troops.
- Enemy/troop/projectile animation visible within first 10 seconds.
- All 3 skills work and consume correct energy.
- Supply interaction works.
- Boss warning, shield, phases and concurrent minions work.
- EN/繁中 switch works.
- Result/loot, challenge code round-trip, classboard import, collection/progress work.
- Mobile landscape smoke test and screenshots manually inspected.
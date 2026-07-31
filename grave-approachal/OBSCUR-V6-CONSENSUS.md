# Obscur — The Sixfold Road

## Game Design Specification — v0.6.0

**Supersedes:** v5 spec proposals. V4 world and fiction are kept.
**Purpose:** Shippable, monetizable, fun-for-8+ game design that 3 people can build.

---

## 1. What This Game Is (One Sentence Per Audience)

**For an 8-year-old:** You roll the die and see the future, then you get to break it if you're fast enough.

**For an adult:** The bot is playing your mask right now — you're deciding whether you agree.

**For an investor:** An idle-game-meets-board-game where zero-input play is the onboarding funnel and masks are the monetizable identity layer.

---

## 2. The Core Loop

### Turn Sequence — Four Phases

```
ROLL  →  BREATH  →  RESOLVE  →  PASS
```

**ROLL:** The system rolls a d6 and shows it face-up to every player simultaneously. The board lights up showing where the active player will land and what type of event they'll hit. No hidden information phase.

**BREATH:** A shared window (5-8 seconds, server-owned clock). Starting with the active player, in seat order, each player gets exactly one chance to spend 1 Focus on a verb, or pass. The window closes when (a) everyone passes consecutively, or (b) 2 verbs total have been played. If nobody spends, the turn resolves as rolled.

**RESOLVE:** Apply the (possibly modified) roll — move the token, trigger the space event, adjust Echoes and the Fracture track. Fully deterministic. No decisions remain.

**PASS:** Advance the turn marker to the next occupied seat.

### Why This Replaces V4

V4's 8-phase turn (READ → INTENT → WITNESS → CAST → BEND → RESOLVE → REACTION → TRANSMISSION) spread one decision across four separate moments. The Breath collapses all player agency into a single visible window — one binary choice (spend or don't) asked at most twice per turn across the table.

---

## 3. Resources — Exactly Two

### Echoes (the win currency)

You collect them. Spaces grant them, some spaces take them. First to **10 Echoes** wins. An 8-year-old can count to 10 and understand whether they're winning.

Why 10: round number, fast games (~15-20 minutes), visible progress every turn.

### Focus (the decision currency)

Everyone receives **3 Focus** at the start of their own turn. Unspent Focus evaporates at end of turn. Focus pays for exactly one thing: using a verb during the Breath.

Focus is not scarce across the game — it's scarce *this turn*. That scarcity is what makes the Breath a real choice instead of a formality. You always have power. You never have enough for everything.

### What's Cut and Why

| Resource | Verdict | Reason |
|---|---|---|
| Resolve | CUT | Was "Echoes but for defense." Focus already handles all decisions. |
| Keys | CUT | Was a second win condition. One win condition is enough. |
| Golden Threads | CUT | Tracked aid relationships — Chronicle feature, not core game. |
| Relics | CUT | Inventory management for 8-year-olds. No. |
| Vows | CUT | Personal quests require too much state tracking. |

---

## 4. The Board

**24 spaces**, circular, counterclockwise. (Down from v4's 36 — faster loops, same density.)

Three space types, color-coded and icon-marked:

| Type | Color | What Happens | Frequency |
|---|---|---|---|
| **LIGHT** | Gold | Gain Echoes (+1 to +3). Safe. | ~12 spaces (50%) |
| **TEETH** | Red | Lose Echoes, get knocked back, or add Fracture. Dangerous. | ~8 spaces (33%) |
| **THRESHOLD** | Purple | Binary choice — one safe, one risky-but-rewarding. | ~4 spaces (17%) |

Every space is pre-determined on the board (not randomly drawn). Players can see what's ahead. The tension comes from the die + the Breath, not from hidden information.

### The Danger Clock — Fractures

**Fracture track:** 0 to 6. Certain TEETH events and risky THRESHOLD choices add to it. If it hits 6, the House wins and everyone loses together.

On Fracture (hits 6 before anyone wins):
1. The match ends immediately.
2. "The House swallowed the Road." Everyone loses.

This shared threat creates cooperation pressure: players who only chase Echoes risk Fracturing the table. Players who only play safe will never reach 10.

---

## 5. Masks — Four at Launch

Each mask is one verb during the Breath. One Focus to use. No passives, no charges, no invisible background rules.

| Mask | Verb | What It Does | What It Costs | The Emotion |
|---|---|---|---|---|
| **Thorn** | REROUTE | After the roll, swap the landing event for a random adjacent space's event. | You're trading the known for the unknown. | Defiance |
| **Ember** | SURGE | After the roll, move 1 extra space forward. | Adds 1 to the Fracture track. | Recklessness |
| **Veil** | SHED | Cancel a negative effect about to hit you. | If the event had a positive component, you lose that too. | Relief |
| **Moss** | CARRY | Absorb another player's negative effect onto yourself instead. | You take the hit. | Tenderness |

### Masks 5 and 6 — Content Drops (Layer 2)

| Mask | Verb | What It Does | Release |
|---|---|---|---|
| **Moon** | SURVEY | Before the roll resolves, reveal the next 3 spaces' event types. | Content drop 1 (4-8 weeks post-launch) |
| **Ash** | DECLARE | Before the roll, predict the die result. If correct, +2 Echoes. | Content drop 2 (8-12 weeks post-launch) |

Moon and Ash are withheld not because they're less interesting, but because their release drives re-engagement and gives the community something to anticipate.

---

## 6. Bots

**Bots get the same verbs as players. No exceptions.** (Carried from v4.)

Bot decision rule: the bot spends Focus on its mask's verb only when doing so would produce a statistically better outcome by 2+ Echoes. Otherwise it passes. This means:
- Bots are competent but predictable.
- The bot IS the mask's coping strategy made literal — it always takes the path of least resistance.
- "The mask decided for you" is both the idle-game hook and the thematic statement.

### What "The Mask Decided For You" Looks Like

When a human player doesn't act during the Breath:
- The screen dims ~20% at their seat.
- A ghost-hand icon taps the board where the bot moves them.
- A quiet in-world caption appears: *"Ember decided for you."*
- No apology banner. No "AI is playing" disclaimer. The mask noticed you weren't there, and it's telling on you.

---

## 7. Win and Loss

**Win:** First player to bank **10 Echoes**.

When a player hits 10:
1. The current round finishes (every player who hasn't gone this round gets one last turn).
2. If multiple players hit 10 in the same round, the player with the most Echoes wins.
3. Tie: the player who hit 10 first (turn order) wins.

**Loss:** The Fracture track reaches 6.

The match ends immediately. The House wins. Everyone loses together.

**Timeout:** If nobody wins and nobody Fractures by round 12, the House wins.

---

## 8. First 60 Seconds — Onboarding Without a Tutorial

1. **Join screen:** Six mask eyes stare at you. Four are selectable (two are locked/coming soon). You tap the face you like. No stats page, no ability comparison. You pick by vibe.

2. **Bot warm-up turn:** Before your first real turn, the bot plays one turn for you, narrated in one line: *"Thorn rolled a 4. Thorn rerouted the Snare into an Echo."* You just watched your mask's personality in action.

3. **Your first Breath:** The die rolls. The board lights up showing where you'll land. Your Focus tokens pulse. A single word appears: **"REROUTE?"** You tap it or you don't. You've learned the game.

4. **Everything else is discovered through play.** TEETH spaces feel dangerous because the screen flashes red. LIGHT spaces feel rewarding because Echoes animate into your counter. The Fracture track rumbles. No tooltip explains what Fractures are — the rumble does.

---

## 9. Monetization — Ethical, Specific, Shippable

### Principle

Monetization lives in the identity layer (who you ARE on the road), not the power layer (what you CAN DO on the road). Signature Cards are the exception — they add verbs, not stats, and are earnable through play.

### Three Tiers

| Tier | Price | What You Get |
|---|---|---|
| **Free** | $0 | 1 mask, full game, ad between matches (~15s), daily login token |
| **Wanderer Pass** | $3.99/mo | Ad-free, 2 masks unlocked, monthly seasonal pack, double login tokens |
| **Sixfold Pass** | $9.99/mo | All masks (including drops), all seasonal packs, creator revenue share boost |

### What People Actually Buy

**Mask Skins** ($1.99-$4.99): Visual variants of your mask. Glowing, spectral, gold, skull, wings. The thing kids show friends at school. Purely cosmetic. This is the bread and butter.

**Seasonal Packs** ($2.99 or 5 login tokens): 6-8 new event cards that add variety to the board's LIGHT, TEETH, and THRESHOLD events. Same balance, different flavor. Drop monthly.

**Creator Packs** ($2.99): Each of the 3 team members creates themed packs tied to their YouTube channel. Different art, different event flavor text, different vibe. Fans buy to support the creator.

### Signature Cards (Layer 2 monetization, post-launch)

Each mask gets 3-5 unique event cards that only trigger for that mask. Mechanically meaningful but not power-creeping — they add variety, not advantage. Earnable through play (4 weeks of dailies) or purchasable ($1.99 for 3).

### Free Currency — Insight Tokens

- 1 per daily login
- 2 per completing a match
- 5 tokens = 1 seasonal pack

No loot boxes. No blind randomness. No gacha. Transparent pricing. Parents see no predation. Kids understand the economy.

### Creator Revenue Splits

| Role | Revenue Share |
|---|---|
| Pack art contributors | 30% of their pack's revenue |
| Card/event designers | 20% of their content's revenue |
| YouTube channel creators | 40% of their branded pack revenue |

Each of the 3 team members independently monetizes through their own creator pack line and YouTube channel integration (when YouTube is added in Layer 2).

---

## 10. Layer Architecture — What Ships When

### Layer 0 — "The Idle Road" (Launch)

The complete, playable, monetizable game:
- 24-space board, d6, 4 masks, bots
- ROLL → BREATH → RESOLVE → PASS
- 2 resources (Echoes + Focus)
- 3 space types (LIGHT / TEETH / THRESHOLD)
- Fracture track
- Mask skins, Wanderer/Sixfold Pass
- Tablet-first, web-playable

**This must be fun to watch with zero input AND fun to play with six humans.** Both are true because The Breath is visible, dramatic, and optional.

### Layer 1 — "The Masks Return" (4-8 weeks)

- Moon mask drop (SURVEY verb)
- First seasonal pack
- Signature Cards (Layer 2 monetization seed)
- Simplified Chronicle: end-of-game tap-based question per mask

### Layer 2 — "The Open Road" (8-16 weeks)

- Ash mask drop (DECLARE verb)
- Creator pack infrastructure
- YouTube channel integration (as in-game Hubs, watch-for-tokens)
- Community card submission pipeline (moderated, revenue-sharing)
- Second board map

### Layer 3+ — Earned Through Metrics

- Full Chronicle (multiplayer social tracking)
- Verb drafting (tiers 1-3, start with 3 verbs, end with 6)
- Executable code cards (sandboxed, tiered trust)
- 3x3 playstyle network
- Procedural board generation
- Anything from v5 spec not already included

---

## 11. The ONE Thing

> You watch the game play itself, and then you see the moment where you could have changed everything, and next time you reach in and do it.

That is The Breath. That is the game. Everything else serves it or gets cut.

---

## 12. What the Kid Said (Don't Forget This)

> "You roll the die and see the future, then you get to break it if you're fast enough. Your mask has superpowers but also bosses you around. Win by collecting Echoes before everyone else, or just watch the bots fight if you're lazy."

If the game can't be explained in those three sentences, it's too complicated.

---

## 13. Open Questions (Need Playtesting)

- Exact Echo rewards per space type (LIGHT: +1/+2/+3 distribution)
- Exact Fracture costs per TEETH event and Ember's SURGE
- THRESHOLD choice calibration (safe vs. risky reward curves)
- Breath window duration (5s? 8s? 10s?)
- Board layout: which spaces are LIGHT/TEETH/THRESHOLD and in what order
- Bot difficulty tuning (threshold for "statistically better by 2+")
- 24 vs 30 space board (needs feel testing)
- Whether REROUTE should be "adjacent" or "random" swap
- Whether VEIL's "lose positive too" is too punishing for kids
- Whether 10 Echoes is the right win target for 15-20 min games

---

## Appendix: The Table Talk Test

The design's north star:

> If players aren't saying things like these during The Breath, the game has failed:
>
> - "Wait wait WAIT — don't let it hit the fire tile, spend your Focus!"
> - "I'm saving mine, I don't care, Ember never cares."
> - "She's gonna Veil it. She's ALWAYS gonna Veil it."

And if one player doesn't tell this story to someone after the game, the game has failed:

> Round 4, Moss spends their last Focus to take Ember's hit instead — not because the game told them to, because they chose it while everyone watched the die glow red. Ember survives. Later the game asks Moss: "You took Ember's fall. Was it yours to take?" Moss taps "Yes." That's the text someone sends their group chat.

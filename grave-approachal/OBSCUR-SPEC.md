# Obscur — The Sixfold Road

## Gameplay Design Specification — v0.5.5

**Date:** 2026-07-29
**Team:** graves, Foxy, dreamer
**Supersedes:** rules-v4 mechanics. The v4 *world* is kept.
**Blocked:** no code against the v4 tree until the licence is granted — `OBSCUR-LICENSING.md`

---

## How to read this

Every design claim carries its source. This exists so nobody has to trust the whole document at once.

| Tag | Means |
|---|---|
| **[F]** | Foxy said it. Quoted in §1. |
| **[G]** | graves decided it. Listed in §1. |
| **[V4]** | Inherited from dreamer's rules-v4. |
| **[M]** | Mine. **Unverified.** Argue with it or cut it. |

**If you are short on time, read only the [G] lines.** Everything else is a record of what you already decided. §11 lists every [M] claim in one place.

---

## 1. Source

### Foxy — discord, 2026-07-27

| # | Verbatim |
|---|---|
| F1 | "the game must be able to play itself without player interaction. meaning if the player doesn't choose an action, the game must be able to randomly force the player to advance." |
| F2 | "just a die / and a start condition / and a end condition / again, JUMANJI" — the board is metaphorical |
| F3 | "lore invariants PACKS / if you enable it, it will enable events of that laore" |
| F4 | "chaos and complex mechanics = stimulation" |
| F5 | "target audience: 8-12 year old" / "correct" |
| F6 | "so optimize for tablet resolution" / "not a joke" |
| F7 | "yes, lets make things modular whenever we can" / "we have a preset suggested" |
| F8 | "being a player must be exciting / there must be a reason why a player wants to join the board game and beat the bots" |
| F9 | "all events are just some variation of move forward x spaces or move back x spaces / maybe some give you items / maybe the items affect other players" |
| F10 | "maybe you can buy / to have your own special skins / we can build a vertical off a solid good board game" |
| F11 | "if its modular, everyone can have a try at making it not suck" |
| F12 | "lets branch from a simple roll the die, move forward" |
| F13 | "allow artists to donate art / and link to their own art pages / and create their own event that way" |
| F14 | "also include whale hooks / and abuse skinner if you have ot" |
| F15 | "we will have three developers expanding on this / i think all with their own claude instance" |
| F16 | "any person can insert game rules" |
| F17 | "we have three youtube channels on hold / so we need this board game to succeed so we can monetize them" |

### graves — decided in session

| # | Decision |
|---|---|
| G1 | Keep the fiction, rework mechanics. |
| G2 | A 3×3 playstyle network, extending Bartle's 2×2. |
| G3 | Bots get the same verbs as players. |
| G4 | Masks start with **3 verbs** — 2 universal, invariable, plus 1 mask verb — and end with **6**. Tiers are 0,1,2,3. Tier 0 is the start; tiers 1–3 are drafts granting one verb each. |
| G5 | Each mask has **2 cards per tier, at minimum**. The third card in an offer is drawn from the deck list. Choose 1 of the 3. Soft cap, not hard caps. |
| G6 | **Universal card** gives a *boost* and a universal verb. **Mask card** gives a *trade* and a mask verb — meaning it is not the normal tier's verb, not that you gain nothing. |
| G7 | Cards accumulate. A theme pack adds equally to all masks. |
| G8 | **Masks are handicaps**, keeping with neurodivergence. |
| G9 | Masking 100% is not a good line. |
| G10 | Packs are sometimes code. Cards are sometimes code. |
| G11 | Monetization must not be cosmetic-only. It must include **"better chance of a thing"** and some gacha and loot-box technique. |
| G12 | Contributors retain personal ownership unless signatory to a collaborative release agreement. |
| G13 | **The verein strategy:** each contributor needs a way to **personally monetize their own contribution**, independent of the other two. |
| G14 | "playing worse than the bots is why you learn to play a game" |

### Team

**Three people: graves, Foxy, dreamer.** Not three additional hires. [G] 

---

## 2. What this game is

This game is about masking. [M]

Not metaphorically — literally. A masked figure is moving down a road that doesn't care whether they're there or not. The road advances by die. The player's only power is interruption: the moment the world tries to move them and they decide whether to fight it, redirect it, or let it go.

The six masks are coping strategies. [M] Not bundles of power — shapes you learned to wear to get down a road that wasn't built for you. Every mask verb is something that costs you. Every mask card is a trade. The handicap is not the mask; the handicap is the exchange rate, and you chose it.

**F1 and F8 used to pull against each other:**

> F1: the game plays itself with zero input.
> F8: there must be a reason to sit down and beat the bots.

**[M] The resolution:** the player's verb is not *move* — the die moves you. The player's invariant proto-verb is *interrupt*. The road proposes. You may argue with it. If you don't, the proposal stands and the bot plays its recommendation.

That is the reason to sit down. The bot is playing your mask right now, with your verbs, making your mask's choices. Whether you agree with it is the whole game.

---

## 3. Layer 0 — the atom

```
a die
a start condition
an end condition
a position per traveler
event cards
mask cards
other players [F9]
```

Turn: roll or hold, advance exactly as rolled, resolve tile event, resolve board (if any modules) event, check end. Repeat. The road is a state, not a rendered board [F2]. All seats bot-fillable [F1].

**[M] Layer 0 is a complete, self-playing game.** It is boring; that is correct. Every layer above must justify itself against it and must be removable back down to it.

---

## 4. Layer 1 — the Breath

**[M] The whole section is mine unless tagged otherwise.** Foxy specified F1 and F8. This is a proposed mechanism for both.

Each turn:

```
ROLL  →  ⟨ THE BREATH ⟩  →  RESOLVE
```

The die rolls **in private, first** — every traveler sees what is about to happen, and then the **Breath** opens: a window in which seated travelers may spend **Focus** to change the outcome. When it closes, the turn resolves. If nobody spent, it resolves as rolled.

**Focus is the spendable resource. The Breath is the window.** [V4 — *Focus* is v4's name for the ±1 Bend resource.]

**Focus is not scarce. Turns are.** [M] Focus resets each turn. You always have a breath. The scarcity is the run itself — a finite number of windows before the House falls. Two demands compete for the same pool each turn: let the mask verb pull (spend Focus on the mask's thing) or interrupt the Road (spend Focus on what the die is doing). You can't stockpile. You can always choose.

What the Breath buys:

- **F1 without a fallback.** Not spending is a real line of play. Nothing waits on a child who put the tablet down.
- **F8.** Spectators watch the die decide; seated travelers can argue with it. Visible in ten seconds without reading a rule.
- **F2, literally.** The game happens *to* you. Your power is when you push back.

**The final result must stay visible.** [V4 — v4 shipped this distinction.] Without it the Breath has no theatre.

---

## 5. Verbs

**Counts are [G4]. Card types are [G5], [G6]. Everything else is [M].**

### Counts

| Point | Verbs held |
|---|---|
| Tier 0 — start | **3** — 2 universal (invariable) + 1 mask verb |
| Tier 1 | 4 |
| Tier 2 | 5 |
| Tier 3 — end | **6** |

Each draft grants exactly one verb. Which verb depends on the card taken.

### Universal starting verbs (invariable — every player, every mask)

**WITNESS** — observe the full board state and declare one true thing about it. No Focus cost. Once per turn, you may instead spend this on another player: place a Chronicle token face-down in their Chronicle space. You can always see. What you do with the seeing is a choice. [M]

VERB2 - NOT GIFT VERB

*"You can always see. You can always connect."* These are the two free verbs — the floor of personhood that no mask takes away. [M]

### The two card kinds [G6]

| | Effect | Verb granted |
|---|---|---|
| **Universal card** | a minor **boost** | the tier's universal verb(s) |
| **Mask card** | a distinct **trade** | the mask's substitute for that tier, *double edged sword* — *not* the universal tier verb(s) |

The all-mask path doesn't lose because mask verbs are weak — it loses because specialized lines have steep costs. By Tier 3 you're highly specialized and increasingly in the strategic debt G9 refers to, and it carries no shame: some coping strategies genuinely work better in isolation, at a cost.

### Tier universal verbs (acquired through draft)

| Tier | Verb | What it does |
|---|---|---|
| 1 | **BEND** | Spend Focus to shift the die result ±1. The direct interrupt. [M] |
| 2 | **TBD** |  |
| 3 |  |  |

**[M] Arc:** BEND teaches you to interrupt. Individual interference → individual cooperation → collective deliberation.

---

## 6. The Draft

Three drafts per run, at tiers 1, 2 and 3. [G4]

Each offers **three cards — in the MVP this is 2 mask, 1 universal. Choose 1.** [G5]

```
tier 1:   A universal   B mask        C mask         choose 1
tier 2:   A mask        B universal   C mask         choose 1
tier 3:   A mask        B mask        C universal    choose 1
```
_the above is an example_

**[M]** Position of the universal card(s) shuffles, so no slot is learnable as "the road's."

**[M]** The mask shows its recommendation before you choose. If you don't choose, the mask takes its recommendation. This is the F1 guarantee at the draft layer and the pedagogy: watch what your mask would have picked, then decide whether you agree.

**[M] Tier gating by road progress and event cards, not round number.** Reaching certain positions on the road unlocks the next tier. Moving forward earns growth. Waiting doesn't. That makes advancement a real choice with a real pressure.

---

## 7. Cards and packs

### Pools accumulate

```
pool(mask, tier) = 2 core + k × (enabled theme packs)
```

**A theme pack adds the same number of mask cards to every one of the six masks, or it adds none at all.** [G7] 

**[M]** Enforce the equal-counts-per-mask rule in the pack schema. A rule in the file format survives a deadline; a rule in a document does not.

### Cards are sometimes code [G10]

A five-operation data grammar covers the common case, but cannot express F4's "complex mechanics" or F16's "any person can insert game rules," and a data-only format puts every new mechanic behind an engine release. [g: lets fix that]

**[M] Tiered trust:**

| Tier | Source | Runs |
|---|---|---|
| T0 | first-party | code, reviewed |
| T1 | signed author | code, reviewed before listing |
| T2 | community | sandboxed, must clear validator + simulator |
| T3 | unsigned / local | sandboxed, off by default |


---

## 8. Masks

**Masks are handicaps, keeping with neurodivergence.** [G8]

Not bundles of power — coping strategies you wear to get down the road. Each mask verb is the path of least resistance: gravitational, not mandatory. [M] It pulls. You can navigate with it or against it. The cost is an exchange rate, as part of the verb itself. Sometimes least resistance is correct. Sometimes resisting it is the skill. The Chronicle watches both.

**The mask plays you when you stop playing it.** [M] Same verbs, same policy, bot in the seat. The failure state is not losing — it's **illegible defeat**. Because the mask pre-registers its recommendation and you consciously override it, every loss arrives with its counterfactual already visible.

The six, from v4, kept by name and character: **Thorn, Ember, Veil, Moss, Moon, Ash.** [V4, G1] (subject to reassertion)

### Starting verbs [M]

[GRAVES: "hey kid i like the ideas buy game design takes a bit more than this so be salient"]

| Mask | Verb | What it does | What it costs |
|---|---|---|---|
| Thorn | **REROUTE** | When an event resolves, declare a face-down alternate instead. The alternate is unknown until you commit. | You can see the determined event (WITNESS is free). You are choosing the unknown over the seen. Not better odds — refusal. |
| Ember | **SURGE** | Take up to 2 additional spaces of movement. | +1 Static per extra space. The cost is paid by the table, not by Ember. |
| Veil | **SHED** | Before a tile resolves, declare you are slipping the effect. Harm avoided. Gain forfeited. The table sees what would have been. | Whatever would have been given is visible to everyone. You may have slipped a gift. |
| Moss | **CARRY** | Before another player takes harm, declare you will take it instead. | You take the hit. |
| Moon | **SURVEY** | Before the die rolls, reveal the top event card to the table. | You spent your turn on information, not action. The information is public — bots and other players adapt. |
| Ash | **DECLARE** | Before the Breath opens, publicly name what will happen this turn. If accurate: +1 on the next roll. | The declaration is public. If wrong, the table witnessed it. |
[G: like these arent great]

### The psychological read [M]

~~Each verb is the same assertion: *I can argue with what's coming.* Thorn refuses the determined event. Ember outpaces the road. Veil refuses the determined harm. Moss refuses the harm landing on someone else. Moon refuses to go in blind. Ash refuses to be surprised.~~

The mask is the shape of that refusal. The cost is what refusing requires.

---

## 9. The 3×3 network [G2]

Bartle's grid is 2×2 and has no vocabulary for a game that moves without you. **[M] Both axes get a middle term:**

**Verb:** ACTING — REACTING — INTERACTING
**Object:** WORLD — THE RUN — PLAYERS

|  | **WORLD** | **THE RUN** | **PLAYERS** |
|---|---|---|---|
| **ACTING** | Pilgrim | Gambler | Hunter |
| **REACTING** | Survivor | Opportunist | Guardian |
| **INTERACTING** | Cartographer | Archivist | Companion |

**[M]** Proposed mapping: Thorn→Pilgrim, Ember→Gambler, Veil→Survivor, Moss→Guardian, Moon→Cartographer, Ash→Archivist.
### [Graves: For primary builds yes, but the offhand build should be a permutation]

**[M] Hunter, Opportunist and Companion have no starting mask.** They are reachable only by drafting toward them. Nobody can start as a griefer; antisocial behavior is a chosen reaction born from your own mask, made in front of the table.

**[M] Live constraint from Bartle (1996):** *"Increasing the number of killers will decrease the number of socialisers by a much greater degree."*

---

## 10. The Chronicle [V4, M]

The Chronicle records the run. It is the divergence log, the print artifact, and the win condition. [V4 — the Chronicle exists in v4. What follows is how v5 uses it.]

### Token counts

**Tokens track what you DID.** Wins, Fractures caused, OFFERs accepted, CARRY uses. The count is the legible climax at House-fall — visible across the table, readable in a second. [M]

### Chronicle tokens (the negative space)

**[M] Other players are your Chronicle keepers.** When a player WITNESSes a moment where another traveler's mask verb was available and they didn't take it, they may spend their WITNESS for the turn to place a Chronicle token face-down in that traveler's Chronicle space. Silent. No announcement.

At Housewin, each traveler flips their Chronicle tokens before the question is read. The count is visible. Then the question is read. **The question is the meaning. The count is the proof.**

### The six Chronicle [STRICTLY EXAMPLES NEED CALIBRATING FOR SHIPPED VERSION] questions [M]

| Mask | Question |
|---|---|
| Thorn | "Your Chronicle says you sat with the Road three times. Did you let go, or were you outrun?" |
| Ember | "Your Chronicle says three people held while you moved. Did you know?" |
| Veil | "Your Chronicle says you slipped three effects. Were any of them gifts?" |
| Moss | "Your Chronicle says you could have Carried and didn't. Do you know who you were protecting?" |
| Moon | "Your Chronicle says you went in blind three times. Was that trust or fear?" |
| Ash | "Your Chronicle says you went quiet three times. Did you know you were right?" |

**[M] Tokens track what you did. Chronicle questions ask about what you didn't.** Every question is about the mask's unnatural moments — the times you didn't take the path of least resistance. That is where your actual self shows up against the shape you're wearing.

### The win condition [M]

The House wins at 3 Fractures. The run ends. There is no single winner.

Each traveler reads their Chronicle question. Each mask scores its own tokens. The Chronicle is the artifact — the record of what the run became and how much of it was you arguing with the Road versus the Road taking you. The winner is decided by **who was on the exit tile at game end, tie broken by token count, and tie broken by cooperation record.**

**[M]** This is not a neutral design. The question asked in front of your friends at run-end is the one that the game answered from watching you play — that is the memorable moment. Not a leaderboard. A reckoning.

---

## 11. Bots [G3]

**Bots get the same verbs as players. No exceptions.**

v4 already worked this way — *"Bots use the same command paths"* [V4] — so this is a property to preserve and enforce, not to introduce.

**[M]** Enforce with a signature that cannot reach private state:

**[M]** What follows if enforced:

- No idle state. Every seat is always driven; the only question is by whom.
- **The mask plays you when you stop playing it.** Same verbs, same policy, bot in the seat.
- Difficulty is policy quality, never resources. No bot gets more Focus, a better die, or an extra verb.
- The simulator runs the real game, so the balance gate is full-fidelity.
- Drop-in is free. A seat taken mid-run was already being played competently.

### The first 60 seconds [M]

1. Mask assigned or chosen. The mask's starting verb appears with one line: what it does, what it costs.
2. WITNESS and OFFER appear with one line each: "You can always see. You can always connect."
3. Bots fill empty seats. The bot is playing your mask — same verbs, same policy.
4. Die rolls publicly. The Breath opens. Your mask shows its recommendation.
5. You take the recommendation, override it, or do nothing. If you do nothing, the bot executes the recommendation.
6. Turn ends. The Chronicle is already watching.

**[M] The hook for F8:** the bot is playing your mask right now, with your verbs. You can see whether the bot would have done what you did. That is the reason to sit down — not "beat the bots" as an abstraction, but *watch your mask play without you and decide if you agree.*

### Losing to your own mask [G14]

*"Playing worse than the bots is why you learn to play a game."*

**[M]** The failure to design against is not losing — it's illegible defeat. Because the mask pre-registers its recommendation and you consciously override it, every loss arrives with its counterfactual attached. The Chronicle records divergence: where you went against your mask, and whether it paid.

---

## 12. Every [M] claim, in one place

The audit list. Nothing here came from Foxy or graves.

1. The game is about masking — the mechanics enact what masking costs — §2
2. Masks are coping strategies, not power bundles — §2
3. The player's verb is "interrupt," not "move" — §2
4. The bot-as-mirror framing ("the bot is playing your mask right now") — §2
5. Layer 0 must stay independently playable — §3
6. Focus resets each turn; turns are the scarcity, not Focus — §4
7. Two competing demands on Focus: mask gravity vs. Road interruption — §4
8. WITNESS as universal starting verb (see freely, record once per turn) — §5
9. OFFER as universal starting verb (give something, free) — §5
10. "You can always see. You can always connect." as the floor of personhood — §5
11. Trade = swap one universal verb out of active hand — §5
12. BEND (T1), GIFT (T2), CALL (T3) as tier universal verbs — §5
13. CALL's object: consensus which single player acts during Breath — §5
14. The arc: BEND → GIFT → CALL as individual interrupt → individual cooperation → collective deliberation — §5
15. Universal card position shuffles in the offer — §6
16. Mask recommendation shown before choosing; taken automatically if you don't — §6
17. Tier gating by road progress, not round number — §6
18. Equal-per-mask enforced in the schema — §7
19. Tiered trust model for code cards — §7
20. Deterministic fuel-metered sandbox; QuickJS/WASM — §7
21. Text and art moderation as the larger risk — §7
22. Mask verb is gravitational, not mandatory — §8
23. "The mask plays you when you stop playing it" — §8
24. Illegible defeat as the real failure mode — §8
25. The six mask verbs (REROUTE, SURGE, SHED, CARRY, SURVEY, DECLARE) — §8
26. REROUTE = event-choice, not path-choice — §8
27. Ember's cost falls on the table, not on Ember — intentional — §8
28. Masks symmetric in cost, not capability — §8
29. The psychological read: each verb is a shape of refusal — §8
30. The 3×3 middle terms and all nine cell names — §9
31. The mask-to-cell mapping — §9
32. Hunter, Opportunist, Companion as drift-only — §9
33. Drift cells change verb gravity, not verb access — §9
34. Companion drift: OFFER operates at Focus-transfer depth — §9
35. Bartle population constraint as a live design input — §9
36. Chronicle keeper mechanism: other players WITNESS your near-misses — §10
37. Ember's Chronicle tokens placed by players who held still — §10
38. Token count as legible climax; Chronicle question as meaning — §10
39. Six Chronicle questions (verbatim) — §10
40. No single winner; mask-relative Chronicle scoring — §10
41. The Chronicle as reckoning, not leaderboard — §10
42. Every consequence listed under bots-same-verbs — §11
43. The `PublicSnapshot` policy signature — §11
44. First 60 seconds beat sequence — §11

---

## 13. Not designed

Items where the brainstorm reached a proposal are marked [M-proposed]. Items with nothing behind them are blank.

- **Bot recommendation body.** The mask's recommendation must be printable — a conditional on a card ("if the event would move you back, REROUTE"). Language unwritten. [M-proposed: one conditional per mask verb, plain enough to read once and internalize]
- **Mask assignment vs. choice.** Which is the default first-play experience, which is the variant? [M-proposed: choice is more authentic to the masking theme; assignment is simpler as a tutorial mode — decide which is default] [GRAVE CHOICE: at game start, players roll the first d6, and go in ascending order. the only time a 1 is truly better than a 6]
- **Road branch structure.** Linear is assumed. Branch positions unconfirmed. [M-proposed: strictly linear; REROUTE operates on event-choice, not path-choice] [G: Deferred to modules; basegame linear, only 2 maps. If a player wins with all 6 masks, give them a free "backrooms" procedural map pack with 1 additional universal card per tier]
- **Trade cost specifics.** What the card also charges is for later; the card library is not scoped. []
- **Focus amount and recovery.** One unit per turn? Two? Does it recover mid-turn or only at turn-start? []
- **The 36+ mask cards and their specific trades.** []
- **Seat count.** Six is unconfirmed. [V4] [6 confirmed for scope]
- **Draft tier gating specifics.** Road positions that gate tiers not yet specified. [M-proposed: road progress, not round number]

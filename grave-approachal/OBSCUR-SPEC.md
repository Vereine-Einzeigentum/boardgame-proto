# Obscur — The Sixfold Road

## Gameplay Design Specification, v5 (clean-sheet mechanics)

**Status:** draft for review — Foxy, dreamer, graves, +3 incoming devs
**Date:** 2026-07-28
**Supersedes:** rules-v4 mechanics, entirely
**Preserves:** Foxyverse fiction, art direction, the name, the atlas, the site shell

---

## 0. What this document is

Rules-v4 is scrapped as a mechanic. It is not scrapped as a *world*.

Foxy's branch point, verbatim: **"lets branch from a simple roll the die, move forward."**
This spec starts there and adds one layer at a time. Every layer is removable. If you delete
everything above Layer 0, you still have a playable game.

The Foxyverse vocabulary — masks, the Static, Echoes, the Bend, the Sixfold Road, the Final
Orbit — survives as `pack:foxyverse-core`, the default lore pack. That is not sentimentality;
it is the **proof of the modular system**. If the same engine can wear Foxyverse on Monday and
Backrooms on Tuesday, the pack architecture is real. If it can't, it was never modular.

---

## 1. Provenance

Every hard requirement below is traceable to something a person actually said in #business-talk.
Nothing here is invented. If a line is my inference, it is marked **[inferred]** and you should
argue with it.

| # | Requirement | Source |
|---|---|---|
| R1 | "the game must be able to play itself without player interaction. meaning if the player doesn't choose an action, the game must be able to randomly force the player to advance." | Foxy, 10:22 PM |
| R2 | "just a die / and a start condition / and a end condition / again, JUMANJI" — board is metaphorical, no physical board or pieces required | Foxy, 10:22 PM |
| R3 | "lore invariants PACKS / if you enable it, it will enable events of that laore" | Foxy, 10:22 PM |
| R4 | "chaos and complex mechanics = stimulation" | Foxy, 10:20 PM |
| R5 | Target audience: 8–12 year old. "correct" | Foxy, 10:25 PM |
| R6 | "so optimize for tablet resolution" / "not a joke" | Foxy, 10:25 PM |
| R7 | "yes, lets make things modular whenever we can" + "we have a preset suggested" | Foxy, 10:24 PM |
| R8 | "being a player must be exciting / there must be a reason why a player wants to join the board game and beat the bots" | Foxy, 10:26 PM |
| R9 | "all events are just some variation of move forward x spaces or move back x spaces / maybe some give you items / maybe the items affect other players" | Foxy, 10:26 PM |
| R10 | "maybe you can buy / to have your own special skins / we can build a vertical off a solid good board game" | Foxy, 10:26 PM |
| R11 | "if its modular, everyone can have a try at making it not suck" | Foxy, 10:26 PM |
| R12 | "lets branch from a simple roll the die, move forward" | Foxy, 10:34 PM |
| R13 | "allow artists to donate art / and link to their own art pages / and create their own event that way" | Foxy, 10:32 PM |
| R14 | "also include whale hooks / and abuse skinner if you have ot" | Foxy, 10:32 PM — see `OBSCUR-RISKS.md` |
| R15 | Three developers, "all with their own claude instance" | Foxy, 10:31 PM |
| R16 | "turnbased, modular, free-for-all, rng movement" + "bots already playing it" | graves 10:25 PM, ratified by Foxy 10:26 PM |
| R17 | **Open concern:** "it having an end does limit engagement longterm" | graves, 10:34 PM |
| R18 | "any person can insert game rules" | Foxy, 9:53 PM |
| R19 | **[inferred]** Six seats, one-to-six travelers | carried from existing product identity — *confirm* |

---

## 2. The problem nobody has solved yet

R1 and R8 are in direct opposition, and everything else is downstream of that collision.

> **R1:** the game must play itself with zero input.
> **R8:** being a player must be exciting; there must be a reason to sit down and beat the bots.

A game that plays itself perfectly is a screensaver. Screensavers do not have players. The
naive fix — "add player actions" — breaks R1 the moment an action is required. The naive fix in
the other direction — "let idle players auto-pass" — makes sitting down pointless, because
passing and playing produce the same game.

**The resolution is to change what the player's verb is.**

In most board games the player's verb is *move*. In Obscur, the die moves you whether you are
there or not. The player's verb is **interrupt**.

---

## 3. Layer 0 — The Atom

```
a die
a start condition
an end condition
a position per traveler
```

Turn: roll, advance, check end. Repeat. No board is rendered as a board — the road is a
*state*, drawn however Presentation likes (R2). Six seats, all bot-fillable.

**Layer 0 is a complete, shippable, self-playing game.** It is boring. That is correct. Every
layer above must be justified against it, and must be deletable back down to it.

---

## 4. Layer 1 — The Breath

The single mechanic that makes this a game instead of a screensaver.

Each turn resolves through one canonical sequence:

```
ROLL  →  ⟨ THE BREATH ⟩  →  RESOLVE
```

The die rolls **in public, first.** Every traveler sees exactly what is about to happen to them.
Then there is a short fixed window — **the Breath**, 4 seconds — in which any *seated* traveler
may spend one Breath token to change it. When the window closes, the turn resolves. If nobody
spent, it resolves exactly as rolled.

That is the whole game.

**What this buys:**

- **R1 satisfied at the mechanical level, not as a fallback.** Zero input is not a timeout
  penalty or a "safe default" — it is a legitimate, sometimes optimal line of play. Nothing is
  ever waiting on a kid who put the tablet down.
- **R8 satisfied.** Spectators watch the die decide. Seated travelers can argue with it.
  That is the entire pitch for sitting down, and it is visible in the first ten seconds of
  watching, without reading a rule.
- **JUMANJI (R2), literally.** The game happens *to* you. Your only power is when you push back.
- **8–12 appropriate (R5).** One binary decision, on a timer, with the outcome already visible.
  No hidden information to reason about, no analysis paralysis, no rulebook before your first turn.
- **Skill curve without complexity.** Breath is scarce. The whole skill of Obscur is *when to
  spend it* — a five-year-old can play, and there is a genuinely good line an adult can miss.

### Verbs are acquired, not issued

**You start with exactly one verb: your mask's.** There is no universal starter set. Every other
verb is earned through the Draft (§4b) — each card grants **one mask-specific verb and one
universal verb**, and the universal is fixed by tier so the whole table gains the same shared
vocabulary at the same moment.

| Tier | Gains | Owned |
|---|---|---|
| 0 | your mask's unique verb | 1 |
| 1 | +1 mask verb, +**BEND** | 3 |
| 2 | +1 mask verb, +**SHIELD** | 5 |
| 3 | +1 mask verb, +**GIFT** | 7 |

Endgame: **7 verbs** — four mask-specific, three universal. Room for ~3 extras puts the ceiling
at 10.

**Why the universals arrive in that order.** Bend fate, then protect yourself, then give. It's a
progression an eight-year-old feels without being told, and it's mechanical rather than preachy.

**SHOVE is deliberately not universal.** Redirecting harm onto another traveler is a *mask*
verb, not a birthright — so griefing requires committing to it, visibly, at the table, rather
than everyone carrying a grief button from turn one. This is the §6 Bartle counterweight moved
out of the tuning file and into the structure: Hunters have to choose to be Hunters.

**Economy:** N Breath at start (tune: 3). Regained from events, from being passed, from the
Static. Never purchasable — see `OBSCUR-RISKS.md` §4.

### The window scales with depth

The Breath was specified at a flat 4 seconds. That was imported from games where a long window
means a stalled table — **and Law 2 (§6) deleted that problem.** There is no idle state; an
expired window isn't a stall, because the mask acts. So window length costs nothing but pacing,
and it should be spent where the decision deserves it.

| Tier | Owned | Typically live | Window |
|---|---|---|---|
| 0 | 1 | ~1 | 4s |
| 1 | 3 | ~2 | 5s |
| 2 | 5 | ~3 | 6s |
| 3 | 7 (10 w/ extras) | ~4 (~6) | 8s |

At ~60 casts per run that is 4–8 minutes of live Breath time inside a 15–20 minute run, which is
the right shape: the game gets more deliberate as it deepens.

**And it is thematically free.** The mechanic is called the Breath. A traveler who has walked
further holds it longer.

**Load check.** Ten owned verbs with ~6 live, turn-based, is *below* what this exact demographic
already carries elsewhere — a Magic opening hand is 7 cards with multiple modes each, a Pokémon
TCG board is 12–24 live options, a Smash character is ~25 moves in real time with no window at
all. Designing down to 4 verbs was condescension, not accessibility.

**The natural/final distinction stays visible.** Players must always see *what the die said*
versus *what happened*, or the Breath has no theatre.

---

## 4b. Layer 1b — The Draft

The Breath is the override at the scale of a turn. The Draft is the same verb at the scale of an
arc, and it is what makes the whole game one idea instead of two:

> **The game proposes. You may override.**

Three times per run — at tiers 1, 2 and 3 — the seat is offered **three cards**, face up, with
**one marked as the mask's recommendation.**

The three are not drawn alike:

| Slot | Source | Character |
|---|---|---|
| 1 | your mask's tier-N pair | fixed, learnable, **who you are** |
| 2 | your mask's tier-N pair | fixed, learnable, **who you are** |
| 3 | the universal tier-N pool, drawn at random | variable, **what the road offers** |

**Every draft is therefore the same question: stay who you are, or take what the road put in
front of you.** Two of yours and one of fate's — the game's theme, restated at the draft layer,
three times a run. A child does not need this explained; they feel it the first time the third
card is better than both of theirs.

Because the mask's two are fixed, they are **memorisable**: a player learns Thorn's tier-2 pair
and starts planning around it. That is the mastery curve. The third card is where variance and
surprise live.

### Drift routing

**Mask cards reinforce your starting cell. Universal cards carry the drift.**

The three drift-only cells (§6 — Hunter, Opportunist, Companion) are reachable *only* through
universal cards. Which produces the strongest form of the Bartle counterweight available:

> **You can only become a griefer because the road offered it and you took it over your own
> mask's line. Never because of the mask you picked.**

Hostility is always a visible, chosen deviation from your own character, made in front of five
other people, at most three times a run.

- Choose a card: you take it.
- Choose nothing: **the mask takes its own recommendation.**

R1 holds at this layer for the same reason it holds at the Breath: not choosing is a real line of
play, not a penalty. And the recommendation does something no timeout default can — it makes the
mask's reasoning *visible*. A child learns this game by watching what their mask would have
picked and deciding whether they disagree. That is the entire tutorial, and it never stops the
game to teach.

### Cards are the drift

A card carries effects from the algebra (§5) **plus a policy nudge**. Taking cards is how a seat
walks the 3×3 grid (§6): you start where your mask starts and you drift by what you pick.

```yaml
card:
  id: the-long-way-round
  text: "The road doubles back. You have seen this door before."
  effects: [ MOVE(SELF, -3), BREATH(SELF, +2) ]
  drift:   { toward: cartographer, weight: 1 }
```

**Reading the road.** The v4 vocabulary already had this — *"read six possible roads"* — and the
Draft is that act. Which produces something useful for free: per §6, Bartle's dynamics say the
Cartographer/Explorer cell is the only counterweight that suppresses griefing without costing us
players anywhere else. If the Draft *is* road-reading, every player performs a Cartographer act
several times a run, structurally, rather than because we tuned a reward number. That's
suggestive rather than proven — Bartle describes populations, not acts — but the counterweight
sits in the spine of the game instead of in a config file.

### Cards are the pack format

A card is data in the closed algebra plus a drift vector. Nothing else. So:

- pack content ships as cards (§7);
- artist-donated events (R13) are cards;
- "any person can insert game rules" (R18) means *a person can write a card*;
- and the physical product is **literally the same object** — see `OBSCUR-REVENUE.md` §0.

### The draft pool is table-scoped

**Load-bearing.** The universal pool is assembled from the table's enabled packs and is
**identical for every seat.** Owning more cards never means drawing better ones.

Collection governs what you can *bring to a table*, and bringing it benefits all six seats — the
same symmetry rule as packs (§7). Get this wrong and card ownership becomes a private edge, which
is pay-to-win aimed at children arriving through the side door. See `OBSCUR-REVENUE.md` §1
Tier 3.

### Packs: cards accumulate, and a theme pack feeds every mask equally

A pack may ship **universals**, **thematic mask cards**, or both. Everything **accumulates** —
enabled packs all contribute at once, which is what R7 ("modular whenever we can") actually asks
for. One rule governs the mask half:

> **A theme pack adds the same number of mask cards to every one of the six masks.**

```
pool(mask, tier) = 2 core  +  k x (enabled theme packs)
```

Identical pool *size* for all six, always. The offer is still 2 drawn from your mask's pool plus
1 universal, so the 1-in-3 universal rate is untouched.

| enabled theme packs (k=2) | pool per mask/tier | outcomes per tier | total loadouts |
|---|---|---|---|
| 0 | 2 | 12 | 10,368 |
| 3 | 8 | 18 | 34,992 |
| 10 | 22 | 32 | 196,608 |

**Why the combinatorics collapse.** The pool is drawn uniformly, so the expected power of a draw
is a **convex combination** of the core pair and each enabled pack's contribution. Therefore:

> **If every pack independently keeps all six masks inside the band, every union of packs does
> too.** Convexity does the work; no combination testing is required.

Twelve packs is **72 cells** to check (12 × 6 masks), not 4,096 configurations. And this is
strictly better than making mask cards substitutive, because packs get to *stack*.

**The rule is schema-enforceable.** The validator rejects any pack whose `mask_cards` counts
differ across the six masks. The balance property is guaranteed by the file format rather than by
anyone remembering it at 2am — the same principle as Breath-is-never-purchasable.

**Memorisability shifts, and improves.** You no longer learn Thorn's exact pair; you learn
Thorn's *pool*. That is how a TCG player actually thinks — you know what the deck can do, not
what you'll draw — and it scales with the collection instead of breaking on it.

**Residual risk, unchanged:** pairwise synergy between specific cards. Samplable, not
combinatorial.

### What this structure costs and returns

| | Cards to design | Distinct endgame loadouts |
|---|---|---|
| Model C (3 mask options/tier) | 63 verbs | 162 |
| Model D (mask verb fixed) | 27 verbs | 6 |
| **2 mask + 1 universal**, pool 10/tier | **66** | **10,368** |
| **2 mask + 1 universal**, pool 20/tier | 96 | 63,888 |

36 mask cards are fixed (6 × 3 tiers × 2). Everything above that is universal pool, and the pool
is what packs sell. This beats Model C on both axes at once — fewer things to author, 64× the
run variety — which settles the Model C / Model D question raised in `OBSCUR-BALANCE.md` §8.

---

## 5. Layer 2 — The effect algebra

Foxy is right, and this is the most important architectural line in the document:

> "all events are just some variation of move forward x spaces or move back x spaces" — R9

So we close it. Every event in the game, forever, from any pack, from any donating artist,
compiles to this grammar and nothing else:

```
effect  := MOVE(target, ±n)
         | BREATH(target, ±n)
         | GRANT(target, item)
         | ROLLMOD(target, ±n, turns)
         | TAG(target, mark)

target  := SELF | LEFT | RIGHT | ALL | LEADER | LAST | ROLLED
item    := <declared in pack, resolves to a stored effect list>
```

**Packs are data. Packs are never code.**

That one decision is what makes R11, R13 and R18 safe to ship. "Any person can insert game
rules" and "allow artists to donate art and create their own event that way" are lovely
ambitions and a catastrophic attack surface if a pack can execute anything. As a closed algebra,
a hostile pack's worst case is a badly balanced event — which the validator catches and the
simulator scores.

It also means the pack format is authorable by a person who cannot program, which is the actual
requirement behind R11.

---

## 6. The 3×3 playstyle network

Per graves' ask. Bartle's grid is 2×2 — two binary axes, four corners. It was built to describe
MUDs, where somebody is always doing something. It has no vocabulary for a game that moves
without you, which is precisely the game we are building.

So both axes get a middle term.

**Verb axis:** ACTING — **REACTING** — INTERACTING
**Object axis:** WORLD — **THE RUN** — PLAYERS

*Reacting* is the native verb of a self-playing game. *The run* is the shared thing a table
co-owns — the road, the pot, the Static, the Chronicle — which is neither "the world" nor "the
other players." Bartle's four types land in the corners, unchanged. The new middle row and
middle column are where Obscur actually lives.

|  | **WORLD** | **THE RUN** | **PLAYERS** |
|---|---|---|---|
| **ACTING** | **Pilgrim** — race the road, claim ground `CD2` *(Bartle: Achiever)* | **Gambler** — force tempo, push the pot `CD6·CD7` | **Hunter** — SHOVE, target rivals `CD2·CD5` *(Bartle: Killer)* |
| **REACTING** | **Survivor** — SHIELD, weather the Static `CD8, white-hat` | **Opportunist** — read the swing, spend the Breath `CD3·CD7` ← **centre of gravity** | **Guardian** — SHIELD others, rescue `CD1·CD5` |
| **INTERACTING** | **Cartographer** — read the road, learn the pack `CD7` *(Bartle: Explorer)* | **Archivist** — the Chronicle, collect, curate, replay `CD4` | **Companion** — GIFT, Threads `CD5` *(Bartle: Socializer)* |

`CDn` = Octalysis Core Drive. CD1 Epic Meaning · CD2 Accomplishment · CD3 Empowerment ·
CD4 Ownership · CD5 Social Influence · CD6 Scarcity · CD7 Unpredictability · CD8 Loss/Avoidance.

### Six masks, nine cells — masks are starting archetypes

Masks do not own cells. **A mask is where a seat starts on the grid; cards are how it moves.**
Six starting archetypes traverse nine cells via the Draft (§4b), so coverage is a property of
play rather than of the roster, and the Sixfold fiction survives intact.

### A mask is a handicap, not a power package

The inversion the whole design rests on. Character-select games hand you a bundle of advantages;
Obscur hands you a **constraint you wear to get down the road.**

Every starting verb is a coping strategy with a price:

| Mask | What it lets you do | What it costs |
|---|---|---|
| **Thorn** | force your own route | the route you force is the riskier one |
| **Ember** | move +2 instead of Bending | +2 Static — *v4 already shipped this exact pattern* |
| **Veil** | slip the harm | slipping forfeits the gain attached to it |
| **Moss** | take the hit for someone | you take the hit |
| **Moon** | read what's ahead | reading spends the turn you could have acted on |
| **Ash** | the run remembers | you are bound to what already happened |

Ember is the proof it works: v4 gave it +2 movement *and* +2 to the shared danger clock, and it
still finished top of the win-share table. **Generalise that pattern to all six.**

This retires the earlier claim that masks are symmetric in capability. They are symmetric in
**cost** — six differently-shaped constraints, equally priced. Table symmetry and clean mask
collection (`OBSCUR-REVENUE.md` §1) rest on that instead, since every mask stays free to draft at
every table.

### Which reframes the Draft entirely

If the mask is a handicap, the two mask cards are *more mask* and the universal is *less*. Every
draft asks one question, three times a run:

> **Keep masking, or let something through.**

Masking is reliable: competent, consistent, recommended, capped. The road is variance — it might
be better, it might be worse, and it is the only way off your starting cell.

Which is why the three drift-only cells are reachable **only** through universals, and why it
matters that they are **Hunter, Opportunist and Companion.** What's under the mask is the anger
and the connection both. That's honest rather than tidy, and no character in this game ever has
to say a word about it — an eight-year-old just notices their mask is safe and a little small.

**The balance target this creates**, cheap to test at ~2,700 matches:

| Line | Share of the 27 paths | Target |
|---|---|---|
| pure-mask — never take a universal | 8 (29.6%) | **below even** — safe, competent, capped |
| pure-road — always take the universal | 1 (3.7%) | **below even** — ungrounded, high variance |
| mixed | 18 (66.7%) | **above even** — knowing when to do which |

Neither extreme wins. Mixed lines already occupy two thirds of the path space, so this sits at
the natural centre of the distribution rather than having to be forced into place.

### Three design laws

**Law 1 — Every cell has at least one mechanic.** If a cell is empty, that playstyle has nobody
to be, and you have silently shipped a narrower game than you think.

**Law 2 — Bots get the same verbs as players. No exceptions.**

Not a fairness gesture — an architecture. There is **no bot system**: there is one command
surface and a set of policies over it. A bot is a function returning a `Command`, exactly as a
human's tap does. Consequences, all of them load-bearing:

- **No idle state exists.** Every seat is always driven; the only question is by whom. A human
  walking away is a driver handoff, not a timeout falling through to a safe default. R1 stops
  being a fallback and becomes the normal case.
- **The mask plays you when you stop playing it.** Extremely Jumanji, and it is the same
  mechanism as bot-filling an empty seat — "Echo Traveler" was already the word for this in v4.
- **Difficulty is policy quality, never resources.** A bot never gets more Breath, a better die,
  or an extra verb. Children detect resource-cheating instantly and resent it permanently.
- **The simulator runs the real game.** Because policies drive the true command surface, the
  10,000-match balance gate is full-fidelity rather than an approximation of one.
- **Drop-in is free.** A spectator can take a seat mid-run, because the seat was already being
  played competently.

**The invariant that makes parity real rather than promised** — a policy may only see the public
snapshot:

```ts
type Policy = (s: PublicSnapshot, seat: SeatId) => Command
```

If a policy structurally cannot reach private state, bot cheating is *unrepresentable* rather
than *prohibited*. Same class of guarantee as Breath-is-never-purchasable, and it belongs in the
type system, where it survives a deadline.

**Law 3 — The mask plays the average line; a human wins by playing the read.**

The tuning target for every policy. Competent, clean, and *predictable* — never a surprising
spend. A human beats their own mask by doing the thing a policy won't: spending Breath at a
moment that only makes sense if you have read the table.

**Losing to your own mask is the point, not the failure.** An earlier draft of this law tried to
protect players from ever playing worse than their idle policy. That was wrong, and graves — who
was a TCG and video-game kid, which is the demographic — called it: *"playing worse than the bots
is why you learn to play a game."* The gap between your line and the better line **is** the
teacher. Remove it and nobody improves at anything.

**The real failure is illegible defeat.** Players don't quit games they lose; they quit games
they can't post-mortem. And this design makes defeat legible by construction, because the mask
**pre-registered its recommendation and you consciously overrode it.** That is strictly better
than after-the-fact analysis: you learn what the better line was, that your instinct diverged,
at exactly which moment, and what it cost. Every loss arrives with its counterfactual attached.

**Therefore the Chronicle records divergence.** Not just what happened — where you went against
your mask and whether it paid. *"You went against the Fox four times this run. Twice it paid."*
That is a coaching artifact an eight-year-old can read, it gives the Archivist cell (§6) real
mechanical weight, and it is a far better thing to print on a physical Chronicle poster than a
scoreline.

### The bot roster is the demo reel

A spectator watching an all-bot table sees six masks being visibly, distinctly themselves, and
picks one before they ever sit down. "Bots already playing it" stops being a technical fallback
and becomes the marketing (R8). Because of Law 2, what the watcher sees is exactly what they can
do — the demo never lies.

### Bartle's dynamics are a live constraint, not decoration

From the 1996 paper — these are stated as population effects, and they bite us specifically:

- *"Increasing the number of killers will decrease the number of socialisers by a much greater
  degree."* Our Hunter cell, unchecked, will empty the table of Companions. With an 8–12
  audience that is not a balance problem, it is a product-death problem.
- *"Massively increasing explorers is the **only** way to reduce the number of killers without
  also reducing the player numbers in other groups."*

**Therefore, two non-negotiable tunings:**

1. **SHOVE costs 2 Breath. Every other verb costs 1.** Griefing is available, priced, and never
   free. Bartle: killers are necessary — *"there being no way to 'lose' the game if any fool can
   'win' just by plodding slowly unchallenged"* — so we do not remove the Hunter. We tax it.
2. **The Cartographer cell is over-rewarded on purpose.** Discovering pack content, reading the
   road, and surfacing lore pays generously. This is the load-bearing counterweight, and it is
   the one Bartle says is the only one that works.

### The CD1 hole

Yu-kai Chou, on Bartle: *"Core Drive 1 (Epic Meaning & Calling) is completely absent from every
Bartle type."* True, and it's the drive that produces long-horizon attachment.

Obscur's answer is **the House.** A persistent antagonist that wins if the table fails
collectively. Guardian and Companion cells feed it. Nobody has to be told a story about why they
matter — they just notice that when the House wins, *everyone* loses, and that the person who
GIFTed a Breath at the right moment is why it didn't.

This also does real work on R17.

---

## 7. Layer 3 — Packs

```yaml
pack:
  id: backrooms-core
  title: "The Backrooms"
  license: CC-BY-4.0
  authors: [{ name: "...", url: "https://..." }]   # R13: artists get the link
  requires: { engine: ">=5.0" }
  invariants:                      # R3: "lore invariants"
    - id: no-two-exits
      when: TAG(SELF, threshold)
      then: [ ROLLMOD(SELF, -1, 2) ]
  events:
    - id: hum
      weight: 30
      text: "The lights hum a note you have heard before."
      art: { src: "...", credit: "...", url: "..." }
      effects: [ MOVE(SELF, -2), BREATH(SELF, +1) ]
  masks: [...]
  presets: [...]                   # R7: "we have a preset suggested"
```

- Packs stack. `foxyverse-core` is the default preset (R7).
- Enabling a pack enables that lore's events — exactly R3.
- **Validator gate:** schema-valid, effect-algebra-only, weights sane, art has credit + URL.
- **Simulator gate:** 10,000 seeded matches. A pack that soft-locks, or pushes any mask outside
  the win-share band, does not ship. This is the mechanism behind R11 — "everyone can have a try
  at making it not suck" only works if *not sucking* is machine-checkable.
- Artist-donated art enters as a pack. Credit and outbound link are schema-required fields, not
  a promise. (R13)

---

## 8. Layer 4 — Time structure, and R17

> graves: "and it having an end does limit engagement longterm"

Correct, and the fix is not to remove the end. An endless run kills a tablet game for
8–12-year-olds faster than a short one — there is no clean place to stop, which means every stop
is an interruption, which means a parent ends the session instead of the child.

Three nested clocks instead:

| Clock | Length | Ends? | Carries |
|---|---|---|---|
| **Run** | 15–20 min *(see Q2)* | yes, cleanly | nothing |
| **Road** | seasonal | yes | cosmetics, pack unlocks `CD2` |
| **Chronicle** | permanent | no | every run you played, replayable `CD4` |

The run ends. The Road and the Chronicle don't. And because of R1, **the table never empties** —
an abandoned seat simply plays itself, so drop-in/drop-out mid-run is free. You can leave
mid-game without ruining it for five other children, which is a genuine and rare property.

---

## 9. Layer 5 — Skins and the vertical (R10)

Anja is bringing her own ethical whale hooks; this section is the frame they drop into, not a
replacement for them.

**Shippable to this audience:**
- Cosmetic-only. Never power. Never Breath.
- **Deterministic purchase** — you see the exact item before you pay. No randomized paid boxes.
- Earned track (the Road) reaches the same cosmetic ceiling as the paid track, slower.
- Artist revenue share on donated-art skins — R13's pipeline *is* the storefront, which is the
  most interesting idea in the whole thread and belongs to Foxy.

**Not shippable to this audience — see `OBSCUR-RISKS.md`:** paid randomization, timed purchase
pressure, social-pressure spending, anything under R14 read literally.

---

## 10. Three developers, three Claude instances (R15)

Three parallel agents will collide unless the seams are frozen before anyone writes a line.
**Freeze these three contracts first. Everything else is negotiable.**

| Dev | Owns | Must not touch | Frozen contract |
|---|---|---|---|
| **A — Core** | engine, die, Breath window, effect algebra, bot policies (all 9 cells) | rendering, packs | `Snapshot`, `Command` |
| **B — Packs** | schema, validator, simulator gate, `foxyverse-core`, `backrooms`, artist pipeline, authoring tool | engine internals | `Pack` |
| **C — Table** | tablet UI, spectator/broadcast, transmissions, a11y, skins | rules, ever | consumes `Snapshot` only |

Core is **pure**: seeded, deterministic, no I/O, no clock of its own. Same seed → same match,
every time, on every machine. That is what makes the simulator gate meaningful and what lets
three agents work without merge terror.

**Stack:** stay on TypeScript. The fork is TS/React/Vite/Node and three devs need to move now.
**Against your standing preference, and here is the honest tradeoff:** a Rust→WASM core would
give you a compiled toolchain and hard cross-client determinism, and it is the better engine.
It also costs every dev an onboarding week and makes the pack authoring tool harder. My call is
TS core behind a strict purity boundary, structured so the core can be lifted to Rust later
without touching B or C. Overrule me if determinism drift shows up in the 10k simulation.

**Licensing:** not GPL — this is being sold, per your own caveat. Engine **MIT**. Content packs
**CC-BY-4.0**, which is what makes the artist-donation pipeline honest: attribution and the
outbound link are license terms, not goodwill.

---

## 11. Tablet and audience constraints (R5, R6 — "not a joke")

- Landscape-first, 1024×768 baseline, safe to 2360×1640.
- **One primary touch target**: the Breath button. Thumb-sized, bottom-corner, reachable
  two-handed. No drag, no double-tap, no long-press, no gesture anywhere in the critical path.
- 4-second Breath window is a **tunable** — instrument it before defending it.
- Reading age 8: no rule text over one line. Symbol + text redundancy everywhere (this survives
  from v4 and should).
- Reduced-motion path, retained from v4.
- The Static escalates visually. On a tablet, for a child, there is a line between *tense* and
  *unpleasant*, and we will find it by testing rather than by taste.

---

## 12. Open questions — Foxy

1. **Six seats confirmed?** Carried forward as an assumption (R19), never actually stated.
2. **Run length:** 15–20 min for the 8–12 target, or your earlier 20–30? These pull apart.
3. **Real-money purchases in v1 at all**, given the audience — or cosmetic-earned-only for launch
   and the storefront in v2? This one is load-bearing for the risk register.
4. **Backrooms + 8–12: where's the tone ceiling?** Spooky-fun, or actually frightening? Changes
   art direction, rating, and store category.
5. **"Beat the bots"** — persistent ranking, or per-run bragging?
6. **Artist agreement:** who owns the license and revenue-share terms for donated art? Needs to
   exist before the first artist donates, not after.
7. **YouTube transmissions:** staying? If so, player-initiated rather than automatic — see
   `OBSCUR-RISKS.md` §2, this is the highest-severity item in the whole project.

---

## 13. What I have not designed yet

Named so nobody assumes it's covered:

- ~~Mask asymmetry~~ — **solved.** Masks are starting archetypes differing in policy, not power
  (§6). Still needs simulation to tune, but it no longer needs designing.
- Draft cadence. Three or four card offers per run is a guess; instrument it.
- The recommendation algorithm. What the mask suggests *is* the mask's personality, so this is
  character work as much as it is policy work — and it is the surface a child actually learns
  the game from.
- The House's actual win condition.
- Bot difficulty tiers — must come from policy quality only, never resources (Law 2).
- Onboarding — the first 60 seconds, which for this audience is the whole product.
- Anja's ethical whale hooks (§9 is the socket; the hooks are hers).

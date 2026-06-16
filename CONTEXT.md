# Egg, Inc. Helper Tools — Shared Language

A monorepo of independent web tools for the mobile game **Egg, Inc.**, plus shared packages. The tools read a player's game data and present analysis, planners, trackers, and visualizers.

> This file is the **shared kernel**: the game vocabulary common to every tool. Each tool also has its own `CONTEXT.md` for terms unique to it — see [`CONTEXT-MAP.md`](./CONTEXT-MAP.md). It is a glossary, not a spec — it defines what terms _mean_, never how they're implemented. When naming a concept, use the term defined here and avoid the listed alternatives. Most terms come straight from Egg, Inc. itself; keep them faithful to the game.

## Project Building Blocks

**Tool**:
One of the independent web apps in the suite (e.g. Rockets Tracker, Smart Assistant). Each is its own workspace under `wasmegg/` (plus `eicoop` at the root) and builds/deploys on its own.
_Avoid_: app, project, page (when a Tool specifically is meant)

**lib**:
The shared package holding Egg, Inc. game data, calculations, and API access used by every Tool. The single source of truth for game constants and domain logic.

**ui**:
The shared package of common Vue UI components reused across Tools.

**Backup**:
A player's full game-save data, fetched from the Egg, Inc. API as a protobuf message (`ei.IBackup`). The raw input most Tools start from.
_Avoid_: save, savegame, game state (when the fetched backup is meant)

**EID**:
A player's Egg, Inc. identifier, entered to fetch their Backup.
_Avoid_: player ID, user ID, account ID

## Game Fundamentals

**Egg**:
The product a farm produces. The game has a fixed progression of egg types (Edible → Superfood → … → Enlightenment) plus limited-time Custom Eggs. Bare "egg" means this product egg — not Soul, Prophecy, Truth, or Virtue Eggs, which are always qualified.

**Soul Egg**:
The core permanent currency, kept across every prestige. Drives the Earning Bonus. Abbreviated SE.
_Avoid_: SE (in prose — spell it out)

**Prophecy Egg**:
A rare permanent egg earned from contracts, trophies, and gifts; each one multiplies the value of every Soul Egg. Abbreviated PE.
_Avoid_: eggs of prophecy, PE (in prose)

**Golden Egg**:
The premium currency used to buy Epic Research, boosts, and crafting. Spans prestiges.
_Avoid_: gold, gems

**Earning Bonus**:
The player's headline multiplier on earnings, derived from Soul Eggs and Prophecy Eggs (scaled by the Soul Food and Prophecy Bonus epic researches). Its magnitude sets the player's Farmer Role.
_Avoid_: earnings bonus, EB, bonus

**Farmer Role**:
The rank label a player earns from the size of their Earning Bonus (Farmer, Kilofarmer, … up the scale). The community's shorthand for progression.
_Avoid_: rank, title, tier (tier is reserved for artifacts)

**Permit**:
A player's account access level: Standard (free) or Pro (paid). Pro removes certain penalties and unlocks features.
_Avoid_: subscription, license, account type

**Prestige**:
Ending a run to bank Soul Eggs and reset the farm. The recurring loop the whole economy is built around.

**Epic Research**:
Permanent, account-wide upgrades bought with Golden Eggs; persist across prestiges.
_Avoid_: epics

**Common Research**:
Per-farm upgrades bought with cash; reset every prestige.
_Avoid_: regular research, normal research

**Colleggtible**:
A permanent multiplicative buff earned by laying enough of a limited-time Custom Egg.
_Avoid_: custom egg buff, collectible

**Trophy**:
A per-egg rank (Bronze, Silver, Gold, Platinum, Diamond) awarded for farm milestones. The Enlightenment Diamond is the game's ultimate trophy.

## The Farm

**Farm**:
A single egg-producing operation for one egg type. Prestiging resets the current farm.

**Enlightenment Farm**:
A farm running the Enlightenment egg, where artifact effects apply only through Clarity. The distinct regime targeted by the Enlightenment tool.

**Hab**:
A chicken house. The set of habs sets the maximum chicken Population.
_Avoid_: house, coop, henhouse

**Population**:
The current number of chickens, capped by total hab space.
_Avoid_: chickens (as a count), flock

**Vehicle**:
A shipping unit that carries eggs off the farm. Trains are vehicles measured in Train Cars.
_Avoid_: truck, transport

**Silo**:
Infrastructure setting how long a farm keeps running while the player is offline.

**Boost**:
A consumable giving a strong temporary effect (e.g. hatchery or earnings boosts), bought with Golden Eggs or tokens. Named boosts include Tachyon Prism, Boost Beacon, Soul Beacon, and Bird Feed.

**Running Chicken Bonus**:
A farm-wide earnings multiplier that builds up while the player is actively tapping, capped by a maximum (Max RCB) raised by research and artifacts. Abbreviated RCB.

**Internal Hatchery Rate**:
The rate new chickens are bred internally. Abbreviated IHR; differs online vs offline.

**Lay Rate**:
The raw rate at which chickens lay eggs, before any shipping limit.
_Avoid_: laying rate, egg rate

**Shipping Capacity**:
The maximum rate vehicles can ship eggs off the farm.
_Avoid_: shipping rate, transport capacity

**Effective Lay Rate**:
The rate of eggs actually shipped — the minimum of Lay Rate and Shipping Capacity. Abbreviated ELR.
_Avoid_: ELR (in prose — spell out on first use)

## Artifacts

**Artifact**:
An equippable item, recovered from missions, that buffs the farm. Equipped artifacts and Stones fill the slots of a Loadout.

**Family**:
A kind of artifact (e.g. a particular relic); each family comes in escalating Tiers.

**Tier**:
A power level within a family; higher tiers give stronger effects.

**Rarity**:
An artifact's quality — Common, Rare, Epic, or Legendary — adding slots and stronger effects at higher rarity.

**Slot**:
A socket on an artifact that holds a Stone; the number of slots rises with rarity.
_Avoid_: socket, port

**Stone**:
A consumable set into a slot to add a specific effect. Stone Fragments are crafted into Stones.

**Clarity**:
The effect, supplied by Clarity Stones (and intrinsic to the Light of Eggendil), that determines how much of an artifact's power applies on an Enlightenment Farm.

**Crafting**:
Building higher-tier artifacts and stones from ingredients via recipes, spending Golden Eggs and earning crafting XP.

**Loadout**:
A specific set of equipped artifacts and stones. A saved, named Loadout is an Artifact Set.

## Missions

**Spaceship**:
A rocket type used to fly missions; each has its own capacity, duration, and fuel needs.

**Mission**:
A single spaceship launch that consumes fuel and returns artifacts and byproducts as loot.
_Avoid_: launch (as the noun for the run — use mission)

**Duration Type**:
A mission's time-scale: Tutorial, Short, Standard (shown as "Long"), or Extended (shown as "Epic").
_Avoid_: mission length, difficulty tier

**Launch Point**:
Points earned per completed mission (scaled by Duration Type) that accumulate to raise a spaceship's level.
_Avoid_: mission score, experience, LP (in prose)

**Sensor**:
A spaceship's capability class (Basic → Next Generation) that gates which missions it can fly.
_Avoid_: scanner, radar

**Quality**:
A mission property — a base value and range — that determines the rarity band of artifacts it can return.
_Avoid_: rarity (rarity is the artifact's, quality is the mission's)

**Fuel**:
Eggs loaded into the fuel tank to launch missions.

**Loot**:
The artifacts and byproducts a mission returns on completion.
_Avoid_: drops (except when discussing probabilities), rewards

## Contracts

**Contract**:
A time-limited challenge to ship a goal amount of a specific egg, run solo or in a Co-op, rewarding cash, artifacts, and Prophecy Eggs.

**Co-op**:
A group of players pooling progress toward a shared Contract.
_Avoid_: team, group, guild

**Contract Season**:
A scheduled run of contracts grouped into a season, with its own cumulative season rewards.

**Leggacy**:
A re-run of a previously-released contract under the same identifier but a new expiry (the original runs ~3 weeks, leggacy re-runs ~1 week).
_Avoid_: incarnation, legacy, repeat, re-release

**Grade**:
A contract's difficulty tier in newer contracts — C, B, A, AA, AAA — setting the goal targets a player faces.
_Avoid_: difficulty, rank

**League**:
The older difficulty split — Elite and Standard — that Grade replaced in newer contracts.
_Avoid_: division, bracket

## Ascension

The newer endgame mode; central to the Ascension Planner and Virtue Companion tools.

**Ascension**:
A run of the Ascension game mode, during which the player lays Virtue Eggs and earns Truth Eggs.

**Virtue Egg**:
One of the five ascension eggs: Curiosity, Integrity, Kindness, Resilience, Humility. The one currently being laid is the _current egg_.

**Shift**:
Switching the current Virtue Egg to another. A shift costs Soul Eggs and permanently increments the Shift Count.
_Avoid_: switch, swap, egg change

**Shift Count**:
The permanent, ever-growing total of shifts the player has performed; drives the escalating Soul Egg cost of each further shift.

**Truth Egg**:
A permanent reward earned by shipping eggs during an ascension, tracked per Virtue Egg against fixed lifetime-shipped thresholds. Each applies a `1.1^TE` multiplier. Abbreviated TE.
_Avoid_: eggs of virtue, eov

**Clothed TE**:
An effective Truth Egg count adjusted down for missing Colleggtible bonuses and epic research — the "real" TE value given an imperfect setup. Abbreviated CTE.
_Avoid_: adjusted TE, effective TE

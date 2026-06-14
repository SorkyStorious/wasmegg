# Context Map

This repo is a suite of independent Egg, Inc. tools sharing one game vocabulary. The shared kernel lives in [`CONTEXT.md`](./CONTEXT.md); each tool that has vocabulary of its own keeps a `CONTEXT.md` next to its code.

**Read order:** always read the root [`CONTEXT.md`](./CONTEXT.md) first, then the relevant tool's `CONTEXT.md`. A term defined in root is never redefined per-tool; a per-tool file only adds what's unique to that tool.

## Shared kernel

- [`CONTEXT.md`](./CONTEXT.md) — the Egg, Inc. game language common to all tools (eggs, currencies, the farm, artifacts, missions, contracts, ascension), plus project building blocks (Tool, lib, ui, Backup, EID). Backed by the `lib` package.

## Tool contexts

- [eicoop](./eicoop/CONTEXT.md) — co-op & solo contract status tracker
- [artifact-explorer](./wasmegg/artifact-explorer/CONTEXT.md) — reference for artifacts, stones, ingredients, recipes, and mission drop rates
- [artifact-sandbox](./wasmegg/artifact-sandbox/CONTEXT.md) — build/evaluate artifact loadouts and their aggregate effects
- [smart-assistant](./wasmegg/smart-assistant/CONTEXT.md) — personalized prestige loadout generator and earning-bonus planner
- [rockets-tracker](./wasmegg/rockets-tracker/CONTEXT.md) — active missions, mission stats, and collection progress
- [virtue-companion](./wasmegg/virtue-companion/CONTEXT.md) — ascension/virtue progress report
- [ascension-planner](./wasmegg/ascension-planner/CONTEXT.md) — plan and optimize an ascension route
- [enlightenment](./wasmegg/enlightenment/CONTEXT.md) — companion for the Enlightenment Diamond Trophy
- [shell-company](./wasmegg/shell-company/CONTEXT.md) — cosmetics (shells, sets, hats, chickens) catalog
- [past-contracts](./wasmegg/past-contracts/CONTEXT.md) — contract history and prophecy-egg completion
- [mission-planner](./wasmegg/mission-planner/CONTEXT.md) — total fuel planner across multiple missions
- [legendary-study](./wasmegg/legendary-study/CONTEXT.md) — population statistics on legendary ownership
- [consumption-sheet](./wasmegg/consumption-sheet/CONTEXT.md) — artifact consumption outcomes
- [events](./wasmegg/events/CONTEXT.md) — calendar of in-game events
- [researches](./wasmegg/researches/CONTEXT.md) — SQL-queryable research database

## Tools with no unique vocabulary

These speak only the shared language; they have no `CONTEXT.md` of their own:

- `_home` — landing page indexing the suite
- `inventory-visualizer` — shares a player's artifact inventory as an image
- `proto-explorer` — explorer/exporter for the game's protobuf API messages
- `eggs-laid` — lists total eggs laid per egg
- `mission-list` — spaceship & mission parameter list (all its terms — Launch Point, Sensor, Quality, Duration Type — are shared and live in root)

> `loot-simulator` is still listed in `pnpm-workspace.yaml` and the root `package.json` workspaces but no longer exists in the tree (removed). Not a live context.

## Relationships

- **`lib` → every tool**: all tools depend on `lib` for game data, calculations, and API access; the shared kernel vocabulary is `lib`'s vocabulary.
- **rockets-tracker → legendary-study**: players opt in via rockets-tracker to contribute anonymized data to legendary-study's population dataset.
- **mission-list ↔ mission-planner ↔ rockets-tracker**: all three share mission/spaceship language (Launch Point, Duration Type, Sensor, Quality, Fuel) defined in root.
- **eicoop ↔ past-contracts**: both speak contract language (Contract, Co-op, Leggacy, Grade, League) defined in root; eicoop tracks live contracts, past-contracts tracks history.
- **artifact-explorer ↔ artifact-sandbox ↔ smart-assistant**: shared artifact/crafting language in root; explorer is reference data, sandbox is a configurator, smart-assistant is a recommender.
- **ascension-planner ↔ virtue-companion**: both speak Ascension language (Virtue Egg, Shift, Truth Egg, Clothed TE) defined in root; companion reports current progress, planner models a future route.

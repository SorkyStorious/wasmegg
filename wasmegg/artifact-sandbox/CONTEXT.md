# Artifact Sandbox

A configurator for building artifact loadouts and seeing their aggregate effect on every farm metric.

> Read the root [`CONTEXT.md`](../../CONTEXT.md) first — Artifact, Stone, Slot, Loadout, Clarity, Enlightenment Farm, Running Chicken Bonus, Effective Lay Rate, Colleggtible, and Clothed TE are defined there. This file adds only Sandbox terms.

## Language

**Build**:
A set of exactly four artifacts (each with up to three stones) assembled to evaluate together.
_Avoid_: inventory, collection, selection

**Active stone**:
A stone in a slot within the artifact's effective slot count; stones beyond that count contribute nothing.

**Effect aggregation**:
The rule for combining many artifact and stone contributions into a final metric — additively (summing deltas) or multiplicatively (compounding them).
_Avoid_: stacking, combining

**Virtue farm**:
A sandbox mode where Earning Bonus is computed from Truth Eggs (`1.1^TE − 1`) instead of Soul Eggs. (Distinct from the mission-planner's "virtue farm", which is about fuel.)

**Max effective lay rate**:
Total hourly shipped-egg rate assuming fully populated habs with all relevant artifacts active.

**Dampening exponent**:
The fixed exponent (0.21) applied to virtual earnings multipliers when deriving soul-egg gain rate, modeling late-game diminishing returns.

**Stone-setting cost**:
The cash price to set or swap a stone: `floor(0.05 × artifact base price + 0.1 × stone base price)`.

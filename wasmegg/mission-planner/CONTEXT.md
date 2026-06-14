# Mission Planner

Calculates the total fuel needed to run a chosen set of missions, checking it against tank capacity.

> Read the root [`CONTEXT.md`](../../CONTEXT.md) first — Mission, Spaceship, Duration Type, Launch Point, Fuel, and Virtue Egg are defined there. This file adds only Mission Planner terms.

## Language

**Fuel Tank**:
The on-ship store holding all mission fuel; capacity rises across fixed upgrade levels.
_Avoid_: cargo tank, fuel capacity

**Virtue farm mission**:
A chicken-spaceship mission (Chicken One/Nine/Heavy) fueled with Virtue Eggs instead of standard eggs and not refuelable — treated as "infinite" fuel for planning. (Distinct from the artifact-sandbox "virtue farm", which is an Earning Bonus mode.)
_Avoid_: virtue farm (unqualified — it's ambiguous across tools)

**Fuel breakdown**:
The per-mission and total fuel table for the selected plan.

**Tank capacity constraint**:
The check flagging when planned fuel exceeds tank capacity, making the plan infeasible without upgrades or fewer launches.

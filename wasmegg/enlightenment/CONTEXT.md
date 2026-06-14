# Enlightenment Companion

A calculator for reaching the Enlightenment Diamond Trophy: projects farm metrics and the artifact/research setup needed to hit the 10-billion-chicken target.

> Read the root [`CONTEXT.md`](../../CONTEXT.md) first — Enlightenment Farm, Clarity, Running Chicken Bonus, Trophy, Hab, and the rate terms are defined there. This file adds only Enlightenment terms.

## Language

**Gusset**:
The Ornate Gusset artifact, which multiplies hab space on an Enlightenment Farm. The tool finds the best stoned gusset to minimize required Wormhole Dampening.

**Cube**:
The Puzzle Cube artifact, which cuts research prices on an Enlightenment Farm.

**Wormhole Dampening**:
The hab-space research that unlocks the 10-billion-chicken Diamond target; the tool computes the exact level needed. Abbreviated WD.

**Farm value**:
A composite score (egg value, lay rate, shipping, earning bonus, Max RCB, hab metrics, away earnings) that the game uses for trophy thresholds.
_Avoid_: farm worth, score

**Population effective**:
Chickens whose eggs actually ship — capped by `min(lay rate, shipping capacity)`.

**Population undeliverable**:
Chickens whose eggs can't ship due to a shipping bottleneck; weighted into farm value.

**Population vacant**:
Empty hab capacity; weighted into farm value.

**Population projected**:
Chickens expected to hatch during away time (from IHR and max away time); weighted into farm value.

**Naked gang**:
Players who finish the Enlightenment Diamond with no artifacts equipped; gusset recommendations don't apply to them.

**Drone values**:
The reward tiers (tier1/tier2/tier3/elite) and probabilities for prestige drones, set by farm value per chicken and research level.

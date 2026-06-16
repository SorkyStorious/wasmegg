# Ascension Planner

A tool to model an ascension route step by step — purchases and shifts over time — projecting rates, earnings, and Truth Egg gains, and optionally generating an optimized route.

> Read the root [`CONTEXT.md`](../../CONTEXT.md) first — Ascension, Virtue Egg, Shift, Shift Count, Truth Egg, Clothed TE, and the farm/rate terms are defined there. This file adds only Ascension Planner terms.

## Language

**Plan**:
A modeled ascension route: an ordered list of Actions plus the configuration to reproduce it. A plan may span one or more chained ascensions.

**Action**:
The atomic, ordered unit of a Plan — one thing the player does (buy research, buy hab, shift, launch missions, wait, …). Actions are the source of truth; everything else is derived from them.
_Avoid_: step, move, operation

**Snapshot**:
The full set of computed outputs (rates, earnings, bank, population, …) at the end of an Action. Derived, never authored.
_Avoid_: state dump

**Mode**:
One of the five ways to start a planning session, each with its own state contract: Start from Scratch, Plan Future, Continue Current, Reconcile, Load Saved Plan.

**Continue Current**:
The Mode that carries the player's live farm state forward into a new plan.

**Plan Future**:
The Mode that uses account-wide progress (epic research, artifacts, TE) but zeroes farm state to model a fresh future ascension.

**Reconcile**:
The Mode (and the act) of comparing a saved Plan against the player's live Backup to see where reality diverged from the plan.

**Continuity**:
The rule that Actions stay mutually consistent — inserting or removing one must not leave later Actions depending on state that no longer holds. A Continuity conflict is surfaced before the change applies.

**Auto-Planner**:
The generator that produces an optimized Plan by simulating shift sequences, rather than the user building Actions by hand.
_Avoid_: solver, optimizer (as the user-facing name)

**Plan Library**:
The collection of saved Plans the user can load or reconcile against.

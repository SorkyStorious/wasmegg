# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

This repo is **multi-context**: a root `CONTEXT.md` holds the shared Egg, Inc. game language common to every tool, `CONTEXT-MAP.md` indexes the contexts, and each significant tool keeps its own `CONTEXT.md` next to its code.

## Before exploring, read these

- **`CONTEXT-MAP.md`** at the repo root — lists every context and how they relate.
- **`CONTEXT.md`** at the repo root — the shared kernel. Always read this first.
- The relevant tool's **`CONTEXT.md`** (e.g. `wasmegg/<tool>/CONTEXT.md` or `eicoop/CONTEXT.md`) for terms unique to the tool you're working in.
- **`docs/adr/`** — read ADRs that touch the area you're about to work in.

A term defined in root is never redefined per-tool; a per-tool file only adds what's unique to that tool. If any of these files don't exist, **proceed silently** — the producer skill (`/grill-with-docs`) creates them lazily as terms and decisions get resolved.

## File structure

```
/
├── CONTEXT.md            ← shared Egg, Inc. game language (the kernel)
├── CONTEXT-MAP.md        ← index of contexts + relationships
├── docs/adr/             ← architectural decisions
├── eicoop/CONTEXT.md
└── wasmegg/
    ├── ascension-planner/CONTEXT.md
    ├── artifact-explorer/CONTEXT.md
    ├── ... (one per significant tool)
```

Tools with no vocabulary of their own (e.g. `_home`, `inventory-visualizer`, `proto-explorer`, `eggs-laid`, `mission-list`) have no `CONTEXT.md` and rely solely on the root kernel.

## Use the glossary's vocabulary

When your output names a domain concept (an issue title, a refactor proposal, a hypothesis, a test name), use the term as defined in the relevant `CONTEXT.md`, and avoid the synonyms each entry lists under `_Avoid_`.

If the concept you need isn't in the glossary yet, that's a signal — either you're inventing language the project doesn't use (reconsider) or there's a real gap (note it for `/grill-with-docs`).

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding:

> _Contradicts ADR-0003 (…) — but worth reopening because…_

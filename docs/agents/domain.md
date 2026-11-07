# Domain Docs

How the engineering skills should consume this repo's domain documentation when exploring the codebase.

## Before exploring, read these

- **`DOMAIN.md`** at the repo root, or
- **`DOMAIN-MAP.md`** at the repo root if it exists: it points at one `DOMAIN.md` per context. Read each one relevant to the topic.
- **`docs/adr/`**: read ADRs that touch the area you're about to work in. In multi-context repos, also check `src/<context>/docs/adr/` for context-scoped decisions.

If any of these files don't exist, **proceed silently**. Don't flag their absence; don't suggest creating them upfront. The `/domain-modeling` skill (reached via `/grill-with-docs` and `/improve-codebase-architecture`) creates them lazily when terms or decisions actually get resolved.

## File structure

Single-context repo (most repos):

```
/
├── DOMAIN.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

Multi-context repo (presence of `DOMAIN-MAP.md` at the root):

```
/
├── DOMAIN-MAP.md
├── docs/adr/                          ← system-wide decisions
└── src/
    ├── ordering/
    │   ├── DOMAIN.md
    │   └── docs/adr/                  ← context-specific decisions
    └── billing/
        ├── DOMAIN.md
        └── docs/adr/
```

## Use the domain vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, or a test name), use the term defined in `DOMAIN.md`. Keep the canonical term when the file excludes synonyms.

If `DOMAIN.md` lacks a needed concept, check whether the project uses it before adding it through `/domain-modeling`.

## Flag ADR conflicts

If your output contradicts an existing ADR, surface it explicitly rather than silently overriding:

> _Contradicts ADR-0007 (event-sourced orders), but worth reopening because…_

# Contributing

## Branching model (lightweight GitFlow)

| Branch | Purpose |
| --- | --- |
| `main` | Always demo-able. Only receives merges from `develop` at milestone ends. Tagged `v0.x`. |
| `develop` | Integration branch. Feature branches merge here via PR. |
| `feature/<area>-<short-name>` | New functionality, e.g. `feature/auth-catalog`, `feature/nfc-borrow`. |
| `docs/<topic>` | Documentation-only work, e.g. `docs/threat-model`. |
| `spike/<topic>` | Time-boxed experiments. Findings go into an ADR; code may be discarded. |
| `fix/<short-name>` | Bug fixes. |

Branch from `develop`, open a PR back to `develop`, squash-merge.

## Commit style

[Conventional Commits](https://www.conventionalcommits.org/) with the area as scope:

```
feat(loans): block borrow when copy is on hold
fix(sync): reject duplicate op ids
docs(adr): record sync strategy
```

Scopes: `mobile`, `admin`, `api`, `auth`, `catalog`, `shelves`, `copies`, `loans`, `returns`, `audit`, `sync`, `identifiers`, `infra`, `docs`.

## Definition of done

- Tests cover the loan rules, tag validation and sync conflicts you touched
- CI is green
- Any decision that changes Section 4 of the project context gets an ADR

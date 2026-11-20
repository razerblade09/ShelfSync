# Library System

A mobile-first, **shelf-aware, offline-first** library management system for a school or university library.

> **Status: planning / pre-implementation.** Nothing in this repo is built yet. The folders below are the target structure; see [docs/prd/PRD.md](docs/prd/PRD.md) and [docs/open-questions.md](docs/open-questions.md).

## What makes it different

Most library apps track only whether a book is borrowed. This one also knows **where each physical copy belongs and where it was last seen**.

- Shelf tags act as addresses (floor, aisle, shelf); each copy has a home shelf.
- Students get directions to the exact shelf for a book.
- Librarian **audit mode**: tap a shelf, scan books, get a report of misplaced, missing and unexpected items.
- **Offline-first** mobile app: actions queue locally and sync later with conflict handling.
- NFC is the primary identifier, behind a pluggable `BookIdentifier` interface (QR as fallback, computer vision as an experiment).

## Repository layout

```
apps/
  mobile/            Student + librarian mobile app (Flutter, proposed)
  admin-web/         Admin / librarian dashboard (stack TBD)
services/
  api/               Backend modular monolith (NestJS, proposed)
    src/modules/     auth, users, catalog, shelves, copies, loans, returns,
                     audit, sync, notifications, identifiers, policies
packages/
  api-contract/      OpenAPI spec + generated clients (single source of truth)
  identifier-spec/   BookIdentifier interface + tag payload/signature spec
infra/
  docker/            Dockerfiles, local compose
  deploy/            Free-tier deployment config
tools/
  nfc-spike/         Throwaway NFC read/write experiments
  seed/              Seed data generator (catalog, shelves, users)
docs/
  prd/               PRD and user stories
  architecture/      System architecture overview
  adr/               Architecture decision records
  threat-model/      Abuse cases and mitigations
  domain/            Domain model, copy state machine
  demo/              Demo script, screenshots, video
```

## Documentation

- [PRD](docs/prd/PRD.md) and [user stories](docs/prd/user-stories.md)
- [Architecture overview](docs/architecture/overview.md)
- [Copy state machine](docs/domain/copy-state-machine.md)
- [Threat model (draft)](docs/threat-model/README.md)
- [ADRs](docs/adr/)
- [Open questions](docs/open-questions.md)

## Roadmap

1. **M0** Decisions: answer open questions, NFC spike, state machine, threat model
2. **M1** Online core: auth, catalog, NFC borrow/return
3. **M2** Audit mode and reshelving queue
4. **M3** Offline queue and sync
5. **M4** Portfolio packaging: demo video, tests, live link

## Contributing / workflow

See [CONTRIBUTING.md](CONTRIBUTING.md) for the branching model and commit style.

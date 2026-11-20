# PRD (draft, awaiting owner review)

**Goal:** a library system for a school or university where borrowing and returning needs no desk, books can be found on the shelf, and inventory audits take minutes, even with unreliable connectivity.

## Settled decisions

| Topic | Decision |
| --- | --- |
| Setting | School or university library |
| Purpose | Portfolio project (architecture doc, demo, tests, live link) |
| Identification | NFC tags on copies and shelves; QR as fallback; CV experimental |
| Design principle | Pluggable `BookIdentifier` interface |
| Core concept | Shelf-aware, offline-first, signed tags |
| Roles in MVP | Student, librarian, admin |
| Platforms | Android and iOS |
| Library rule | A book may be outside the library only if borrowed |

## MVP scope

**In:** S1-S4, L1-L3, L6, A1-A2. NFC behind a pluggable interface. Signed tags and return-station proof. Offline queue and sync for borrow/return.

**Out of MVP:** holds and renewals (S5, S6), proxy borrowing and fine waivers (L4, L5), tag key management UI (A3), exit check (L7), Read here (S8), recommendations and analytics (S7, A4), computer-vision audit, RFID, BLE navigation, university SSO.

> Review note: the in-scope list is large for a solo project. The milestones in the README stage it: online core first, then audit, then offline sync.

## Non-functional requirements (proposed targets)

| Area | Requirement |
| --- | --- |
| Offline | Cached search, borrow and return work without connectivity; queued actions sync on reconnect. Conflict ordering: see ADR-0004 (open) |
| Consistency | A copy can never be loaned to two students (transactions and row locking) |
| Security | Signed tag payloads; short-lived station proofs; RBAC; TLS; audit log of loans, returns and admin actions |
| Performance | Tap-to-confirmation under 2 s online; catalog search under 500 ms at ~100,000 copies; ~2,000 active students. Unvalidated until a seeded load test exists |
| Usability | Borrow in two taps after finding the book; one-handed use; contrast and font scaling |
| Privacy | Students see only their own loan history; staff access role-limited and logged |
| Platforms | Android and iOS from one codebase; NFC tested on physical devices |
| Maintainability | Modular monolith; automated tests on loan rules, tag validation, sync conflicts; CI on every push |

## Portfolio success criteria

Working demo of borrow, return and audit flows; short demo video; architecture doc with threat model; tests on the hard logic; live deployed link.

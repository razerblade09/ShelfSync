# Threat model (draft, Step 4 of the process)

To be completed before schema and API design. Seeded with the abuse cases from the project context plus gaps found in review.

| # | Abuse case | Current mitigation | Gap / to decide |
| --- | --- | --- | --- |
| 1 | Fake return from home | Return-station proof (rotating authenticated codes) + `return_pending` | Station key storage and rotation |
| 2 | Walk out without confirming a borrow | Exit check; audit-based detection | Depends on door checkpoint (open question 1) |
| 3 | Cloned / forged tag | Signed per-tap code verified by server (NTAG 424 DNA style) | Verify against current tag and OS docs |
| 4 | **Replay of a captured tap** (offline) | Not yet defined | Per-tap counter checked on sync |
| 5 | **Provisional loan never synced** | Not yet defined | Expiry time and failure handling |
| 6 | **Manipulated device clock** | "Earliest timestamp wins" | Unsafe; use server order or tag counter (ADR-0004) |
| 7 | Two students borrow the last copy offline | Conflict rule + notify | Needs deterministic ordering |
| 8 | Lost / stolen phone | Re-login with device binding | Remote session revocation |
| 9 | Stolen tag keys | Key rotation (A3, post-MVP) | Per-tag diversified keys vs shared key |
| 10 | Privacy leak of loan history | Own-history-only, role-limited logged staff access | Retention policy |

## Next

- Add trust boundaries to a data-flow diagram
- Rate each case (likelihood / impact) and choose MVP mitigations

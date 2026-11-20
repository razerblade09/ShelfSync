# Copy state machine (draft)

The project context models location as two zones (`IN_LIBRARY`, `BORROWED`). That leaves gaps, for example a returned-but-unconfirmed book. This draft makes status explicit so every transition is checkable. **Proposed, not yet agreed.**

## States

| State | Meaning |
| --- | --- |
| `ON_SHELF` | In the library, on its home shelf |
| `OFF_SHELF` | In the library, not on its home shelf (table, cart, wrong shelf); goes to the reshelving queue |
| `BORROWED` | Loaned to a student; allowed outside the library |
| `RETURN_PENDING` | Student tapped a return station; awaiting librarian scan or shelf-audit confirmation |
| `UNACCOUNTED` | Not borrowed, not found after a full sweep and the grace window (possible theft) |
| `LOST` | Confirmed lost (e.g. borrower reported, or unaccounted resolved as lost) |
| `DAMAGED` | Pulled from circulation for repair |
| `WITHDRAWN` | Permanently removed from the collection |

## Transitions

```mermaid
stateDiagram-v2
    [*] --> ON_SHELF: register copy (L3)
    ON_SHELF --> BORROWED: borrow (S2)
    OFF_SHELF --> BORROWED: borrow (S2)
    BORROWED --> RETURN_PENDING: station tap (S3)
    RETURN_PENDING --> ON_SHELF: librarian scan / audit finds on home shelf (L2)
    RETURN_PENDING --> BORROWED: never confirmed, loan reopens, fines apply
    ON_SHELF --> OFF_SHELF: audit finds missing from shelf, seen elsewhere
    OFF_SHELF --> ON_SHELF: reshelved (L6)
    OFF_SHELF --> UNACCOUNTED: full sweep + grace window elapsed
    ON_SHELF --> UNACCOUNTED: full sweep + grace window elapsed
    UNACCOUNTED --> ON_SHELF: found and reshelved
    UNACCOUNTED --> LOST: confirmed lost
    BORROWED --> LOST: borrower reports lost / overdue limit
    ON_SHELF --> DAMAGED: pulled for repair
    DAMAGED --> ON_SHELF: repaired
    DAMAGED --> WITHDRAWN
    LOST --> WITHDRAWN
    LOST --> ON_SHELF: recovered
```

## Rules to enforce in code

- A copy in `BORROWED` has exactly one open loan; any other state has none.
- Only `ON_SHELF` and `OFF_SHELF` copies can be borrowed.
- Unborrowed copies may not leave the library (exit check, L7).
- Every transition writes an audit-log row (actor, time, reason).

## Still undefined

- Grace window length and its trigger (see [open questions](../open-questions.md))
- Fine handling when `RETURN_PENDING` reopens

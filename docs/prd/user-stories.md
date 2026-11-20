# User stories (approved draft)

Priority: **Must** = MVP, **Should** = after MVP, **Later** = backlog.

## Student

| ID | Pri. | Story |
| --- | --- | --- |
| S1 | Must | Search the catalog and see availability and shelf location (cached search works offline) |
| S2 | Must | Borrow by tapping shelf tag then book; blocked by fines, loan limit or another student's hold; works offline via queue |
| S3 | Must | Return at a station; station tap required; loan becomes `return_pending` |
| S4 | Must | See own loans and get due-date reminders |
| S5 | Should | Place a hold and be notified when ready |
| S6 | Should | Renew a loan once if no one is waiting |
| S7 | Later | Recommendations and reading history |
| S8 | Later | Mark a book as "Read here" (optional in-house session with auto-expiry) |

## Librarian

| ID | Pri. | Story |
| --- | --- | --- |
| L1 | Must | Audit a shelf and see misplaced, unexpected and unaccounted books; grace window before flagging unaccounted |
| L2 | Must | Confirm pending returns |
| L3 | Must | Register a new copy: program and sign its NFC tag, assign a shelf |
| L4 | Should | Borrow or return on a student's behalf |
| L5 | Should | Waive or adjust fines |
| L6 | Must | Sweep reading areas and manage the reshelving queue |
| L7 | Should | Exit check flags unborrowed books leaving the library |

## Admin

| ID | Pri. | Story |
| --- | --- | --- |
| A1 | Must | Manage users and roles, including bulk import from a student list |
| A2 | Must | Configure policies: loan period, loan limit, fine rate |
| A3 | Should | Manage shelves and stations; rotate or revoke tag keys |
| A4 | Later | Analytics dashboard (demand, hold wait times) |

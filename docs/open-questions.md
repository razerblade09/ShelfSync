# Open questions

These block or shape design decisions. Answer them, then record the outcome as an ADR.

1. **Door checkpoint?** Is there a desk, guard or gate? Decides the exit-check design (L7).
2. **Reading areas?** Can books be carried anywhere, or are there defined reading areas? Defined areas make the librarian sweep (L6) easier.
3. **Deadline / time budget** for the MVP?
4. **NFC hardware for the demo:** real tags, simulated tags, or both? How many tags can you buy?
5. **Roles in MVP:** student, librarian, admin (currently assumed; confirm).

## Added during review

6. **Grace window length** before a missing copy becomes `UNACCOUNTED`, and what triggers the clock.
7. **Offline ordering:** client timestamps can be wrong or manipulated. Prefer server-assigned order on sync or a tag counter. See ADR-0004.
8. **Provisional loan expiry:** how long can an unsynced offline loan stay provisional, and what happens if verification then fails?
9. **Android-first or both platforms?** iOS needs a Mac, a physical iPhone and a paid developer account for NFC.
10. **Stack lock:** Flutter vs React Native, NestJS vs Spring Boot. Currently proposed, not confirmed.

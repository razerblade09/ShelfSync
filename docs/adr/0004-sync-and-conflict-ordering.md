# ADR-0004: Sync strategy and conflict ordering

- **Status:** Open

## Context
The project context proposes a custom operation log with "earliest timestamp wins". Client clocks can be wrong or manipulated, so client timestamps are not a safe ordering.

## Options
1. Server-assigned order on arrival, with the client's original time kept only for display
2. Use the secure tag's per-tap counter as ordering/replay evidence
3. Adopt an existing sync layer (e.g. PowerSync, ElectricSQL) instead of a custom one
4. Simple outbox pattern with idempotent operation IDs

## Decision
Pending. Whatever is chosen must define: idempotency of ops, provisional-loan expiry, and the user-facing message when an offline op is rejected.

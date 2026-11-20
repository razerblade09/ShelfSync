# ADR-0001: Pluggable BookIdentifier; NFC primary

- **Status:** Accepted (settled in project context, Section 4)

## Context
The original idea used QR codes; the owner considers QR dated.

## Decision
Define a `BookIdentifier` interface. NFC is the primary implementation, QR the cheap fallback, computer vision an experimental option for audit mode. A simulated implementation is used for tests and demos without hardware.

## Consequences
Hardware can change without touching loan or audit logic. The interface and tag payload spec live in `packages/identifier-spec`.

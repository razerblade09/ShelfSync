# ADR-0002: Modular monolith backend (NestJS + PostgreSQL)

- **Status:** Proposed (awaiting owner confirmation; Spring Boot is an equal alternative)

## Decision
NestJS (TypeScript) as a modular monolith, PostgreSQL for data. Postgres gives transactions and row locking for the last-copy race.

## Consequences
One deployable, clear module boundaries under `services/api/src/modules`. Revisit only if a module needs independent scaling, which is unlikely at ~2,000 students.

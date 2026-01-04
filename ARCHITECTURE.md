# Architecture Overview

## System Design
The system is built as a modular, event-driven pipeline composed of
independent ingestion, evaluation, and presentation layers.

## Core Components
- **Ingestion Workers**: Collect raw signals from external sources.
- **Decision Engine**: Evaluates signals against deterministic invariants.
- **Persistence Layer**: Stores state transitions and evaluations.
- **Dashboard**: Presents real-time system posture and decision outputs.

## Concurrency Model
- Background workers process events asynchronously.
- State transitions are serialized through invariant checks.
- SQLite WAL mode ensures deterministic write behavior.

## Failure Handling
- Failed ingestions are retried with backoff.
- Invalid signals are discarded at invariant boundaries.
- System state remains consistent under partial failure.

## Scalability Notes
- Ingestion and evaluation layers can be horizontally scaled.
- Database layer can be migrated to PostgreSQL if required.

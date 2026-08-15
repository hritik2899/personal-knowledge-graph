# Architecture

## Goal

The system should represent personal knowledge as a graph while retaining source documents and embeddings for semantic retrieval.

## Core Model

```text
                    ┌─────────────────────┐
                    │       Sources       │
                    │ docs / GitHub /     │
                    │ notes / manual data │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Ingestion Layer   │
                    │ parse / normalize   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Extraction Pipeline │
                    │ entities + relations│
                    └───────┬───────┬─────┘
                            │       │
                   ┌────────▼─┐ ┌──▼─────────┐
                   │   Graph  │ │   Vector   │
                   │  Store   │ │   Store    │
                   └────┬─────┘ └─────┬──────┘
                        │             │
                        └──────┬──────┘
                               ▼
                    ┌─────────────────────┐
                    │ Hybrid Retrieval    │
                    │ graph + semantic    │
                    └──────────┬──────────┘
                               ▼
                    ┌─────────────────────┐
                    │ AI / Agent Layer    │
                    └──────────┬──────────┘
                               ▼
                    ┌─────────────────────┐
                    │ API / UI / MCP      │
                    └─────────────────────┘
```

## Design Principles

1. Every important fact should have provenance.
2. Prefer structured relationships over storing everything as text.
3. Keep ingestion idempotent.
4. Separate source data from derived graph/vector data.
5. Support both exact graph queries and semantic retrieval.
6. Keep the first implementation simple enough to run locally.

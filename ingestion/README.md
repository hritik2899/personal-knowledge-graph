# Ingestion Layer

The ingestion layer converts external data into normalized source records and graph candidates.

## Pipeline

1. Discover files / sources.
2. Parse without losing original metadata.
3. Normalize into `Source`, `Conversation`, `Message`, or `Document` records.
4. Chunk long text for embeddings.
5. Extract entities and typed relationships.
6. Resolve entities against the existing graph.
7. Write graph nodes/edges with provenance.
8. Generate/update embeddings.
9. Record an ingestion checkpoint.

## Required adapters

- `chatgpt_export`
- `documents`
- `github`
- `resume`
- `manual_json`

## Idempotency

Every source object gets a stable deterministic identifier derived from the source system and source id. Re-running ingestion should update existing records rather than duplicate them.

## ChatGPT importer

See [`docs/chatgpt-import.md`](../docs/chatgpt-import.md). The official export must be supplied by the user; the application cannot directly access the user's entire ChatGPT account history.

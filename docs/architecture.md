# Production Architecture

```text
                         +----------------------+
                         |   Personal Sources   |
                         |----------------------|
                         | ChatGPT export       |
                         | PDFs / notes / docs   |
                         | GitHub / code        |
                         | Resume / projects    |
                         | Manual memories      |
                         +----------+-----------+
                                    |
                                    v
                         +----------------------+
                         | Ingestion + Normalize|
                         +----------+-----------+
                                    |
                                    v
                    +-------------------------------+
                    | Entity / Relation Extraction  |
                    | facts, topics, preferences,   |
                    | projects, decisions, events   |
                    +---------------+---------------+
                                    |
                  +-----------------+------------------+
                  |                                    |
                  v                                    v
       +--------------------+              +--------------------+
       | Property Graph DB  |              | Vector Store       |
       | entities + edges   |              | chunks + embeddings|
       +---------+----------+              +---------+----------+
                 |                                   |
                 +----------------+------------------+
                                  v
                         +-------------------+
                         | Hybrid Retrieval  |
                         | graph + semantic  |
                         +---------+---------+
                                   |
                                   v
                         +-------------------+
                         | Memory / RAG Agent |
                         +---------+---------+
                                   |
                    +--------------+---------------+
                    |              |               |
                    v              v               v
                  API             UI              MCP
```

## Design principles

1. **Raw data is immutable.** Keep original source records.
2. **Every extracted fact has provenance.** Never lose the source message/document.
3. **Temporal knowledge matters.** A preference or fact can change over time.
4. **Contradictions are data.** Store competing claims with timestamps and confidence.
5. **Graph and vector retrieval are complementary.** Graph handles explicit relationships; vectors handle semantic similarity.
6. **Privacy first.** Secrets and raw private data should never be committed to Git.
7. **Incremental ingestion.** Re-importing the same source must be idempotent.

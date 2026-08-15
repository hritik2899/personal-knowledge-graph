# Personal Knowledge Graph

A personal knowledge graph and AI memory system for connecting my projects, skills, experiences, people, companies, documents, notes, and ideas.

## Vision

Build a private, searchable representation of my knowledge that combines a graph database, semantic search, structured entities, and an AI interface.

## Initial Architecture

```text
Sources
  ├── Documents / Notes
  ├── GitHub
  ├── Projects / Resume
  └── Manual Knowledge
          │
          ▼
     Ingestion Layer
          │
          ▼
   Entity + Relation Extraction
          │
      ┌───┴────┐
      ▼        ▼
 Graph Store  Vector Store
      │        │
      └───┬────┘
          ▼
   Retrieval / RAG Layer
          │
          ▼
     AI / Agent Layer
          │
          ▼
       API / UI / MCP
```

## Planned Capabilities

- Entity and relationship management
- Document ingestion and parsing
- Semantic search
- Graph traversal and context retrieval
- Hybrid graph + vector RAG
- Personal timeline and project history
- AI assistant over personal knowledge
- MCP interface for agent/tool access
- Source provenance and confidence tracking

## Repository Structure

```text
architecture/   Architecture and design decisions
data/           Seed data and graph schemas
ingestion/      Data ingestion pipelines
graph/          Graph models and storage
retrieval/      Graph + vector retrieval
agents/         AI/agent workflows
api/            Backend API
frontend/       Web interface
docs/            Documentation
config/         Configuration
tests/          Tests
```

## Status

🚧 Initial architecture — implementation starts here.

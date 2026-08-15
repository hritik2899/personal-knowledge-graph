# ChatGPT History Import

The graph is designed to ingest a user's complete ChatGPT export rather than relying on the assistant's conversational context.

## Important limitation

This application cannot automatically read every historical ChatGPT conversation from the ChatGPT account. The user must export their ChatGPT data and provide the export to this application.

## Target input

The importer should support the official ChatGPT data export, especially `conversations.json`, and preserve:

- conversation id
- conversation title
- timestamps
- message ids
- role (user/assistant/system/tool)
- message text
- parent/child message relationships when present
- model metadata when present
- conversation metadata

## Processing pipeline

```text
ChatGPT export
      |
      v
Normalizer
      |
      +--> Conversation nodes
      +--> Message nodes
      +--> Topic/entity extraction
      +--> Claims/facts
      +--> Preferences
      +--> Projects
      +--> Decisions
      +--> Questions
      +--> Skills/technologies
      |
      v
Relationship extraction
      |
      +--> mentioned_in
      +--> contains
      +--> about
      +--> relates_to
      +--> answers
      +--> asks
      +--> supports
      +--> contradicts
      +--> prefers
      +--> uses
      +--> worked_on
      +--> learned
      +--> decided
      +--> evolved_from
      |
      v
Graph + embeddings + provenance
```

Never treat an extracted fact as ground truth without retaining its source message and extraction confidence.

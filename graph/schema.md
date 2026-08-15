# Knowledge Graph Schema

The graph uses a typed property-graph model. Every important assertion is traceable to source data.

## Core node types

`Person`, `Conversation`, `Message`, `Topic`, `Project`, `Company`, `Role`, `Skill`, `Technology`, `Document`, `Idea`, `Goal`, `Decision`, `Preference`, `Fact`, `Question`, `Answer`, `Event`, `Job`, `Education`, `Location`, `Organization`, `Repository`, `Task`, `Experience`, `Source`.

## Universal properties

Every node may contain `id`, `type`, `name`, `description`, `created_at`, `updated_at`, `valid_from`, `valid_to`, `confidence`, `source_ids`, `embedding_id`, and `metadata`.

## Relationship vocabulary

### Conversation / message
`CONTAINS`, `NEXT_MESSAGE`, `REPLIES_TO`, `MENTIONS`, `ABOUT`, `ASKS`, `ANSWERS`, `REFERENCES`, `GENERATED_FROM`

### Knowledge
`RELATES_TO`, `SUPPORTS`, `CONTRADICTS`, `DERIVED_FROM`, `INSTANCE_OF`, `PART_OF`, `SIMILAR_TO`, `DEPENDS_ON`

### Person
`OWNS`, `PREFERS`, `INTERESTED_IN`, `LEARNED`, `KNOWS`, `WORKED_ON`, `WORKED_AT`, `STUDIED_AT`, `LIVES_IN`, `FROM`, `HAS_GOAL`

### Work / projects
`EMPLOYED_BY`, `HAS_ROLE`, `BUILT`, `CONTRIBUTED_TO`, `USES`, `IMPLEMENTED_WITH`, `DEPLOYED_ON`, `IMPROVES`, `REPLACED`, `MIGRATED_TO`

### Temporal / evolution
`PRECEDED_BY`, `FOLLOWED_BY`, `EVOLVED_FROM`, `CHANGED_TO`, `DECIDED_ON`, `OCCURRED_AT`

### Preferences / behavior
`PREFERS`, `DISLIKES`, `WANTS`, `AVOIDS`, `TENDS_TO`, `USES_FREQUENTLY`

## Provenance

A relationship can carry:

```json
{
  "confidence": 0.94,
  "source_id": "msg_xxx",
  "extraction_method": "llm",
  "created_at": "..."
}
```

Conflicting historical statements are retained rather than silently overwritten.
# Graph Schema

The initial graph is intentionally small and extensible.

## Nodes

- `Person`
- `Company`
- `Project`
- `Skill`
- `Document`
- `Experience`
- `Technology`
- `Concept`
- `Event`

## Relationships

- `Person -[WORKED_AT]-> Company`
- `Person -[BUILT]-> Project`
- `Person -[KNOWS]-> Skill`
- `Project -[USES]-> Technology`
- `Project -[DOCUMENTED_BY]-> Document`
- `Project -[RELATED_TO]-> Concept`
- `Experience -[AT_COMPANY]-> Company`
- `Experience -[INVOLVES]-> Project`
- `Event -[ABOUT]-> Concept`

## Provenance

Every derived fact should eventually support:

- source identifier
- source type
- extraction timestamp
- confidence
- optional source span / citation

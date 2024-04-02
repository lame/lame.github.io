
## Primitive Actions

- Move-body-part
- Move-object
- Expel
- Ingest
- Propel
- Speak
- See
- Hear
- Smell
- Feel
- Move-possession
- Move-concept (idea to go somewhere for instance)
- Think-about
- Conclude

Primitives create an ontology of the world

Verbs can be replaced with primitives:

- shot -> propelled a bullet
- fertalized -> spread fertilizer
- decided -> conclude

Each primitive should have an associated frame:

```text
Action Frame
- primitive: propel
- agent:
- object:
```

```text
Action Frame
- primitive: move-possession
- agent: [animate object before verb]
- coagent:
- object: [inanimate object after verb ]
```

## Hierarchical actions and sub-actions

![action frame sub action](./assets/action_frame_sub_action.png)

![multi verb](./assets/multi_verb.png)

### Example

"Anika decided to have a glass of water"

1) decided (verb) -> conclude
2) Conclude frame:

```text
Action
primitive: conclude
agent: Anika
result:  ->
```

3) have -> ingest
4) Ingest subframe:

```text
Action
primitive: ingest
agent: Anika
object: glass of water
```

## State changes


- Use background knowledge to disambiguate between similar sounding statements with different meanings

## Thematic Role Systems

### Analysis

"Ashok made pancakes for David with a griddle."

#### Lexical analysis

- categorize words, noun, verb, etc
  - "Ashok (noun) made (verb) pancakes for David with a griddle."
- noun phrase and verb phrase encompassing multiple words
  - "Ashok(noun phrase) | made pancakes for David with a griddle(verb phrase)"

#### Semantic analysis

- structure of the sentence like action, object, beneficiary and instrument
  - "Ashok(agent) made(verb) pancakes(thematic object) for David(beneficiary) with a griddle(instrument)."
- Frame representation

```text
Thematic Role:
- Verb: make
- Agent: Ashok
- Beneficiary: David
- Thematic Object: Pancakes
- Instrument: Griddle
```

- capture verbs
- Single verbs can be ambiguous

## Leveraging Constraints

### Constraints

Constraints imposed by the language help guide meaning

| Preposition | Thematic Roles            |
|-------------|---------------------------|
|by           |Agent, conveyance, location|
|for          |Beneficiary, duration      |
|from         |Source                     |
|to           |Destination                |
|with         |Coagent, instrument        |

Examples of by:

- "That was written by Ashok" - Agent
- "David went to NY by train" - Conveyance
- "David stood by the statue" - Location

Individual verbs can be ambiguous

!!! 14.09 resolving ambiguity in verbs

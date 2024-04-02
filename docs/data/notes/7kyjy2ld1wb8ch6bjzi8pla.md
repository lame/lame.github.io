
A structured knowledge representation, "the meaning of the meaning"

Think that a frame is a molecule rather than an atom

Cognative processing w/ frames is bottom up (from natural languang to representation)
and top down (from memory to structured representation).

Stereotypes are cognatively efficient, so frames represent stereotypes

## Structure of Frames

A frame is a knowledge structure

```
Ashok ate a frog:

Ate (verb frame)
    Subject: Ashok
    Object: Frog
    Location: Stomach (now)
    Time: past
    Utensils: ?
    Object-Alive: False
    Object-is: in-subject
    Subject-mood: Happy

```

Slots (Subject, Object, etc.) & Fillers (Ashok, Frog, etc.)

Slots on a frame can have a pointer to another frame, for instance the `Subject`
slot above could point to a noun-frame of Ashok. Allows for a discourse level
understanding rather than a sentence level understanding.

```
Ate (verb)
    Subject: -> Ashok

Ashok (noun)
    Title: Professor
    Location: Atlanta, GA
```

## Properties of Frames

- Frames represent stereotypes of the key word for the frame, like `Ate`
- Provides default values
- Takes advantage of inheritance and instances

```
Animal
    num-arms: (default value)
    num-legs: (default value)

Human (type of animal) - Class
    num-arms: 2
    num-legs: 2
    job:
    name:

Human (type of animal) - Instance
    num-arms: 2
    num-legs: 2
    job: Professor
    name: Ashok
```

- Frames can be used to as a structured representation to store a sentence of input, and can be used to generate a sentence of output.

## Representations

Similar to semantic nets, production systems

![Procedural frame](./assets/Procedural_frame.png)

1) Ate gets added to the working memory
2) The slots and default filler values get loaded from semantic memory into working mem

## Story Understanding

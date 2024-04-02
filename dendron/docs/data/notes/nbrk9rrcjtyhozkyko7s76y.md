
$$
\vee, \lor
\wedge
\colon
\oplus
\otimes
\lnot
\forall
\exists
$$

## Formal Notation

- Inference: agent will use knowledge and logic to provide inference
- Soundness: Only valid conclusions can be proven
- Completeness: All valid conclusions can be proven

- Predicate: a function that maps object args to T/F
  - Feathers(bluebird) >>> True

Implication x implies y, $\Rightarrow$

## Conjunctions, Disjunctions, Negations, Implications

### Conjunction

if an animal lays eggs and an animal flies than the animal is a bird

$$
\text{If Lays-eggs(animal)} \wedge \text{Flies(animal)} \Rightarrow \text{Then Bird(animal)}
$$

### Disjunction

if an animal lays eggs or an animal flies than the animal is a bird
$$
\text{Lays-eggs(animal)} \vee \text{Flies(animal)} \Rightarrow \text{Then Bird(animal)}
$$

If an animal flies and is not a bird, it is a bat
$$
\text{Flies(animal)} \wedge \lnot\text{Bird(animal)} \Rightarrow \text{Bat(animal)}
$$


## Truth Tables

- Demorgan's law $\lnot(A\wedge B) == \lnot A \vee \lnot B$
  - The outer not flips the inner operation

Kinda weird logic for "Implies" $\Rightarrow$

|A|B|$A\Rightarrow B$|
|--|--|:-:|
|T|T|T|
|T|F|F|
|F|T|T|
|F|F|T|

$A \Rightarrow B == \lnot A \vee B$

## Rules of Inference

### Modus Ponens

|x|Logic|
|--|--|
|Sentence 1| $P \Rightarrow Q$ |
|Sentence 2| $P$ |
|Sentence 3| $Q$ |

### Modus Tollens

|x|Logic|
|--|--|
|Sentence 1| $P \Rightarrow Q$ |
|Sentence 2| $\lnot Q$ |
|Sentence 3| $\lnot P$ |

## Resolution Theorem Proving

- Prove the opposite of what we're trying to prove
- Start by eliminating the thing you're trying to prove with the contrapositive in the full sentence


## Explanation-based Learning Revisited

Explain why an error led to a failure

- The cup example of explaining what a cup is based on attribtutes.

![cup explanation](./assets/cup_explanation.png)

The agent created an explanation of a cup, but it was incorrect, how does it correct for what made the explanation incorrect?

## Isolating Mistakes

How can the agent isolate the error in it's former model?

- Venn diagram where left circle is characteristics of a positive example
  - Right circle is characteristics of a negative example
  - The right outer join of the venn diagram are "false suspicious features"

In order to attempt to correct, the agent can retry with just false suspicious features to see if that feature is a negative characteristic

Algo for isolating mistakes:

```
To find all suspicious true-success relations:
- Intersect all true success $\bigcap T$
- Union all false successes $\bigcup T$
- Remove assersions in union from intersection $\bigcap T - \bigcup F$

To find all suspicious false-success relations:
- Intersect all false success $\bigcap F$
- Union all true success $\bigcup T$
- Remove all assersions in union from intersection $\bigcap F - \bigcup T$
```

## Explaining Mistakes

How can the agent explain the problem that led to the error?

"Why is the handle being fixed important to an item being a cup?"

Without explaining the mistakes, the agent can't truly learn and create optimal entries in the tree

## Correcting Mistakes

How can the agent repair the model to prevent the error from recurring?

- Errors can be in agent model or agent architecture


- Given a problem, generate potential solutions and test the generated solutions

The loop is:

1) Generate solutions
2) Test generated solutions
3) Prune/merge results to unque set w/ linking to parent/child states
4) Repeat

## Smart Generators

- Creates possible next states
- To make the generator "smart" it should not regenrate any duplicate or previous states, or generate illegal states

## Smart Testers

- Tester enforces problem constraints
- "Smart" testers remove illegal states that have been generated

## Generate and Test in an Unconstrained Domain

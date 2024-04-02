
- If problems are well formed, means-ends analysis and problem reduction can work well
- Weak method (makes little use of knowledge)

## State Spaces

- Initial state and goal state, the path along is a means of solving the problem

## Means-Ends Analysis

- Positive steps reduce the difference between the current state and the goal state, think the `a*` algorithm
- Example of a universal AI method
- No guarantee of optimality, or even being able to solve the problem

## Problem Reduction

- Decompose a hard problem into several smaller, easier problems
- Think about how recurrsive solutions work to solve problems

- In the block stacking example, decompose the final state into a series of "milestones" that are more likely to lead to a successful solution.
- Does not provide guarantees of success

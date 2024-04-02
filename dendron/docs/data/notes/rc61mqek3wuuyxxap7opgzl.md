
## Prompt

Ever since the One Ring was forged by the Dark Lord Sauron, few have been able to resist its seductive power. Gollum was famously corrupted by it, and during his journey to destroy it, even Frodo was tempted by it. One of the few to be able to resist the call of its power was Samwise (Sam) Gamgee.

At one point during their journey to destroy the ring, Frodo, Sam, and Gollum arrive at a river. The river is too wide and deep to swim across, but fortunately, there is a small raft docked on one side. Frodo is too tired from the burden of carrying the ring to drive the raft, however, and Gollum is weak to steer. So, only Sam can steer the raft.

The raft is only large enough for two people at a time; if all three try to ride it, they will sink. So, Sam will have to take Gollum and Frodo across one at a time. However, neither Gollum nor Frodo can be be trusted alone with the One Ring on either side of the river. In fact, neither of them can be trusted alone on the raft with Sam and the ring: its allure is too great, and if given the opportunity, they will simply shove Sam off the side and keep the ring. Therefore, if the either Frodo or Gollum is on the raft with Sam, the ring must be left on one of the riverbanks; if the ring is on the raft, then only Sam can be on the raft with it.

How can Frodo, Sam, Gollum, and the ring get across the river under these conditions? Specifically, neither Frodo nor Gollum can ever be alone with ring on either bank of the river, nor can Frodo or Gollum be on the raft with the ring. If the ring is on the raft, then only Sam can be on the raft with it. Obviously, Sam is also permitted to steer the raft alone. (It is okay, however, for the ring, Sam, and Frodo or Gollum to be on one bank of the river together, so long as on the next move, Sam departs with either the ring or Frodo/Gollum).

First, construct a semantic network representing this problem. This should take approximately half a page, including a figure of two states with a transition between them. Make sure to include all components of the state, and an operator indicating how we transition from one state to another.

Second, apply generate & test to this semantic network in order to solve the problem. In applying generate & test, your generator should be smart enough to only make valid moves (e.g. it will not try to move Gollum and the ring together at once, or make consecutive moves in the same direction across the river without Sam bringing the raft back), but it should not be smart enough to only make moves that result in valid states (e.g. it should still try to move Frodo first, even though that move results in an invalid state, specifically Gollum alone with the ring). Your tester, in turn, should check each generated state to see if (a) it follows the rules, and (b) if it has met the goal. You may decide whether identifying states that have already been visited is the responsibility of the generator or the tester.

Include the entire semantic network that solves this problem. Clearly indicate which states are failed, and why. The semantic network should explore the entire problem space: every state should be either ruled out or have its following states explored. We expect this will fit on one page: you may create a more space-efficient representation if need be. As long as it is legible, you may also hand-write the network and insert it as an image into your paper.

## Semantic Net

Objects:

- Ring
- Sam
- Frodo
- Gollum
- Boat
- Left Shore
- Right Shore
- River

Actions:

- Transition Right
- Transition Left

Working Sequence:

```
(FGSR) L ------------ R
(FG)   L --- SR ->--- R
(FG)   L ----<- S---- R (Ring)
(G)    L ----SF ->--- R (Ring)
(G)    L ----<- SR--- R (Frodo)
(Ring) L ----SG ->--- R (Frodo)
(Ring) L ----<- S---- R (FG)
()     L ----SR ->--- R (FG)
()     L ------------ R (SRGF)
```

- Generate & Test

The generator will only propose states where Samwise is traveling back and forth for
brevity as there are no possible states that can exist given the rules if Sam is not in
the boat.

---
id: 25p8qmdgwcyhgibqvorq9uw
title: Version_Spaces
desc: ''
updated: 1711376378992
created: 1703613593218
---

## Algorithm for Version spaces

1) Begin with two models, the most specialized and the most general model possible.
2) If the example is a positive example, generalize the specalized model to include the positive example and prune away from the general model that cannot include it
3) If the example is a negative example, specialize the general model to exclude the negative example, prune away from the specific models that do not exclude it
4) Prune away any version spaces subsumed by earlier version spaces

## Tree-Based Representations

- Decision trees create more optimal trees, but require all the examples up-front
- Discrimination trees create less optimal trees, but can learn incrementally

> Mirror of [iceanimations/bakeInstancer](https://github.com/iceanimations/bakeInstancer), published by
> the studio under EPL 2.0. Kept here for reference; the original repository is the canonical one.

# bakeInstancer

Bakes a Maya particle instancer into plain transforms, so the instances survive a round trip through a
renderer or a format that has no idea what an instancer is.

The instancer node is efficient and, in the middle of a pipeline, unreliable: it can be dropped by an
export, ignored by a farm node running a different plugin set, or lost when the scene goes through a
format that only knows transforms. Baking it out to real transforms costs memory and buys certainty.

## What it does

`src/bake_particle_instancer.py` walks the instance data through `OpenMayaFX`, samples at fractional
frame steps rather than whole frames, and rebuilds the instances as a transform hierarchy. The file
opens with its own task list, which is a fair description of where it stopped:

```
** DONE bake at floating point frame steps
** TODO bake more than one instancer at a time
** TODO separate gather and create /passes/
** TODO make a class structure of the baking script
** TODO check possibilities of optimizing
** TODO make GUI
```

`src/window.py` is the small Qt front end that did get built.

## Authorship

22 commits between 2013 and 2021:

| Author | Commits |
|---|---|
| Qurban Ali | 16 |
| Talha Ahmed | 6 |

Qurban Ali wrote this one on my team. Mirrored as part of the toolbox, not as an example of my code.

LICENSE
=======

Copyright 2021. Talha Ahmed. All rights reserved.

This work is licensed under the terms of Eclipse Public License - v 2.0.
For a copy see https://www.eclipse.org/org/documents/epl-2.0/EPL-2.0.txt

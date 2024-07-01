---
layout: post
title: Ren'Py reposition image
date: 2024-07-01 18:56:25
excerpt: How to reposition an image in Ren'Py using a transform statement.
categories: renpy transform image
---

This post goes over how to reposition an image in [Ren'Py](https://www.renpy.org/) using a [transform statement](https://www.renpy.org/doc/html/atl.html).

## ypos

Transform to reposition an image on the y-axis:

```py
transform ypos(position):
    ypos position
```

For example, move a sprite down in `game/script.rpy`:

```rpy
show eileen at ypos(1.25), center
```

See [ypos](https://www.renpy.org/doc/html/style_properties.html#style-property-ypos) for more details.

## xpos

Transform to reposition an image on the y-axis:

```py
transform xpos(position):
    xpos position
```

For example, move a sprite to the center in `game/script.rpy`:

```rpy
show eileen at xpos(0.5)
```

See [xpos](https://www.renpy.org/doc/html/style_properties.html#style-property-xpos) for more details.

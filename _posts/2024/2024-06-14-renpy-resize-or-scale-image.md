---
layout: post
title: Ren'Py resize or scale image
date: 2024-06-14 14:10:16
excerpt: How to resize or scale an image in Ren'Py using a transform statement.
categories: renpy transform image
---

This post goes over how to resize or scale an image in [Ren'Py](https://www.renpy.org/) using a [transform statement](https://www.renpy.org/doc/html/atl.html).

## Half Size

Transform to make an image 50% smaller:

```py
transform halfsize():
    zoom 0.5
```

Use in `game/script.rpy`:

```rpy
show eileen at halfsize, center
```

## Transform

Transform to resize an image:

```py
transform scale(ratio):
    zoom ratio
```

Use in `game/script.rpy`:

```rpy
show eileen at scale(0.5), center
```

---
layout: post
title: Ren'Py color opacity
date: 2026-09-21 21:02:06
excerpt: How to set Ren'Py color opacity.
categories: renpy color alpha opacity
---

Normally, you can set text opacity in Ren'Py with the `alpha` text tag:

```rpy
"Normal text, {alpha=0.5}half-transparent text{/alpha}."
```

To set the opacity as part of a color, use an eight-digit hexadecimal color in `#rrggbbaa` format.

The first six digits specify the red, green, and blue values; the final two digits specify the alpha channel.

For example, `80` sets the color's alpha to approximately 50% opacity:

```rpy
define e = Character("Eileen", color="#ffffff80")
```

The alpha value ranges from `00` (fully transparent) to `ff` (fully opaque).

Here are the hexadecimal alpha values at 5% increments:

| Opacity | Hex alpha | Example |
| --- | --- | --- |
| 0% | `00` | `#ffffff00` |
| 5% | `0d` | `#ffffff0d` |
| 10% | `1a` | `#ffffff1a` |
| 15% | `26` | `#ffffff26` |
| 20% | `33` | `#ffffff33` |
| 25% | `40` | `#ffffff40` |
| 30% | `4d` | `#ffffff4d` |
| 35% | `59` | `#ffffff59` |
| 40% | `66` | `#ffffff66` |
| 45% | `73` | `#ffffff73` |
| 50% | `80` | `#ffffff80` |
| 55% | `8c` | `#ffffff8c` |
| 60% | `99` | `#ffffff99` |
| 65% | `a6` | `#ffffffa6` |
| 70% | `b3` | `#ffffffb3` |
| 75% | `bf` | `#ffffffbf` |
| 80% | `cc` | `#ffffffcc` |
| 85% | `d9` | `#ffffffd9` |
| 90% | `e6` | `#ffffffe6` |
| 95% | `f2` | `#fffffff2` |
| 100% | `ff` | `#ffffffff` |

---
layout: post
title: How to hide save in Ren'Py
date: 2026-09-06 19:13:47
excerpt: How to [hide the Save menu](/posts/renpy-hide-save) in Ren'Py.
categories: renpy
---

Sometimes you may want to hide the **Save** menu in a Ren'Py game—for example, in a game where choices are final.

## Quick Menu

To hide the menu at the bottom of the screen, open `game/screens.rpy` and change the default value of `quick_menu`:

```diff
-default quick_menu = True
+default quick_menu = False
```

Alternatively, you can hide it from your script after the game starts:

```rpy
label start:
    $ quick_menu = False
```

## Navigation Screen

Open `game/screens.rpy` and find the `navigation` screen. Comment out or remove the **Save** button:

```rpy
textbutton _("Save") action ShowMenu("save")
```

If you also want to hide loading, remove the `Load` button:

```rpy
textbutton _("Load") action ShowMenu("load")
```

Removing these buttons only removes them from that navigation screen. Other code could still open the screens directly with `ShowMenu("save")` or `ShowMenu("load")`.

## Game Menu

By default, pressing **Esc** or right-clicking opens the **Save** screen.

To open another screen instead, set `config.game_menu_action` in `game/options.rpy`:

```rpy
define config.game_menu_action = ShowMenu("preferences")
```

This example opens the **Preferences** screen when the player presses **Esc** or right-clicks.

You can replace `preferences` with another game-menu screen. In `game/screens.rpy`, search for `tag menu` to find the available screens:

- `about`
- `preferences`
- `history`
- `help`
- `save`
- `load`

These changes hide the usual ways to access saving, but they do not disable saving completely if another part of the game calls the save screen or save functions directly.

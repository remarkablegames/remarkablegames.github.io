---
layout: post
title: Ren'Py main menu title
date: 2024-09-17 19:55:03
excerpt: How to change and style the main menu title in Ren'Py.
categories: renpy title
---

This post goes over how to change and style the main menu title in [Ren'Py](https://www.renpy.org/).

## Name

Open `game/options.rpy` and edit `config.name`:

```py
## A human-readable name of the game. This is used to set the default window
## title, and shows up in the interface and error reports.
##
## The _() surrounding the string marks it as eligible for translation.

define config.name = _("Main Menu Title")
```

Replace `Main Menu Title` with your title.

## Size

Open `game/gui.rpy` and edit `gui.title_text_size`:

```py
## The size of the game's title.
define gui.title_text_size = 75
```

Replace `75` with your text size in pixels.

## Color

Open `game/screens.rpy` and update style `main_menu_title`:

```py
style main_menu_title:
    properties gui.text_properties("title")
    color "#f00"
```

Replace `#f00` with your hexadecimal color.

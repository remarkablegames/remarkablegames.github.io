---
layout: post
title: Ren'Py sorting minigame
date: 2025-10-26 14:56:35
excerpt: How to create a Ren'Py sorting minigame.
categories: renpy sorting minigame python
image: /assets/images/2025/2025-10-26-renpy-sorting-minigame.png
---

This post goes over how to create a sorting minigame in [Ren'Py](https://www.renpy.org/).

![Ren'Py Sorting Game](/assets/images/2025/2025-10-26-renpy-sorting-minigame.png)

> The image is from the game [KnitBone]({% post_url 2025/2025-09-30-knitbone %}).

## Class

Create the Python class:

```py
init python:
    class Sorting:
        def __init__(self):
            self.moves = 0
            self.values = []

        def jump(self):
            renpy.jump("sorting_minigame")

        def start(self, moves: int, items: int, win: str, lose: str):
            self.moves = moves
            self.values = []
            self.win = win
            self.lose = lose

            while self.values == sorted(self.values):
                # TODO: change this logic if you don't want your items to be randomized
                self.values = renpy.random.sample(list(range(1, items + 1)), items)

            self.jump()

        def won(self):
            return self.values == sorted(self.values)

        def lost(self):
            return not self.moves

        def ondrag(self, drags, drop):
            drag = drags[0]
            [drag_index, drag_value] = self.parse_drag_name(drag.drag_name)

            if not drop:
                drag.snap(**self.get_snap(drag_index))
                return

            [drop_index, drop_value] = self.parse_drag_name(drop.drag_name)

            drag.snap(**self.get_snap(drop_index))
            drop.snap(**self.get_snap(drag_index))

            drag.drag_name = self.stringify_drag_name(drop_index, drag_value)
            drop.drag_name = self.stringify_drag_name(drag_index, drop_value)

            self.values[drag_index - 1] = drop_value
            self.values[drop_index - 1] = drag_value

            self.moves -= 1
            # TODO: replace or remove audio
            renpy.sound.queue("drop.ogg", relative_volume=1.0)
            self.jump()

        def get_snap(self, index: int):
            return {
                "x": (index - 1) / len(self.values),
                "y": 0.5,
                "delay": 0.2,
            }

        def stringify_drag_name(self, index: int, value: int):
            return f"{index},{value}"

        def parse_drag_name(self, name: str):
            [index, value] = name.split(",")
            return [int(index), int(value)]
```

And initialize it:

```py
default sorting = Sorting()
```

## Screen

Create the screen:

```py
screen sorting_minigame():
    frame:
        background Solid((0, 0, 0, 100))
        text "{color=#ccc}Remaining Moves: [sorting.moves]"
        xpos 30
        ypos 30

    draggroup:
        for index, value in enumerate(sorting.values, start=1):
            drag:
                # TODO: add your images to `game/images/` folder and
                # use one-based numbering (e.g., `item 1.png` and `item 1 hover.png`)
                child f"item {value}.png"
                hover_child f"item {value} hover.png"
                selected_child f"item {value} hover.png"
                drag_name sorting.stringify_drag_name(index, value)
                draggable not(sorting.won() or sorting.lost())
                dragged sorting.ondrag
                droppable True
                xpos sorting.get_snap(index)["x"]
                ypos sorting.get_snap(index)["y"]
                # TODO: replace or remove audio
                hovered [Queue("sound", "hovered.ogg")]
```

## Label

Create a label that calls the screen:

```py
label sorting_minigame:
    if sorting.won():
        show screen sorting_minigame
        "You won!"
        hide screen sorting_minigame
        jump expression sorting.win
    elif sorting.lost():
        show screen sorting_minigame
        "You lost..."
        hide screen sorting_minigame
        jump expression sorting.lose

    call screen sorting_minigame
```

## Usage

Start the slider minigame:

```py
# game/script.rpy
label start:
    $ sorting.start(moves=4, items=6, win="my_win_label", lose="my_lose_label")
```

To disable user rollback (the `Back` button), add this to `script.rpy`:

```py
define config.rollback_enabled = False
```

## Script

See the full script `sorting.rpy`:

```py
# game/sorting.rpy
default sorting = Sorting()

init python:
    class Sorting:
        def __init__(self):
            self.moves = 0
            self.values = []

        def jump(self):
            renpy.jump("sorting_minigame")

        def start(self, moves: int, items: int, win: str, lose: str):
            self.moves = moves
            self.values = []
            self.win = win
            self.lose = lose

            while self.values == sorted(self.values):
                # TODO: change this logic if you don't want your items to be randomized
                self.values = renpy.random.sample(list(range(1, items + 1)), items)

            self.jump()

        def won(self):
            return self.values == sorted(self.values)

        def lost(self):
            return not self.moves

        def ondrag(self, drags, drop):
            drag = drags[0]
            [drag_index, drag_value] = self.parse_drag_name(drag.drag_name)

            if not drop:
                drag.snap(**self.get_snap(drag_index))
                return

            [drop_index, drop_value] = self.parse_drag_name(drop.drag_name)

            drag.snap(**self.get_snap(drop_index))
            drop.snap(**self.get_snap(drag_index))

            drag.drag_name = self.stringify_drag_name(drop_index, drag_value)
            drop.drag_name = self.stringify_drag_name(drag_index, drop_value)

            self.values[drag_index - 1] = drop_value
            self.values[drop_index - 1] = drag_value

            self.moves -= 1
            # TODO: replace or remove audio
            renpy.sound.queue("drop.ogg", relative_volume=1.0)
            self.jump()

        def get_snap(self, index: int):
            return {
                "x": (index - 1) / len(self.values),
                "y": 0.5,
                "delay": 0.2,
            }

        def stringify_drag_name(self, index: int, value: int):
            return f"{index},{value}"

        def parse_drag_name(self, name: str):
            [index, value] = name.split(",")
            return [int(index), int(value)]

screen sorting_minigame():
    frame:
        background Solid((0, 0, 0, 100))
        text "{color=#ccc}Remaining Moves: [sorting.moves]"
        xpos 30
        ypos 30

    draggroup:
        for index, value in enumerate(sorting.values, start=1):
            drag:
                # TODO: add your images to `game/images/` folder and
                # use one-based numbering (e.g., `item 1.png` and `item 1 hover.png`)
                child f"item {value}.png"
                hover_child f"item {value} hover.png"
                selected_child f"item {value} hover.png"
                drag_name sorting.stringify_drag_name(index, value)
                draggable not(sorting.won() or sorting.lost())
                dragged sorting.ondrag
                droppable True
                xpos sorting.get_snap(index)["x"]
                ypos sorting.get_snap(index)["y"]
                # TODO: replace or remove audio
                hovered [Queue("sound", "hovered.ogg")]

label sorting_minigame:
    if sorting.won():
        show screen sorting_minigame
        "You won!"
        hide screen sorting_minigame
        jump expression sorting.win
    elif sorting.lost():
        show screen sorting_minigame
        "You lost..."
        hide screen sorting_minigame
        jump expression sorting.lose

    call screen sorting_minigame
```

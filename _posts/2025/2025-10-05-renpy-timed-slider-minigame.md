---
layout: post
title: Ren'Py timed slider minigame
date: 2025-10-05 20:42:24
updated: 2025-10-17 19:46:36
excerpt: How to create a timed slider minigame in Ren'Py.
categories: renpy slider minigame python
---

This post goes over how to create a timed slider minigame in [Ren'Py](https://www.renpy.org/).

## Class

Create a Python class for the slider:

```py
init python:
    class Slider:
        WIDTH = 100
        WIDTH_MAX = 1000
        PADDING = 10

        def start(self, speed, jump_win, jump_lose):
            self.xsize = self.WIDTH
            self.xsize_max = self.WIDTH_MAX
            self.xpos_target = renpy.random.randint(0, self.WIDTH_MAX - self.WIDTH - self.PADDING)
            self.speed = speed
            self.xpos_current = 0
            self.direction = 1
            self.jump_win = jump_win
            self.jump_lose = jump_lose
            renpy.jump("slider")

        def update(self):
            if self.xpos_current <= 0:
                self.direction = 1
            elif self.xpos_current + self.xsize >= self.xsize_max - self.PADDING:
                self.direction = -1
            self.xpos_current += self.speed * self.direction

        def stop(self):
            xpos_current = self.xpos_current
            xpos_target = self.xpos_target
            xsize = self.xsize

            has_collided = (
                # left intersection
                (xpos_current >= xpos_target and xpos_current <= xpos_target + xsize) or
                # right intersection
                (xpos_current + xsize >= xpos_target and xpos_current + xsize <= xpos_target + xsize)
            )

            if has_collided:
                renpy.jump(self.jump_win)
            else:
                renpy.jump(self.jump_lose)
```

And initialize it:

```py
default slider = Slider()
```

_Optional:_ If you want the target to be at the center:

```diff
-self.xpos_target = renpy.random.randint(0, self.WIDTH_MAX - self.WIDTH - self.PADDING)
+self.xpos_target = (self.WIDTH_MAX - self.WIDTH - self.PADDING) // 2
```

## Screen

Create a screen for the slider:

```py
screen slider():
    timer 0.001:
        repeat True
        action Function(slider.update)

    button:
        action Function(slider.stop)
        xalign 0.5
        yalign 0.5

        frame:
            background "#00000099"
            xsize slider.xsize_max
            ysize 50

            bar:
                right_bar Solid((255, 255, 255, 100))
                xsize slider.xsize
                xpos slider.xpos_target

            bar:
                value 1
                xsize slider.xsize
                xpos slider.xpos_current

    textbutton "Stop":
        action Function(slider.stop)
        xalign 0.5
        yalign 0.65
```

## Label

Create a label that calls the slider screen:

```py
label slider:
    call screen slider
```

## Usage

Start the slider minigame:

```py
# game/script.rpy
label start:
    $ slider.start(speed=10, jump_win="win_label", jump_lose="lose_label")
```

## Script

See the full script `slider.rpy`:

```py
# game/slider.rpy
default slider = Slider()

init python:
    class Slider:
        WIDTH = 100
        WIDTH_MAX = 1000
        PADDING = 10

        def start(self, speed, jump_win, jump_lose):
            self.xsize = self.WIDTH
            self.xsize_max = self.WIDTH_MAX
            self.xpos_target = renpy.random.randint(0, self.WIDTH_MAX - self.WIDTH - self.PADDING)
            self.speed = speed
            self.xpos_current = 0
            self.direction = 1
            self.jump_win = jump_win
            self.jump_lose = jump_lose
            renpy.jump("slider")

        def update(self):
            if self.xpos_current <= 0:
                self.direction = 1
            elif self.xpos_current + self.xsize >= self.xsize_max - self.PADDING:
                self.direction = -1
            self.xpos_current += self.speed * self.direction

        def stop(self):
            xpos_current = self.xpos_current
            xpos_target = self.xpos_target
            xsize = self.xsize

            has_collided = (
                # left intersection
                (xpos_current >= xpos_target and xpos_current <= xpos_target + xsize) or
                # right intersection
                (xpos_current + xsize >= xpos_target and xpos_current + xsize <= xpos_target + xsize)
            )

            if has_collided:
                renpy.jump(self.jump_win)
            else:
                renpy.jump(self.jump_lose)

screen slider():
    timer 0.001:
        repeat True
        action Function(slider.update)

    button:
        action Function(slider.stop)
        xalign 0.5
        yalign 0.5

        frame:
            background "#00000099"
            xsize slider.xsize_max
            ysize 50

            bar:
                right_bar Solid((255, 255, 255, 100))
                xsize slider.xsize
                xpos slider.xpos_target

            bar:
                value 1
                xsize slider.xsize
                xpos slider.xpos_current

    textbutton "Stop":
        action Function(slider.stop)
        xalign 0.5
        yalign 0.65

label slider:
    call screen slider
```

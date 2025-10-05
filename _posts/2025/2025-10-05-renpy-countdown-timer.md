---
layout: post
title: Ren'Py countdown timer
date: 2025-10-05 17:32:37
excerpt: How to create a countdown timer in Ren'Py.
categories: renpy countdown timer python
---

This post goes over how to create a countdown timer in [Ren'Py](https://www.renpy.org/).

## Class

Create a Python class for the countdown timer:

```py
init python:
    class Countdown:
        DECREMENT = 0.01
        SCREEN = "countdown"

        def start(self, seconds, jump):
            self.current = seconds
            self.length = seconds
            self.jump = jump
            renpy.show_screen(self.SCREEN)

        def cancel(self):
            renpy.hide_screen(self.SCREEN)

        def decrement(self):
            self.current -= self.DECREMENT

        def end(self):
            self.cancel()
            renpy.jump(self.jump)
```

And initialize it:

```py
default countdown = Countdown()
```

## Screen

Create a screen for the countdown timer:

```py
screen countdown():
    timer countdown.DECREMENT:
        repeat True
        action If(
            countdown.current > 0,
            true=Function(countdown.decrement),
            false=Function(countdown.end),
        )

    bar value AnimatedValue(countdown.current, countdown.length):
        xalign 0.5
        yalign 0.6
        xmaximum 300
```

## Usage

Use the countdown timer for [quick time events (QTE)](https://wikipedia.org/wiki/Quick_time_event):

```py
# game/script.rpy
label start:
    $ countdown.start(seconds=3, jump="end")
    menu:
        "Choice 1":
            $ countdown.cancel()
            jump choice1
        "Choice 2":
            $ countdown.cancel()
            jump choice2
```

## Script

See the full script `countdown.rpy`:

```py
# game/countdown.rpy
default countdown = Countdown()

init python:
    class Countdown:
        DECREMENT = 0.01
        SCREEN = "countdown"

        def start(self, seconds, jump):
            self.current = seconds
            self.length = seconds
            self.jump = jump
            renpy.show_screen(self.SCREEN)

        def cancel(self):
            renpy.hide_screen(self.SCREEN)

        def decrement(self):
            self.current -= self.DECREMENT

        def end(self):
            self.cancel()
            renpy.jump(self.jump)

screen countdown():
    timer countdown.DECREMENT:
        repeat True
        action If(
            countdown.current > 0,
            true=Function(countdown.decrement),
            false=Function(countdown.end),
        )

    bar value AnimatedValue(countdown.current, countdown.length):
        xalign 0.5
        yalign 0.6
        xmaximum 300
```

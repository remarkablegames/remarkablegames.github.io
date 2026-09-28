---
layout: post
title: How to play voice bleeps in a Ren'Py game
date: 2026-09-28 14:14:04
excerpt: How to play voice bleeps in a Ren'Py visual novel game.
categories: renpy voice bleep python audio
---

This tutorial shows how to play a looping voice bleep while Ren'Py reveals dialogue text.

## Add the bleep sound

Add a [bleep](https://dmochas-assets.itch.io/dmochas-bleeps-pack) audio file in your game directory. For example:

```
game/audio/bleep.ogg
```

## Create a dedicated audio channel

Register a custom channel in your `.rpy` script:

```python
# game/script.rpy
init python:
    BLEEP_CHANNEL = "bleep"
    renpy.music.register_channel(BLEEP_CHANNEL, mixer="voice", loop=True)
```

Setting the `voice` mixer means the bleep follows the game's voice-volume setting.

Enabling `loop` makes the sound repeat until the channel is stopped.

Using a separate channel is useful because the bleep will not interfere with background music, sound effects, or actual voice clips.

## Create the dialogue callback

Add a callback function:

```python
def voice_callback(event, **kwargs):
    if event == "show_done":
        renpy.music.play("audio/bleep.ogg", channel=BLEEP_CHANNEL)
    elif event in ("slow_done", "end"):
        renpy.music.stop(channel=BLEEP_CHANNEL, fadeout=0.2)
```

The callback receives events from the dialogue system:

- `show_done` starts the looping bleep.
- `slow_done` stops it after the text has finished appearing.
- `end` stops the bleep if the dialogue interaction ends (skipped/interrupted).

The `fadeout` gives the sound a smooth fade instead of cutting it off abruptly.

## Attach the callback to a character

Define a character using the callback:

```rpy
define e = Character("Eileen", callback=voice_callback)
```

Now your bleep should play:

```rpy
label start:
    e "This dialogue uses a looping bleep while the text appears."
    e "The bleep stops when the line is complete."
    return
```

## Play a sound when dialogue is dismissed

Optionally, you can play a sound when the dialogue is dismissed:

```python
def dismiss_callback():
    renpy.sound.play("audio/click.ogg")
    return True

config.say_allow_dismiss = dismiss_callback
```

## Script

Here's the full script:

```python
# game/script.rpy
init python:
    BLEEP_CHANNEL = "bleep"
    renpy.music.register_channel(BLEEP_CHANNEL, mixer="voice", loop=True)

    def voice_callback(event, **kwargs):
        if event == "show_done":
            renpy.music.play("audio/bleep.ogg", channel=BLEEP_CHANNEL)
        elif event in ("slow_done", "end"):
            renpy.music.stop(channel=BLEEP_CHANNEL, fadeout=0.2)

    def dismiss_callback():
        renpy.sound.play("audio/click.ogg")
        return True

    config.say_allow_dismiss = dismiss_callback

define e = Character("Eileen", callback=voice_callback)
```

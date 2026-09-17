---
layout: post
title: Ren'Py gallery image with password unlock
date: 2026-09-16 23:15:23
excerpt: How to [unlock a Ren'Py gallery image with a password](/posts/renpy-gallery-image-with-password-unlock).
categories: renpy gallery python
---

Sometimes you want to keep a gallery image locked until the player enters a password. Unlike the normal gallery flow where an image unlocks the moment it's seen in-game, you can gate a single button behind a password while the rest of the gallery stays open.

## Persistent Flag

Start by defining a persistent flag that controls the lock:

```py
default persistent.unlock_gallery_image_with_password = False
```

## Password Prompt

Next, add a function that prompts for the password:

```py
init python:
    def unlock_gallery_image_with_password():
        entered = renpy.invoke_in_new_context(
            renpy.input,
            "Enter the password to unlock the image:",
            mask="*",
        )

        if entered == "password":
            persistent.unlock_gallery_image_with_password = True
            renpy.save_persistent()
            renpy.restart_interaction()
        else:
            renpy.notify("Incorrect password.")
```

The `renpy.invoke_in_new_context` call runs `renpy.input` in a new context, which lets the prompt appear while the gallery is still on screen.

If you try to call `renpy.input()` directly from the button's `Function` action, it throws the exception:

```
Cannot start an interaction in the middle of an interaction, without creating a new context.
```

The optional `mask="*"` argument hides what the player types, so the password stays hidden.

When the password is correct, `persistent.unlock_gallery_image_with_password` is enabled and saved.

Calling `renpy.restart_interaction()` redraws the gallery so the gated button becomes unlocked immediately.

## Gallery Button

In the gallery configuration script, gate the button with a condition:

```py
g = Gallery()

g.button("sylvie_green")
g.condition("persistent.unlock_gallery_image_with_password")
g.image("bg lecturehall", "sylvie green normal")
g.image("bg lecturehall", "sylvie green smile")
```

The `g.condition` keeps the button locked until `persistent.unlock_gallery_image_with_password` is `True`.

Use `g.image` instead of `g.unlock_image` since the former doesn't require the image to have been seen in-game to unlock.

## Unlock Button

Finally, add an unlock button to the gallery screen in `game/screens.rpy`:

```py
if not persistent.unlock_gallery_image_with_password:
    textbutton _("Unlock with password"):
        action Function(unlock_gallery_image_with_password)
```

See the [code example](https://github.com/remarkablegames/renpy-gallery).

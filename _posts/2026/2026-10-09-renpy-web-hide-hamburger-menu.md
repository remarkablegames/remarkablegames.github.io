---
layout: post
title: Hide Ren'Py web hamburger menu
date: 2026-10-09 13:09:00
excerpt: How to hide the Ren'Py hamburger menu for the web game.
categories: renpy web hamburger menu
---

This post explains how to hide the [hamburger menu](https://www.renpy.org/doc/html/web.html#hamburger-menu) that appears in the top-left corner of a [Ren'Py](https://www.renpy.org/) web game.

## CSS

If you created your web build with the Ren'Py Launcher, you can hide the menu by adding a CSS rule to the web build's `index.html`:

```html
<style>
  #ContextContainer {
    display: none;
  }
</style>
```

You can also use `sed` to update the rule:

```sh
sed -i 's|#ContextContainer {|#ContextContainer { display: none;|' web/index.html
```

> Make sure to replace `web` with your web build destination.

On macOS, use:

```sh
sed -i '' 's|#ContextContainer {|#ContextContainer { display: none;|' web/index.html
```

## JavaScript

To hide the menu from `game/script.rpy`, run this JavaScript code:

```python
label start:
    if renpy.emscripten:
        $ renpy.emscripten.run_script(
            "document.getElementById('ContextContainer').style.display = 'none'"
        )
```

[renpy.emscripten](https://www.renpy.org/doc/html/web.html#javascript) checks whether the game is running in a web build. [renpy.emscripten.run_script](https://www.renpy.org/doc/html/web.html#renpy.emscripten.run_script) executes the JavaScript that hides the menu.

See [example](https://github.com/remarkablegames/renpy-examples/blob/master/game/scripts/javascript.rpy).

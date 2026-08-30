---
layout: post
title: How I added mobile support to a desktop game
date: 2026-08-29 21:49:00
excerpt: 🔚 [Deus Ex Machina](/posts/deus-ex-machina-mobile-support) is now playable on mobile with a touch toolbar and pinch-to-zoom.
categories: mobile phaser platformer puzzle typescript game
image: /assets/images/2026/2026-08-29-how-to-add-mobile-support-to-desktop-game.png
---

I just shipped mobile support for [Deus Ex Machina](https://remarkablegames.org/deus-ex-machina/), a puzzle-platformer where you draw arrows to guide a robot through industrial levels. You can now play it on a phone or tablet.

- [Wavedash](https://wavedash.com/games/deus-ex-machina)
- [itch.io](https://remarkablegames.itch.io/deus-ex-machina)
- [remarkablegames](https://remarkablegames.org/deus-ex-machina/)

![Deus Ex Machina mobile gameplay](/assets/images/2026/2026-08-29-how-to-add-mobile-support-to-desktop-game.png)

## The Problem

**Deus Ex Machina** was built for desktop:

- left-click to place an arrow,
- left-click again to rotate it,
- right-click to erase, and
- `R` to restart.

On a touch device, none of those inputs exist, so I needed a way to add touch controls without breaking the desktop experience.

## Touch Toolbar

The biggest change is the new `MobileToolbar` component. It only renders when `isMobile()` detects a touch device:

```ts
export function isMobile(): boolean {
  return (
    'ontouchstart' in window ||
    navigator.maxTouchPoints > 0 ||
    window.matchMedia('(pointer: coarse)').matches
  );
}
```

The toolbar has 6 buttons:

1. Pan
2. Place
3. Rotate
4. Erase
5. Clear
6. Restart

**Pan** lets you drag the camera; **Place**, **Rotate**, and **Erase** switch the editor's mode; **Clear** resets the arrows; and **Restart** reloads the current level while preserving any tiles you've drawn.

Because the toolbar can block level elements, I added a `≡` drag handle so players can move it anywhere inside the camera view.

A few things I learned while building the drag handle:

- Call `setInteractive()` before `setDraggable()` or the Phaser input system will throw.
- Clamp the toolbar inside `cameras.main.worldView` so it never drags off-screen.

## Camera Gestures

On mobile, the camera responds to touch directly:

- One finger in **Pan** mode moves the camera.
- One tap with minimal movement performs the selected tile action.
- Two fingers pinch to zoom in and out, with zoom clamped between a fit-to-screen minimum and a maximum of `3x`.

## Orientation and UI

The manifest now uses `landscape-primary`, and the game tries to lock the screen to landscape on supported devices. I also updated the level hints so they show a consistent message for each platform.

If you're making a web game with Phaser, the main takeaway is to keep the desktop and mobile control paths separate when the controls are different. React-style state from `phaser-jsx` makes the UI easy to manage, but for a drag handle you'll want to touch the Phaser GameObject directly to avoid re-render surprises.

Give it a try on your phone and let me know how it feels!

- [Wavedash](https://wavedash.com/games/deus-ex-machina)
- [itch.io](https://remarkablegames.itch.io/deus-ex-machina)
- [remarkablegames](https://remarkablegames.org/deus-ex-machina/)

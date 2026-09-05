---
layout: post
title: Kaplay responsive options
date: 2026-09-05 15:00:59
excerpt: Understanding [responsive options in Kaplay.js](/posts/kaplay-responsive-options).
categories: kaplay javascript game-development web
---

When building a web game with [Kaplay.js](https://kaplayjs.com/), you need to decide how the game should look when the window, canvas, or device screen size changes.

Kaplay provides options such as `width`, `height`, `stretch`, and `letterbox` to control this behavior. Understanding how they work together helps you create games that scale properly without distorted graphics or broken layouts.

## Default setup

A basic Kaplay game can be initialized without specifying a resolution:

```ts
import kaplay from "kaplay";

kaplay();
```

When `width` and `height` are omitted, Kaplay uses the canvas dimensions as the game's coordinate dimensions.

This works well when the canvas has a stable size, such as when the game is embedded in an iframe with fixed dimensions. However, if the canvas size changes, objects don't automatically reposition themselves.

## Fixed resolution

For many games, it's useful to define a fixed internal resolution:

```ts
kaplay({
  width: 640,
  height: 360,
});
```

This creates a fixed 640×360 coordinate system with a 16:9 aspect ratio. Your game logic and object positions are based on those dimensions, regardless of how large the game appears in the browser.

A fixed resolution is useful when:

- Your game uses pixel art.
- You want predictable object positions.
- You're designing for a specific aspect ratio.
- You want the same game layout on different screens.

## Option `stretch`

The `stretch` option scales the game to use the available canvas area:

```ts
kaplay({
  width: 640,
  height: 360,
  stretch: true,
});
```

The game still uses a 640×360 coordinate system, but that game view is enlarged or reduced to fit the canvas.

However, if the display has a different aspect ratio, stretching can distort the game. Circles may appear elliptical, and sprites may become wider or taller than intended.

Use `stretch` when filling the available space is more important than preserving the exact shape of the game.

## Option `letterbox`

The `letterbox` option preserves the game’s aspect ratio while allowing it to scale:

```ts
kaplay({
  width: 640,
  height: 360,
  stretch: true,
  letterbox: true,
});
```

Kaplay scales the game as large as possible without distorting it. Any unused space is filled with bars.

Depending on the difference in aspect ratios, the bars may appear:

- On the left and right sides.
- Above and below the game.

For example, a 16:9 game shown in a 4:3 area will have bars above and below because the available area is relatively taller.

The important distinction is:

- `stretch: true` fills the available area but may distort the game.
- `letterbox: true` preserves the aspect ratio by allowing unused space.
- Use both options when you want a fixed internal resolution that scales to the available canvas without changing the game's aspect ratio.

## Option `scale`

The `scale` option changes the scale factor used when rendering the game:

```ts
kaplay({
  width: 640,
  height: 360,
  stretch: true,
  letterbox: true,
  scale: 2,
});
```

This may help improve the appearance of low-resolution graphics when the game is rendered at a larger size. However, increasing scale does not add detail to sprites or improve the quality of the source images. It can also increase rendering and memory costs.

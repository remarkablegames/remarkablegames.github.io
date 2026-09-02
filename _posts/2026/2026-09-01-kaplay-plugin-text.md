---
layout: post
title: Kaplay Plugin Text
date: 2026-09-01 21:38:02
excerpt: 🦖 How to render styled text in Kaplay.js games with [kaplay-plugin-text](/posts/kaplay-plugin-text).
categories: kaplay plugin styled text canvas
---

[Kaplay Plugin Text](https://github.com/remarkablegames/kaplay-plugin-text) allows you to render styled text with outline, shadow, and gradient effects in [Kaplay.js](https://kaplayjs.com/).

## Motivation

KAPLAY renders text via WebGL, which doesn't natively support stroke, shadow, or gradient on text. For example, you can't do this:

```ts
// This doesn't work in KAPLAY
text('Hello, world!', {
  outline: { color: rgb(0, 0, 0), width: 4 },
  shadow: { color: rgb(0, 0, 0), offsetX: 4, offsetY: 4, blur: 8 },
});
```

I wanted a way to display styled text, so I created this plugin.

## Install

Install [kaplay-plugin-text](https://www.npmjs.com/package/kaplay-plugin-text):

```sh
npm install kaplay kaplay-plugin-text
```

## Usage

Import the plugin:

```ts
import kaplay from 'kaplay';
import { styledTextPlugin } from 'kaplay-plugin-text';

kaplay({
  plugins: [styledTextPlugin],
});
```

Outline text:

```ts
add([
  styledText('Hello', {
    size: 48,
    fill: rgb(255, 255, 255),
    outline: {
      color: rgb(0, 0, 0),
      width: 4,
    },
  }),
]);
```

Add a drop shadow:

```ts
add([
  styledText('Hello', {
    size: 48,
    fill: rgb(255, 255, 255),
    shadow: {
      color: rgb(0, 0, 0),
      offsetX: 4,
      offsetY: 4,
      blur: 8,
    },
  }),
]);
```

Fill with a gradient:

```ts
add([
  styledText('Hello', {
    size: 48,
    gradient: {
      from: rgb(255, 0, 0),
      to: rgb(0, 0, 255),
      direction: 'horizontal',
    },
  }),
]);
```

Combine outline, shadow, and gradient:

```ts
add([
  styledText('GAME OVER', {
    size: 56,
    outline: { color: BLACK, width: 6 },
    shadow: { color: BLACK, offsetX: 6, offsetY: 6, blur: 12 },
    gradient: {
      from: rgb(255, 215, 0),
      to: rgb(255, 50, 50),
      direction: 'horizontal',
    },
  }),
]);
```

Update text and styles at runtime:

```ts
const score = add([styledText('Score: 0', { size: 32 })]);

score.text = 'Score: 10';

score.setStyle({ fill: rgb(0, 255, 0) });
```

## How It Works

The plugin creates an offscreen `<canvas>` element, renders text using the 2D context API (`strokeText`, `shadowBlur`, `createLinearGradient`, `fillText`). Then it converts the canvas to a KAPLAY sprite via `SpriteData.fromImage()`. Rendering only happens when text or styles change (per-frame draws are a single cached sprite call).

## Links

- [GitHub](https://github.com/remarkablegames/kaplay-plugin-text)
- [NPM](https://www.npmjs.com/package/kaplay-plugin-text)

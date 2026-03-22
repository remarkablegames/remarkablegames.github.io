---
layout: post
title: Kaplay Plugin Tiled
date: 2026-03-22 16:45:07
excerpt: 🦖 How to load Tiled maps in Kaplay.js games with [kaplay-plugin-tiled](/posts/kaplay-plugin-tiled).
categories: kaplay plugin tiled map
---

[Kaplay Plugin Tiled](https://github.com/remarkablegames/kaplay-plugin-tiled) allows you to load [Tiled](https://www.mapeditor.org/) maps in [Kaplay.js](https://kaplayjs.com/). See [demo](https://remarkablegames.org/kaplay-tiled-demo/):

<iframe src="https://remarkablegames.org/kaplay-tiled-demo/" frameBorder="0" width="100%" height="500"></iframe>

## Motivation

I wanted a way to loading finite orthogonal Tiled JSON maps in my KAPLAY game so I created a plugin.

The current implementation is intentionally small:

- Finite orthogonal Tiled JSON only.
- One tileset per map.
- Visible tile layers plus optional `tiles` and `objects` matchers for extra spawned components.

## Prerequisites

Install [kaplay-plugin-tiled](https://www.npmjs.com/package/kaplay-plugin-tiled):

```sh
npm install kaplay kaplay-plugin-tiled
```

Install [Tiled](https://www.mapeditor.org/):

```sh
brew install --cask tiled
```

Open Tiled with your tileset and export the map level as JSON. See [example](https://github.com/remarkablegames/kaplay-tiled-demo/tree/master/public/tiled).

## Usage

Import the plugin:

```ts
import kaplay from 'kaplay';
import { tiledPlugin } from 'kaplay-plugin-tiled';

kaplay({
  plugins: [tiledPlugin],
});
```

Load your tileset image and map level JSON:

```ts
import level from './level.json';
import tilesetUrl from './tileset.png';

loadSprite('tileset', tilesetUrl);
```

Draw the tilemap:

```ts
addTiledMap(level, { sprite: 'tileset' });
```

Or render the tilemap and add game objects:

```ts
addTiledMap(level, {
  sprite: 'tileset',
  objects: [
    {
      match: { properties: { collides: true } },
      comps: ({ width, height }) => [
        area({
          shape: new Rect(vec2(), width, height),
        }),
        body({ isStatic: true }),
      ],
    },
  ],
});
```

## Links

- [GitHub](https://github.com/remarkablegames/kaplay-plugin-tiled)

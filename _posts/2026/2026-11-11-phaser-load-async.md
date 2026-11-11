---
layout: post
title: Loading Phaser assets in the background
date: 2026-11-11 15:28:46
excerpt: Learn how to load Phaser assets in the background without interrupting gameplay, and use loader events to know when they're ready.
categories: phaser load assets async performance
---

Learn how to load [Phaser](https://phaser.io/) assets in the background so they're ready when you need them.

## Preload

Phaser calls `create()` after the assets queued in `preload()` finish loading:

```ts
class Game extends Phaser.Scene {
  preload() {
    this.load.tilemapTiledJSON('map1', 'assets/map1.json');
    this.load.tilemapTiledJSON('map2', 'assets/map2.json');
  }

  create() {
    // blocked until all assets in preload are loaded
  }
}
```

So to get the scene or gameplay started sooner, load assets needed later after startup instead.

## Prefetch

Phaser's loader allows assets to be queued after `preload()`:

```ts
class Game extends Phaser.Scene {
  preload() {
    this.load.tilemapTiledJSON('map1', 'assets/map1.json');
  }

  create() {
    // gameplay is unblocked
    this.prefetchAsset();
  }

  private prefetchAsset() {
    this.load.tilemapTiledJSON('map2', 'assets/map2.json');

    // this is needed for assets queued outside preload()
    // and the loader won't stop the scene's update loop
    this.load.start();
  }
}
```

This loads `map2` after the scene has started. Since the loader runs asynchronously, the scene keeps updating while the map downloads.

## Loaded

The file-complete event lets you know when the asset is available:

```ts
class Game extends Phaser.Scene {
  preload() {
    this.load.tilemapTiledJSON('map1', 'assets/map1.json');
  }

  create() {
    this.prefetchAsset();
  }

  private prefetchAsset() {
    const key = 'map2';

    this.load.once(`filecomplete-tilemapJSON-${key}`, () => {
      // map2 is now available in the tilemap cache
      const map = this.make.tilemap({ key });
      // create its layers when you're ready to use it
    });

    this.load.tilemapTiledJSON(key, 'assets/map2.json');
    this.load.start();
  }
}
```

Make sure to set up the listener before calling `load.start()`.

---
layout: post
title: Phaser Scene lifecycle methods
date: 2024-04-14 14:50:33
excerpt: Understanding [Phaser](https://phaser.io/) Scene lifecycle methods.
categories: phaser scene lifecycle methods
---

This post goes over [Phaser](https://phaser.io/) Scene lifecycle methods:

1. [constructor](#constructor)
2. [init](#init)
3. [preload](#preload)
4. [create](#create)
5. [update](#update)

```js
import Phaser from 'phaser';

class MyScene extends Phaser.Scene {
  constructor() {
    console.log(1);
  }

  init() {
    console.log(2);
  }

  preload() {
    console.log(3);
  }

  create() {
    console.log(4);
  }

  update() {
    console.log(5);
  }
}
```

## constructor

`constructor` is called first when the Scene class is instantiated:

```js
export class Boot extends Phaser.Scene {
  constructor() {
    // ...
  }
}
```

Use it to set the Scene `key`:

```js
export class Boot extends Phaser.Scene {
  constructor() {
    super('mySceneKey'); // super({ key: 'mySceneKey' });
  }
}
```

## init

`init` is called after `constructor` and before `preload`:

```js
export class Boot extends Phaser.Scene {
  init(data) {
    // ...
  }
}
```

It's called every time the Scene starts/restarts and can receive optional data:

```js
this.scene.start('mySceneKey', { myData: 'foo' });
```

## preload

`preload` is called after `init` and before `create`:

```js
export class Boot extends Phaser.Scene {
  preload() {
    // ...
  }
}
```

Use it to load assets:

```js
export class Boot extends Phaser.Scene {
  preload() {
    this.load.image('myImageKey', 'path/to/image.png');
  }
}
```

## create

`create` is called after `preload` and before `update`:

```js
export class Boot extends Phaser.Scene {
  create() {
    // ...
  }
}
```

Use it to render sprites, tilemaps, etc. and attach listeners:

```js
export class Boot extends Phaser.Scene {
  create() {
    this.add.image(0, 0, 'myImageKey');
  }
}
```

## update

`update` is the game loop and it's called every step:

```js
export class Boot extends Phaser.Scene {
  update(time, delta) {
    // ...
  }
}
```

Use it to check game logic such as gameobject collisions and controller inputs:

```js
export class Boot extends Phaser.Scene {
  update() {
    if (this.cursors.up.isDown && this.player.body.touching.down) {
      this.player.body.setVelocityY(-100);
    }
  }
}
```

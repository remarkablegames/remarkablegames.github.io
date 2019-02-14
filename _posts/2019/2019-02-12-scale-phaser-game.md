---
layout: post
title: Scaling a Phaser game
date: 2019-02-12 21:28:43
excerpt: To scale or resize a Phaser game canvas, use the built-in Scale Manager.
categories: phaser scale resize game web javascript
---

## Phaser 2

To scale/resize a Phaser 2 game:

```js
var game = new Phaser.Game(/* config */);
game.scaleMode = Phaser.ScaleManager.SHOW_ALL;
game.scale.pageAlignHorizontally = true;
game.scale.pageAlignVertically = true;
```

See [example](https://phaser.io/examples/v2/input/game-scale) and [docs](https://phaser.io/docs/2.6.2/Phaser.ScaleManager.html).

## Phaser 3

To scale/resize a Phaser 3 game:

```js
new Phaser.Game({
  scale: {
    mode: Phaser.Scale.FIT,
    autoCenter: Phaser.Scale.CENTER_BOTH,
  },
  // config
});
```

[ScaleManager](https://photonstorm.github.io/phaser3-docs/Phaser.Scale.ScaleManager.html) was added in Phaser `3.16.0`. Make sure you're using that version or higher.

The scale settings are set in the [GameConfig](https://photonstorm.github.io/phaser3-docs/global.html#GameConfig__anchor). See [examples](https://labs.phaser.io/index.html?dir=scalemanager/&q=) and [docs](https://photonstorm.github.io/phaser3-docs/Phaser.Scale.ScaleManager.html).

**Note**: In order for the text to scale properly, use `fontSize` instead of `font` for the style:

```js
// good
this.add.text(16, 16, 'My Text', {
  fontSize: 32,
  fontFamily: 'Arial',
});

// bad
this.add.text(16, 16, 'My Text', {
  font: '32px Arial',
});
```

## Addendum

Before Phaser 3 added the `ScaleManager` class, I created my own [resize helper](https://gist.github.com/remarkablemark/e42a98ef7e8b1b109d298f16b8278262) that was inspired by this [article](https://www.emanueleferonato.com/2018/02/16/how-to-scale-your-html5-games-if-your-framework-does-not-feature-a-scale-manager-or-if-you-do-not-use-any-framework/).

I hope this post helped you out! Let me know if you have any questions.

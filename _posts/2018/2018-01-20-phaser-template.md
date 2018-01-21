---
layout: post
title: Phaser Template
date: 2018-01-20 19:11:17 -0500
excerpt: >-
  <p><a href="https://github.com/remarkablegames/phaser-template" target="_blank">Phaser Template</a> is a boilerplate for creating Phaser games with ES6 syntax support.</p>
  <iframe src="https://remarkablegames.github.io/phaser-template/" frameBorder="0" width="100%" height="300px"></iframe>
  <p>Because it's open-source, it's <em>free to use and modify</em>. Feedback and contributions are always welcome!</p>
  <p>What games are you going to build using <a href="https://github.com/remarkablegames/phaser-template" target="_blank">Phaser Template</a>?</p>
categories: phaser-template phaser template es6
---

> TLDR; [Phaser Template](https://github.com/remarkablegames/phaser-template) is a boilerplate for getting [Phaser](https://phaser.io) games up and running in no time.

## Motivation

Why did I create [Phaser Template](https://github.com/remarkablegames/phaser-template)?

As a game developer, I valued the following:
- ease and speed of creating and shipping a game,
- maintainability and readability of the code,
- to learn something and have fun.

Overall, this meant I wanted to spend more of my time coding the game and less of my time setting up and configuring the tools and environment in which the game runs. I built [Phaser Template](https://github.com/remarkablegames/phaser-template) hoping to solve that problem.

## Modern Syntax

Instead of the usual ES5 syntax:

```js
var game = new Phaser.Game(800, 600, Phaser.AUTO, '', {
  preload: preload,
  create: create,
  update: update
});

function preload() {
  // preload
}

function create() {
  // create
}

function update() {
  // update
}
```

You can use the cleaner [ES6](https://github.com/lukehoban/es6features#ecmascript-6-gitioes6features) syntax instead:

```js
import { Game, AUTO } from 'phaser';

class MyGame extends Game {
  constructor() {
    super(800, 600, AUTO, '');
  }

  preload() {
    // preload
  }

  create() {
    // create
  }

  update() {
    // update
  }
}

const game = new MyGame();
```

## Acknowledgements

The template is built on top of [web-app-template](https://github.com/remarkablemark/web-app-template), which is a stripped down version of [create-react-app](https://github.com/facebookincubator/create-react-app). (This is where the nice development/production configuration comes from.) In terms of deploying, it's using [gitploy](https://github.com/remarkablemark/gitploy) for deploying to [GitHub Pages](https://pages.github.com).

So what are you waiting for? Use [Phaser Template](https://github.com/remarkablegames/phaser-template) to build your next level game today!

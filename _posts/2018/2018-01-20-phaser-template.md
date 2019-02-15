---
layout: post
title: Phaser Template
date: 2018-01-20 19:11:17
excerpt: >-
  <p><a href="https://github.com/remarkablegames/phaser-template" target="_blank">Phaser Template</a> is a boilerplate for creating Phaser games. See <a href="https://remarkablegames.org/phaser-template/" target="_blank">demo</a> below.</p>
  <iframe src="https://remarkablegames.org/phaser-template/" frameBorder="0" width="100%" height="520px"></iframe>
  <p>It's <em>open-source</em> so it's <em>free to use</em> and <em>modify</em>. Feedback and contributions are welcome.</p>
  <p>What games are you planning to build using <a href="https://github.com/remarkablegames/phaser-template" target="_blank">Phaser Template</a>?</p>
categories: phaser-template phaser template es6
---

> TLDR; [Phaser Template](https://github.com/remarkablegames/phaser-template) is a boilerplate for getting [Phaser](https://phaser.io) games up and running.

## Motivation

Why did I create [Phaser Template](https://github.com/remarkablegames/phaser-template)?

It was to scratch a personal itch. As a game developer, I value the following:

- the **ease** of building and releasing a game,
- the **maintainability** and **readability** of the code,
- the ability to **learn** something new while having **fun**.

This meant I wanted to spend less time configuring and setting up the tools and more time creating the game. I built [Phaser Template](https://github.com/remarkablegames/phaser-template) to solve that problem.

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

You can use [ES6](https://github.com/lukehoban/es6features#ecmascript-6-gitioes6features) syntax instead:

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

The template is built on top of [web-app-template](https://github.com/remarkablemark/web-app-template), which is a stripped down version of [create-react-app](https://github.com/facebookincubator/create-react-app). (This is where the nice development/production configuration comes from.) In terms of deploying, it's using [gitploy](https://github.com/remarkablemark/gitploy) to deploy to [GitHub Pages](https://pages.github.com).

I'd love to hear how you plan to use [Phaser Template](https://github.com/remarkablegames/phaser-template). Contributions are always welcome!

## Demo

<iframe src="https://remarkablegames.org/phaser-template/" frameBorder="0" width="100%" height="520px"></iframe>

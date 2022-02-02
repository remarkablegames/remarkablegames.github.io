---
layout: post
title: Phaser Template
date: 2018-01-20 19:11:17
updated: 2022-01-01 15:15:24
excerpt: >-
  <p><a href="https://github.com/remarkablegames/phaser-template" target="_blank">Phaser Template</a> allows you to bootstrap Phaser games quickly. See the <a href="https://remarkablegames.org/phaser-template/" target="_blank">demo</a> below.</p>
  <iframe src="https://remarkablegames.org/phaser-template/" frameBorder="0" width="100%" height="520px"></iframe>
  <p>It's <em>open-source</em>. Feedback and contributions are welcome.</p>
  <p>What games are you planning to build using <a href="https://github.com/remarkablegames/phaser-template" target="_blank">Phaser Template</a>?</p>
categories: phaser-template phaser template es6
---

> **TLDR;**: [Phaser Template](https://github.com/remarkablegames/phaser-template) allows you to create [Phaser](https://phaser.io) games quickly.

> **2021-12-20**: Migrated Phaser Template to TypeScript.

## Motivation

Why did I create [Phaser Template](https://github.com/remarkablegames/phaser-template)?

It was to scratch an itch because as a developer, I value:

- the **ease** of building and releasing a game,
- the **maintainability** and **readability** of the good code, and
- the ability to **learn** something new while having **fun**.

I wanted to spend less time configuring and setting up the tools and more time creating the game. I built [Phaser Template](https://github.com/remarkablegames/phaser-template) with that in mind.

## Modern Syntax

Instead of the usual ES5 syntax:

```js
var game = new Phaser.Game(800, 600, Phaser.AUTO, '', {
  preload: preload,
  create: create,
  update: update,
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

You can use [TypeScript](https://www.typescriptlang.org/) with the latest syntax:

```ts
import Phaser from 'phaser';

class MyGame extends Phaser.Game {
  constructor() {
    super(800, 600, Phaser.AUTO, '');
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

This template is built with [Parcel](https://parceljs.org/) and uses a [GitHub Action](https://github.com/JamesIves/github-pages-deploy-action) to deploy to [GitHub Pages](https://pages.github.com).

I'd love to hear how you plan to use [Phaser Template](https://github.com/remarkablegames/phaser-template). Contributions are welcome!

## Demo

<iframe src="https://remarkablegames.org/phaser-template/" frameBorder="0" width="100%" height="520px"></iframe>

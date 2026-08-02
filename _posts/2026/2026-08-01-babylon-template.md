---
layout: post
title: Babylon Template
date: 2026-08-01 20:44:07
excerpt: 🎯 Babylon Template allows you to build Babylon.js games.
categories: babylon template game typescript javascript web
image: https://remarkablegames.org/babylon-template/logo.svg
---

[Babylon Template](https://github.com/remarkablegames/babylon-template) allows you to build [Babylon.js](https://www.babylonjs.com/) games. See [demo](https://remarkablegames.org/babylon-template/):

<iframe src="https://remarkablegames.org/babylon-template/" frameBorder="0" width="100%" height="500"></iframe>

## Motivation

This template gives you a ready-to-use foundation for browser-based 3D games. It handles the rendering setup, build tooling, and deployment plumbing so you can focus on building the game.

## Tech Stack

- [Babylon.js](https://www.babylonjs.com/) for 3D rendering
- [Vite](https://vitejs.dev/) for fast development and production builds
- [TypeScript](https://www.typescriptlang.org/) for type-safe game code
- [Tailwind CSS](https://tailwindcss.com/) for styling
- [GitHub Actions](https://github.com/features/actions) to build, test, and deploy to [GitHub Pages](https://pages.github.com/)

## Architecture

The template uses a lightweight ECS-style setup with `core`, `systems`, and `scenes` folders. The entry point wires up the engine, scene, and systems:

```ts
import { createEngine, createScene } from './core';
import { InputSystem, RenderSystem } from './systems';

const canvas = document.querySelector<HTMLCanvasElement>('canvas');

if (!canvas) {
  throw new Error('Game canvas not found');
}

const engine = createEngine(canvas);
const scene = createScene(engine);

new InputSystem(scene);
new RenderSystem(scene);
```

Babylon.js modules are imported selectively to keep bundle sizes small.

## Quick Start

Clone the repository:

```sh
git clone https://github.com/remarkablegames/babylon-template.git mygame
cd mygame
```

Install the dependencies:

```sh
npm install
```

Run the game in development mode:

```sh
npm start
```

Build the game for production:

```sh
npm run build
```

## Demo

See [Endless Runner](https://github.com/remarkablegames/endless-runner), a game built with this template. Dodge obstacles and keep moving forward using the arrow keys or WASD.

Play the [game](https://remarkablegames.org/endless-runner/) or check out the source code on [GitHub](https://github.com/remarkablegames/endless-runner).

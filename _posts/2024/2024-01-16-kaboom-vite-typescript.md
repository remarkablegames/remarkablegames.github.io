---
layout: post
title: Kaboom Vite TypeScript
date: 2024-01-16 19:15:12
excerpt: How to set up a [Kaboom.js](https://kaboomjs.com/) game with [Vite](https://vitejs.dev/) and [TypeScript](https://www.typescriptlang.org/).
categories: kaboom vite typescript game
---

This post goes over how to set up a [Kaboom.js](https://kaboomjs.com/) game with [Vite](https://vitejs.dev/) and [TypeScript](https://www.typescriptlang.org/).

## Create Kaboom

Generate a Kaboom.js project with [`create-kaboom`](https://kaboomjs.com/doc/setup):

```sh
npm init kaboom -- mygame
```

We won't be developing off this project but we'll copy some of the assets to our Vite project.

## Vite

[Scaffold a project with Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project):

```sh
npm create vite@latest myvite -- --template vanilla-ts
```

Delete unused files like:

- `public/vite.svg`
- `src/counter.ts`
- `src/style.css`
- `src/typescript.svg`

Update `vite.config.mts`:

```ts
import { defineConfig } from 'vite'

export default defineConfig({
  build: {
    assetsInlineLimit: 0,
  },
  esbuild: {
    minifySyntax: false,
  },
})
```

Disabling [`build.assetsInlineLimit`](https://vitejs.dev/config/build-options#build-assetsinlinelimit) ensures assets like images don't get inlined as base64 URLs.

Disabling [`esbuild.minifySyntax`](https://esbuild.github.io/api/#minify) ensures the Kaboom variables don't get uglified.

## Kaboom

Update `index.html`:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + TS</title>
  </head>
  <body>
    <!-- initialize the context with the `kaboom()` function -->
    <script type="module">
      import kaboom from 'kaboom'
      kaboom()
    </script>
    <script type="module" src="/src/main.ts"></script>
  </body>
</html>
```

The reason we're initializing `kaboom` before `main.ts` is because we want to load `kaboom` first and add it to the global namespace.

Update `src/vite-env.d.ts`:

```ts
/// <reference types="vite/client" />

import 'kaboom/global'

declare module '*.png' {
  const src: string
  export default src
}
```

By importing `kaboom/global`, you can use of the global type definitions in your code editor.

By declaring module `'*.png'`, you can use this syntax:

```ts
import bean from '/sprites/bean.png'
```

Copy `sprites/bean.png` from your `create-kaboom` project to your Vite project:

```sh
mv mygame/sprites/bean.png myvite/public/sprites/bean.png
```

Update `src/main.ts`:

```ts
// load assets
loadSprite('bean', '/sprites/bean.png')

// add a character to screen
add([
  // list of components
  sprite('bean'),
  pos(80, 40),
  area(),
])

// add a kaboom on mouse click
onClick(() => {
  addKaboom(mousePos())
})

// burp on 'b'
onKeyPress('b', burp)
```

Start your game with:

```sh
npm run dev
```

Build your game with:

```sh
npm run build
```

## Resources

- [`remarkablegames/kaboom-template`](https://github.com/remarkablegames/kaboom-template)

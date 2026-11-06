---
layout: post
title: Kaplay Plugin UI
date: 2026-11-06 16:11:13
excerpt: 🦖 How to add UI game objects like buttons, modals, and tooltips to Kaplay.js games with [kaplay-plugin-ui](/posts/kaplay-plugin-ui).
categories: kaplay plugin ui button modal tooltip
---

[Kaplay Plugin UI](https://github.com/remarkablegames/kaplay-plugin-ui) adds UI game objects like buttons, modals, and tooltips to [Kaplay.js](https://kaplayjs.com/) games.

## Motivation

KAPLAY doesn't ship with built-in UI components. You can draw shapes and text, but interactive buttons, modal dialogs, and hover tooltips have to be hand-rolled. This plugin fills that gap with game object factories and a customizable theme.

## Install

Install [kaplay-plugin-ui](https://www.npmjs.com/package/kaplay-plugin-ui):

```sh
npm install kaplay kaplay-plugin-ui
```

## Usage

Import the plugin:

```ts
import kaplay from 'kaplay';
import { uiPlugin } from 'kaplay-plugin-ui';

const k = kaplay({
  plugins: [uiPlugin],
});
```

Add a button:

```ts
k.addButton('Start', {
  pos: k.vec2(100, 100),
  onClick: () => {
    k.go('game');
  },
});
```

Add a modal:

```ts
k.addModal({
  title: 'Pause',
  text: 'Take a break?',
  actions: [
    { text: 'Resume' },
    { text: 'Quit', onClick: () => k.go('menu') },
  ],
});
```

Add a tooltip:

```ts
const button = k.addButton('Settings');

k.addTooltip('Open settings', {
  target: button,
  placement: 'top',
});
```

Customize the theme:

```ts
k.setTheme({
  palette: {
    primary: k.rgb(80, 160, 255),
    text: k.rgb(255, 255, 255),
  },
  shape: {
    borderRadius: 8,
  },
});
```

Check out the source code on [GitHub](https://github.com/remarkablegames/kaplay-plugin-ui).

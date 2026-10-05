---
layout: post
title: Wavedash init script
date: 2026-08-06 13:00:22
updated: 2026-10-05 19:13:05
excerpt: How to initialize Wavedash in your web game using JavaScript.
categories: wavedash web game javascript sdk
---

This post explains how to initialize [Wavedash](https://docs.wavedash.com/sdk/overview) in your web game:

- [Script](#script)
- [SDK](#sdk)
  - [Bundler](#bundler)
  - [CDN](#cdn)
- [GitHub Action](#github-action)

## Script

`window.Wavedash` is available before your game starts so call `init()` in your `index.html`:

```html
<script>
window.Wavedash&&(Wavedash.updateLoadProgressZeroToOne(1),Wavedash.init());
</script>
```

If you don't call `init()`, your game is blocked behind a loading screen.

## SDK

### Bundler

If you bundle your game, install the SDK for editor autocomplete and types:

```bash
npm install @wvdsh/sdk-js
```

```javascript
import Wavedash from "@wvdsh/sdk-js";

Wavedash.updateLoadProgressZeroToOne(1);
Wavedash.init();
```

The package re-exports the `window.Wavedash` global that Wavedash already provides, so there's nothing extra to download at runtime and no version to pin.

### CDN

You can also import it straight from [esm.sh](https://esm.sh/) without a build step:

```html
<script type="module">
  import('https://esm.sh/@wvdsh/sdk-js').then(({ default: Wavedash }) => {
    Wavedash.updateLoadProgressZeroToOne(1);
    Wavedash.init();
  });
</script>
```

This adds a network request on load and throws outside Wavedash, so use `wavedash dev` for local development. Prefer the [script](#script) approach unless you want the package's types.

## GitHub Action

Inject the script using [wavedash-action]({% post_url 2026/2026-08-05-wavedash-action %}). Set `inject-init: false` if your game calls `init()` itself.

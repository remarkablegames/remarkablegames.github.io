---
layout: post
title: Wavedash init script
date: 2026-08-06 13:00:22
excerpt: How to initialize the Wavedash SDK in your web game using JavaScript.
categories: wavedash web game javascript sdk
---

This post explains how to initialize the [Wavedash SDK](https://docs.wavedash.com/sdk/overview) in your web game using JavaScript.

## Script

Add the script before the closing `</body>` tag in your `index.html`:

```html
<script type="module">
  import('https://esm.sh/@wvdsh/sdk-js').then(({ default: Wavedash }) => {
    Wavedash.updateLoadProgressZeroToOne(1);
    Wavedash.init();
  });
</script>
```

The script:

1. Loads the [Wavedash SDK](https://www.npmjs.com/package/@wvdsh/sdk-js) from [esm.sh](https://esm.sh/)
2. Updates the progress bar from 0% to 100%
3. Initializes the Wavedash SDK

To pin the SDK to a specific version:

```diff
 <script type="module">
-  import('https://esm.sh/@wvdsh/sdk-js').then(
+  import('https://esm.sh/@wvdsh/sdk-js@1.3.37').then(
     ({ default: Wavedash }) => {
       Wavedash.updateLoadProgressZeroToOne(1);
       Wavedash.init();
     },
   );
 </script>
```

Alternatively, you can inject the SDK using [wavedash-action]({% post_url 2026/2026-08-05-wavedash-action %}).

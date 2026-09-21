---
layout: post
title: "How to fix Ren'Py web build: Failed to decode WEBP"
date: 2026-09-20 22:23:25
excerpt: >
  How to fix Ren'Py web build error: ["Failed to decode WEBP"](/posts/fix-renpy-web-build-failed-to-decode-webp).
categories: renpy web build python webp error
---

This post goes over how to fix the Ren'Py web build error:

```
renpy.pygame.error.error: Failed to decode WEBP
```

## Why it happens

For progressive loading, the web build generates a small placeholder thumbnail for every image using `pygame_sdl2.image.load()`.

However, Ren'Py's decoder cannot load animated WebP files, which causes the web build to fail.

## Find the culprit

Use the script to find all the animated WebP images:

```sh
find game/images -type f -name "*.webp" -exec sh -c 'webpinfo "$1" | grep -q "Animation: 1" && echo "animated: $1"' sh {} \;
```

For example:

```
animated: game/images/background.webp
```

## Fix the image

Convert each animated WebP to a still image by extracting the first frame with `webpmux`:

```sh
webpmux -get frame 1 'game/images/background.webp' -o 'game/images/background_fixed.webp'
mv 'game/images/background_fixed.webp' 'game/images/background.webp'
```

This re-encodes the image as a normal still WebP file that the decoder can load.

Alternatively, you can use an image editing tool like [Krita](https://krita.org/) to re-export the WebP image with animation disabled.

## Verify

Run the Ren'Py web build again to verify that it gets past the image decoding step.

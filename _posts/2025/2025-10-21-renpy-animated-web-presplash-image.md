---
layout: post
title: Ren'Py animated web presplash
date: 2025-10-21 19:07:56
excerpt: How to create an animated presplash image for your Ren'Py web game.
categories: renpy ffmpeg bash webp
image: https://remarkablegames.org/renpy-template/web-presplash.webp
---

This post goes over how to create an animated presplash image for your [Ren'Py](https://www.renpy.org/) web game.

## Background

When building Ren'Py for the web, it uses a default `web-presplash.jpg` image:

![Web Presplash](https://remarkablegames.org/renpy-template/web-presplash.webp)

But you can replace that image with [`web-presplash.webp`](https://www.renpy.org/doc/html/web.html#presplash), which is an [animated image format](https://wikipedia.org/wiki/WebP):

![WebP](https://remarkablegames.org/assembly-city/web-presplash.webp)

## WebP

If you have a [GIF](https://en.wikipedia.org/wiki/GIF) or video, you can convert the file to WebP using [FFmpeg](https://www.ffmpeg.org/):

```sh
ffmpeg -i input.gif -c:v libwebp -lossless 0 -compression_level 6 -q:v 75 -loop 0 -an web-presplash.webp
```

> Replace `input.gif`.

Set the options to resize the dimensions:

```
-vf scale=WIDTH:HEIGHT
```

> Replace `WIDTH` and `HEIGHT`.

Alternatively, you can use a free online converter if you don't want to use FFmpeg.

## Build

After building for the web using the Ren'Py launcher, change to the web directory:

```sh
cd my-renpy-game-web/
```

If you're using Ren'Py <[8.5.0](https://www.renpy.org/release/8.5.0), copy `web-presplash.webp` to the web directory and replace `web-presplash.jpg` in all files:

```sh
rm web-presplash.jpg
grep -lr web-presplash.jpg | xargs sed -i 's/web-presplash.jpg/web-presplash.webp/g'
```

Start a server to verify that the animated image is working:

```sh
python3 -m http.server
```

```sh
open http://localhost:8000
```

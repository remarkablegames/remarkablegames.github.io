---
layout: post
title: Ren'Py animated web presplash
date: 2025-10-21 19:07:56
updated: 2026-10-11 22:28:59
excerpt: How to create an animated presplash image for your Ren'Py web game.
categories: renpy web image ffmpeg bash webp
image: https://remarkablegames.org/renpy-template/web-presplash.webp
---

This post explains how to create an animated presplash image for your [Ren'Py](https://www.renpy.org/) web game.

## Background

When building Ren'Py for the web, the default presplash image is `web-presplash.jpg`:

![Web Presplash](https://remarkablegames.org/renpy-template/web-presplash.webp)

You can replace it with [web-presplash.webp](https://www.renpy.org/doc/html/web.html#presplash), which is an [image format](https://wikipedia.org/wiki/WebP) that supports animation:

![WebP](https://remarkablegames.org/assembly-city/web-presplash.webp)

## WebP

If you have a [GIF](https://wikipedia.org/wiki/GIF) or video, you can convert it to WebP using [FFmpeg](https://www.ffmpeg.org/):

```sh
ffmpeg -i input.gif -c:v libwebp -lossless 0 -compression_level 6 -q:v 75 -loop 0 -an web-presplash.webp
```

Replace `input.gif` with your source file. Check the result in your target browser to confirm that it animates and loops as expected.

To resize while preserving the source aspect ratio, add this filter to the command:

```
-vf "scale=WIDTH:HEIGHT:force_original_aspect_ratio=decrease"
```

Replace `WIDTH` and `HEIGHT` with the maximum dimensions. This preserves the aspect ratio, so the output may be smaller than one of those dimensions.

Use `scale=WIDTH:HEIGHT` instead if you want exact dimensions, but that can stretch the image.

Alternatively, you can use a [free online converter](https://remarkablemark.org/file-converter/).

## Video

To use a video named `web-presplash.mp4`, first build your web game.

In the generated web directory, put `web-presplash.mp4` beside `index.html`, then replace the presplash `<img>` element:

```html
<img id="presplash" src="web-presplash.webp">
```

with:

```html
<video id="presplash" autoplay muted playsinline poster="web-presplash.webp">
  <source src="web-presplash.mp4" type="video/mp4">
</video>
```

Here's a bash script that uses sed:

```sh
sed -i 's|<img id="presplash" src="web-presplash.webp">|<video id="presplash" autoplay muted playsinline poster="web-presplash.webp"><source src="web-presplash.mp4" type="video/mp4"></video>|' index.html
```

## Ren'Py <8.5.0

If you’re using a version earlier than Ren'Py [8.5.0](https://www.renpy.org/release/8.5.0), there's a bug where `web-presplash.webp` isn't copied correctly during the web build.

The solution is to copy `web-presplash.webp` into the generated web directory and run this script to update text-file references:

```sh
grep -lr web-presplash.jpg | xargs sed -i 's/web-presplash.jpg/web-presplash.webp/g'
```

You can also also delete the unused image:

```sh
rm web-presplash.jpg
```

To test the web build, start a server from the generated web directory:

```sh
python3 -m http.server
```

Then verify in your browser:

```sh
open http://localhost:8000
```

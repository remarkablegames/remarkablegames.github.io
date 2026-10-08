---
layout: post
title: Watercolor
date: 2026-10-08 15:53:58
excerpt: 🎨 [Watercolor](/posts/watercolor) turns any image into a watercolor painting.
categories: watercolor javascript canvas image browser
---

[Watercolor](https://remarkablemark.org/watercolor/) turns any image into a watercolor painting in your browser.

<iframe src="https://remarkablemark.org/watercolor/" frameborder="0" width="100%" height="800" style="display: block; margin: 0 auto;"></iframe>

## Features

- Upload an image with a file picker, drag-and-drop, or a clipboard paste
- Adjust blur, saturation, quantization, and paper texture
- Compare the original and edited image with a slider
- Download images as PNG, JPEG, or WebP
- Preview large images at a reduced scale before rendering
- Images are processed locally instead of being uploaded to a server

## Blur

Blur softens image details, making shapes feel more like watercolor washes than a photograph. The amount is measured in image pixels, so a value of `2` blurs by two pixels regardless of how large the source image is.

## Saturation

Adjust saturation to make colors more vivid or muted. A value of `1` leaves colors unchanged, while `0` produces a grayscale image.

## Color Quantization

Color quantization simplifies the image's colors, turning smooth gradients into flatter bands. Smaller steps preserve more detail; larger steps create bolder shapes.

## Paper Texture

Paper texture overlays sparse translucent specks in paper white and warm shadow, layered so that overlaps deepen the way stacked glazes do. The specks are drawn with the same blur and saturation as the image itself, so they pick up the softness and tint of the current settings instead of sitting on top as a flat overlay.

Texture positions are seeded, so the same image with the same settings always produces the same painting.

## Presets

The app includes several one-click presets:

- **Loose:** Soft focus with flat, banded color and light texture
- **Wet-on-wet:** Extra-soft focus with rich color and heavier texture
- **Sketch:** Near-monochrome with fine tonal bands and visible tooth
- **Posterized:** Bold flat shapes with coarse color banding

Presets provide a quick starting point for experimenting with different looks.

## Export

The edited image can be downloaded as PNG, JPEG, or WebP. The downloaded file keeps the original name with a `-watercolor` suffix.

Explore the [source code on GitHub](https://github.com/remarkablemark/watercolor) or try the [Watercolor app](https://remarkablemark.org/watercolor/).

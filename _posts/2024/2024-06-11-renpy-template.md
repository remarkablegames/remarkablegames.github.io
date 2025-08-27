---
layout: post
title: Ren'Py Template
date: 2024-06-11 13:10:54
excerpt: >
  [Ren'Py Template](/posts/renpy-template) allows you to bootstrap [Ren'Py](https://www.renpy.org/) visual novel games quickly.
categories: renpy template visual novel game
---

[Ren'Py Template](https://github.com/remarkablegames/renpy-template) allows you to bootstrap [Ren'Py](https://www.renpy.org/) visual novel games quickly.

## Motivation

Why did I create [Ren'Py Template](https://github.com/remarkablegames/renpy-template)?

Because I wanted to spend less time setting up the CI/CD and more time writing visual novels.

The GitHub repository contains:

- a blank project
- GitHub Actions (CI) to
  - deploy the web build to GitHub Pages
  - lint the script
  - release the project

The CI/CD uses [setup-renpy]({% post_url 2024/2024-06-10-setup-renpy-cli-github-actions %}) to automate the Ren'Py CLI workflows.

## Demo

See [demo](https://remarkablegames.org/renpy-template/):

<iframe src="https://remarkablegames.org/renpy-template/" frameBorder="0" width="100%" height="390px"></iframe>

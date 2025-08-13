---
layout: post
title: Ren'Py CLI GitHub Actions
date: 2024-06-10 19:33:05
updated: 2024-06-12 14:24:55
excerpt: How to set up [GitHub Actions](https://github.com/features/actions) workflow with [Ren'Py CLI](https://www.renpy.org/doc/html/cli.html).
categories: renpy cli github actions
---

This post goes over how to set up [GitHub Actions](https://github.com/features/actions) workflow with [Ren'Py CLI](https://www.renpy.org/doc/html/cli.html).

## Action

To set up GitHub Actions with Ren'Py CLI, use [setup-renpy](https://github.com/marketplace/actions/setup-renpy):

```yml
# .github/workflows/renpy.yml
on: push
jobs:
  renpy:
    runs-on: ubuntu-latest
    steps:
      - name: Setup Ren'Py
        uses: remarkablegames/setup-renpy@v1
```

The action downloads the [Ren'Py SDK](https://www.renpy.org/latest.html), and exposes the `renpy-cli` and `renpy-launcher` binaries for Linux/macOS and `renpy` executable for Windows:

```yml
# .github/workflows/renpy.yml
on: push
jobs:
  renpy-linux:
    runs-on: ubuntu-latest
    steps:
      - name: Setup Ren'Py
        uses: remarkablegames/setup-renpy@v1

      - name: Ren'Py version
        run: |
          renpy-cli --version
          renpy-cli --help

  renpy-windows:
    runs-on: windows-latest
    steps:
      - name: Setup Ren'Py
        uses: remarkablegames/setup-renpy@v1

      - name: Ren'Py version
        run: |
          renpy-cli --version
          renpy-cli --help
```

## Usage

### Lint

[Check script (lint)](https://www.renpy.org/doc/html/cli.html#check-script-lint):

```yml
# .github/workflows/lint.yml
on: push
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v5

      - name: Setup Ren'Py
        uses: remarkablegames/setup-renpy@v1

      - name: Lint script
        run: renpy-cli game lint
```

### Web Build

[Builds a web release of the game](https://www.renpy.org/doc/html/cli.html#web-build):

```yml
# .github/workflows/build.yml
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v5

      - name: Setup Ren'Py
        uses: remarkablegames/setup-renpy@v1
        with:
          web: true

      - name: Web build
        run: renpy-launcher web_build . --destination dist
```

> `renpy-launcher` is only available on Linux/macOS and is not available on Windows.

## Resources

- [remarkablegames/setup-renpy](https://github.com/remarkablegames/setup-renpy)
- [remarkablegames/renpy-template](https://github.com/remarkablegames/renpy-template)
- [remarkablegames/renpy-examples](https://github.com/remarkablegames/renpy-examples)

---
layout: post
title: Upload to itch.io with butler
date: 2024-02-25 13:12:55
excerpt: How to upload a game to [itch.io](https://itch.io/) with [butler](https://itch.io/docs/butler/) and [GitHub Actions](https://github.com/features/actions).
categories: itch.io butler github actions cli
---

This post goes over how to upload a game to [itch.io](https://itch.io/) with [butler](https://itch.io/docs/butler/) and [GitHub Actions](https://github.com/features/actions).

## CLI

You can use [butler](https://itch.io/docs/butler/installing.html) to upload your game locally to itch.io with the command-line.

First [login](https://itch.io/docs/butler/login.html) to butler:

```sh
butler login
```

Then [push](https://itch.io/docs/butler/pushing.html) your game to itch.io:

```sh
butler push directory user/game:channel
```

- Replace `directory` with the folder or `.zip` file of your built game
- Replace `user` with your itch.io username
- Replace `game` with your game name
- Replace `channel` with your project type (e.g., html5, linux, windows, osx, etc.)

## GitHub Actions

To upload your game to itch.io with GitHub Actions, use [setup-butler](https://github.com/marketplace/actions/setup-butler):

{% raw %}

```yml
# .github/workflows/upload.yml
name: Upload to itch.io
on: push
jobs:
  itchio-upload:
    runs-on: ubuntu-latest
    steps:
      - name: Setup butler
        uses: remarkablegames/setup-butler@v1

      - name: Upload to itch.io
        run: butler push directory user/game:channel
        env:
          BUTLER_API_KEY: ${{ secrets.BUTLER_API_KEY }}
```

{% endraw %}

The `BUTLER_API_KEY` is your [itch.io API key](https://itch.io/user/settings/api-keys). Generate a key and add it to your repository's **Settings** > **Secrets and variables** > **Actions**.

## Example

Using an [example workflow](https://github.com/remarkablegames/inversion/blob/master/.github/workflows/release-please.yml) where:

- build is located at the `dist` folder
- itch.io username is `remarkablegames`
- game name is `inversion`
- game is an `html5` project

Then the workflow step is:

{% raw %}

```diff
 - name: Upload to itch.io
-  run: butler push directory user/game:channel
+  run: butler push dist remarkablegames/inversion:html5
   env:
     BUTLER_API_KEY: ${{ secrets.BUTLER_API_KEY }}
```

{% endraw %}

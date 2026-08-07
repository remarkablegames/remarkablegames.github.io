---
layout: post
title: Upload to Wavedash with GitHub Actions
date: 2026-08-05 22:00:31
updated: 2026-08-07 15:05:31
excerpt: How to upload and publish a web game to Wavedash with `remarkablegames/wavedash-action` and GitHub Actions.
categories: wavedash github actions ci-cd deploy web game
---

This post goes over how to upload and publish a web game to [Wavedash](https://wavedash.com/) with [`remarkablegames/wavedash-action`](https://github.com/remarkablegames/wavedash-action) and [GitHub Actions](https://github.com/features/actions).

## GitHub Actions

To upload your game to Wavedash with GitHub Actions, use [wavedash-action](https://github.com/marketplace/actions/wavedash-action):

{% raw %}

```yml
# .github/workflows/wavedash.yml
name: Upload to Wavedash
on: push
jobs:
  wavedash-upload:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v7

      # Build your web game...

      - name: Upload to Wavedash
        uses: remarkablegames/wavedash-action@v1
        with:
          token: ${{ secrets.WAVEDASH_TOKEN }}
```

{% endraw %}

The `WAVEDASH_TOKEN` is your Wavedash API key. [Generate one](https://wavedash.com/dev-portal/keys) and add it to your repository's **Settings** > **Secrets and variables** > **Actions**.

If you don't already have a `wavedash.toml`, the action will create one for you and [inject the Wavedash SDK into your entrypoint HTML]({% post_url 2026/2026-08-06-wavedash-init-script %}) as long as you provide `game-id`, `upload-dir`, and `entrypoint`. The generated file looks like:

```toml
# wavedash.toml
game_id = "YOUR_GAME_ID_HERE"
upload_dir = "./dist"
entrypoint = "index.html"
```

## Example

Using an [example workflow](https://github.com/remarkablegames/tokenmaxxer/blob/master/.github/workflows/release-please.yml) where:

- build is located at the `dist` folder
- game ID is `YOUR_GAME_ID_HERE`
- entrypoint is `index.html`
- build message is the release tag

The workflow job is:

{% raw %}

```yml
wavedash:
  needs: release
  if: ${{ needs.release.outputs.release_created }}
  runs-on: ubuntu-latest

  steps:
    - name: Checkout repository
      uses: actions/checkout@v7

    # Build your web game...

    - name: Upload to Wavedash
      uses: remarkablegames/wavedash-action@v1
      with:
        token: ${{ secrets.WAVEDASH_TOKEN }}
        game-id: YOUR_GAME_ID_HERE
        upload-dir: dist
        entrypoint: index.html
        build-message: ${{ needs.release.outputs.tag_name }}
```

{% endraw %}

To publish the build immediately, add `publish: true`:

{% raw %}

```diff
-   - name: Upload to Wavedash
+   - name: Upload and publish to Wavedash
      uses: remarkablegames/wavedash-action@v1
      with:
        token: ${{ secrets.WAVEDASH_TOKEN }}
        game-id: YOUR_GAME_ID_HERE
        upload-dir: dist
        entrypoint: index.html
        build-message: ${{ needs.release.outputs.tag_name }}
+       publish: true
+       publish-title: ${{ needs.release.outputs.tag_name }}
+       publish-fixed: |
+         Fixed fullscreen sizing
+         Fixed input timing
```

{% endraw %}

The inputs `publish-title` and `publish-fixed` are optional but they allow you to add release notes.

## Inputs and outputs

The most useful [inputs](https://github.com/remarkablegames/wavedash-action#inputs) are:

- `token`: your required Wavedash API key
- `game-id`, `upload-dir`, and `entrypoint`: used to auto-create `wavedash.toml` when it's missing
- `sdk-version`: sets the Wavedash SDK version injected into the entrypoint HTML
- `build-message`: passed to `wavedash build push`
- `publish`: publishes the uploaded build when set to `true`
- `publish-title`, `publish-summary`, `publish-added`, `publish-removed`, `publish-fixed`, and `publish-adjusted`: optional release notes passed to `wavedash publish`

And the [outputs](https://github.com/remarkablegames/wavedash-action#outputs) are:

- `build-id` and `playtest-url`: returned by `wavedash build push`
- `published`: is `true` if the build was published

## Resources

- [wavedash-action](https://github.com/remarkablegames/wavedash-action)
- [Wavedash CLI docs](https://docs.wavedash.com/cli)
- [Wavedash quickstart](https://docs.wavedash.com/getting-started/quickstart)

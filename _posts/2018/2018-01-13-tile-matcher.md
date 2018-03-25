---
layout: post
title: Tile Matcher
date: 2018-01-13 21:19:22 -0500
excerpt: >-
  <p><a href="https://remarkablegames.org/tile-matcher/" target="_blank">Tile Matcher</a> has been released!</p>
  <iframe src="https://remarkablegames.org/tile-matcher/" frameBorder="0" width="100%" height="300px"></iframe>
  <p>It's a puzzle game written in Preact (see <a href="https://github.com/remarkablegames/tile-matcher" target="_blank">source</a>). The goal is to clear all the tiles with the minimum number of moves.</p>
  <p>Ready for a fun challenge? Play it <a href="https://remarkablegames.org/tile-matcher/" target="_blank">here.</a></p>
categories: tile-matcher tile-matching puzzle game preact
---

[Tile Matcher](https://remarkablegames.org/tile-matcher/) is out!

It's a [tile-matching game](https://en.wikipedia.org/wiki/Tile-matching_video_game) where the objective is to clear the board using as little moves as possible.

## Prototype

I wanted to try my hand at building a game without relying on a game engine&mdash;hence, I hacked my first [prototype](https://jsfiddle.net/remarkablemark/nxgqv5u3/) over a weekend.

<script async src="//jsfiddle.net/remarkablemark/nxgqv5u3/embed/result,js,css,html/"></script>

## Engine

Because the user interface (UI) only updates when it's clicked, there was no need for an update loop to run in the background.

I was able to build the puzzle UI using basic HTML elements and event listeners&mdash;which is why I chose [Preact](https://github.com/developit/preact) as my library of choice given its speed, size, and syntax (simplicity of use).

## Algorithm

The trickiest part was figuring out how to clear matching tiles. I used a [multi-dimensional array](https://wikipedia.org/wiki/Array_data_type#Multi-dimensional_arrays) for the data structure of the board.

```js
// 2x2 board
[
  [SPADE, DIAMOND],
  [HEART, CLUB]
]
```

When a tile is clicked, I check the top, right, bottom, and left adjacent tile. If there's a match, it would do another recursive check from the matched tile. The process will keep going until no more matches are found. Also, when a tile is matched, it's set to `null` to signify that it's _cleared_ from the board.

Then all matched tiles or `null` values are moved from the top (first in the index) to the bottom (last in the index). This create an illusion that the rest of the tiles are falling down due to gravity. However, it looks too instantaneous as there's no animation.

## UI

Everything else was pretty straightforward. The board is a [table](https://developer.mozilla.org/docs/Learn/HTML/Tables/Basics) with tiles as [buttons](https://developer.mozilla.org/docs/Web/HTML/Element/button) with [HTML entities](https://dev.w3.org/html5/html-author/charref).

```html
<!-- 2x2 board -->
<table>
  <tbody>
    <tr>
      <td>
        <button>&spades;</button>
      </td>
      <td>
        <button>&diams;</button>
      </td>
    </tr>
    <tr>
      <td>
        <button>&hearts;</button>
      </td>
      <td>
        <button>&clubs;</button>
      </td>
    </tr>
  </tbody>
</table>
```

## Game

You can play the game [here](https://remarkablegames.org/tile-matcher/) and check out the source code [here](https://github.com/remarkablegames/tile-matcher). I'd love to hear your feedback and ideas.

<iframe src="https://remarkablegames.org/tile-matcher/" frameBorder="0" width="100%" height="300px"></iframe>

---
layout: post
title: Tile Matcher
date: 2018-01-13 21:19:22 -0500
excerpt: >-
  <p><a href="https://remarkablegames.github.io/tile-matcher/" target="_blank">Tile Matcher</a> v0.1.0 has been released!</p>
  <iframe src="https://remarkablegames.github.io/tile-matcher/" frameBorder="0" width="100%" height="300px"></iframe>
  <p>It's an <a href="https://github.com/remarkablegames/tile-matcher" target="_blank">open-source puzzle game</a> written in Preact. The goal is to clear all the tiles using as little moves as possible.</p>
  <p>Ready for a challenge? <a href="https://remarkablegames.github.io/tile-matcher/" target="_blank">Play the game here.</a></p>
categories: tile-matcher tile-matching puzzle game preact
---

[Tile Matcher](https://remarkablegames.github.io/tile-matcher/) version 0.1.0 is out!

It's a [tile-matching game](https://en.wikipedia.org/wiki/Tile-matching_video_game) where the objective is to clear the board (using as little moves as possible). I wanted to see how hard it would be to build a game without relying on a full-fledged framework&mdash;hence, the first [prototype](https://jsfiddle.net/remarkablemark/nxgqv5u3/) was hacked together in a weekend.

<script async src="//jsfiddle.net/remarkablemark/nxgqv5u3/embed/result,js,css,html/"></script>

Since the puzzle interface only updates when it's clicked, there was no need to use a game engine with an update loop that's constantly running in the background. As a result, I chose [Preact](https://github.com/developit/preact) for its ease of building and rendering UI views.

The only tricky part was coming up with the algorithm for clearing tiles. In short, when a tile is clicked, the adjacent tiles (top, right, bottom, left) would be checked for a match. If a match is found, then it would continue to recursively check for other matches. Each time a match is found, the tile would be set to `undefined`. When there are no more matches, any empty tiles on the bottom are moved to the top. This gives the effect that existing tiles have fallen down. As you can guess, the data structure used for the tiles is [multi-dimensional array](https://en.wikipedia.org/wiki/Array_data_type#Multi-dimensional_arrays).

Everything else was pretty straightforward as I used [buttons](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) for the tiles and [HTML entities](https://dev.w3.org/html5/html-author/charref) for the tile content.

Play the [game here](https://remarkablegames.github.io/tile-matcher/) and check out the [source code here](https://github.com/remarkablegames/tile-matcher).

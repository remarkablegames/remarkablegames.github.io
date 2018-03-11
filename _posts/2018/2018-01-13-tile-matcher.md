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

It's a [tile-matching game](https://en.wikipedia.org/wiki/Tile-matching_video_game) where the objective is to clear the board using as little moves as possible. I wanted to try my hand at building a game without relying on a game engine&mdash;hence, I hacked my first [prototype](https://jsfiddle.net/remarkablemark/nxgqv5u3/) over a weekend.

<script async src="//jsfiddle.net/remarkablemark/nxgqv5u3/embed/result,js,css,html/"></script>

Because the user interface (UI) only updates when it's clicked, there's no need for an update loop to run in the background. I could build the UI using basic HTML and event listeners&mdash;which is why I chose [Preact](https://github.com/developit/preact) for the library's speed, size, and syntax.

The only tricky thing was coming up with an algorithm for clearing the tiles. What I ended up doing was checking the top, right, bottom, and left tile for a match when a tile is clicked. If a match is found, then it would continuously check the other tiles until no matches are found. Afterwards, all cleared tiles are moved from the top to the bottom (to create the illusion that it's falling down due to gravity). However, the lack of animation makes it look too instantaneous. The data structure is used for the tile board is a [multi-dimensional array](https://wikipedia.org/wiki/Array_data_type#Multi-dimensional_arrays).

Everything else was pretty straightforward. I used [buttons](https://developer.mozilla.org/docs/Web/HTML/Element/button) for the tiles and [HTML entities](https://dev.w3.org/html5/html-author/charref) for the icons.

You can play the game [here](https://remarkablegames.org/tile-matcher/) and check out the source code [here](https://github.com/remarkablegames/tile-matcher). I'd love to hear your feedback and ideas.

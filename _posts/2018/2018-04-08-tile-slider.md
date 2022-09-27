---
layout: post
title: Tile Slider
date: 2018-04-08 18:07:22
excerpt: >-
  <p><a href="https://remarkablegames.org/tile-slider/" target="_blank">Tile Slider</a> has been released!</p>
  <iframe src="https://remarkablegames.org/tile-slider/" frameBorder="0" width="100%" height="325px"></iframe>
  <p>It's a logic-based, combinatorial number-placement puzzle (see <a href="https://github.com/remarkablegames/tile-slider" target="_blank">source</a>).</p>
  <p>Ready to slide some tiles? Play it <a href="https://remarkablegames.org/tile-slider/" target="_blank">here</a>.</p>
categories: tile-slider sliding tile combination puzzle preact
---

[Tile Slider](https://remarkablegames.org/tile-slider/) is out!

Here's a Wikipedia [description](https://wikipedia.org/wiki/Sliding_puzzle) of the sliding block/tile puzzle:

> A **sliding puzzle**&hellip; is a combination puzzle that challenges a player to slide &hellip; pieces along certain routes &hellip; to establish a certain end-configuration.

## Data Structure

The solution would always be generated first:

```js
// 2x2 solution
[1, 2, 3, null];
```

Then it would be shuffled to create the puzzle:

```js
// 2x2 puzzle
[
  [2, 3],
  [1, null],
];
```

This is similar to the approach I used in generating a [Sudoku puzzle]({% post_url 2018/2018-03-20-sudoku %}) (minus the complex algorithm).

## UI

Like [Tile Matcher]({% post_url 2018/2018-01-13-tile-matcher %}), a lot of elements were borrowed and reused in the initial [fiddle](https://jsfiddle.net/remarkablemark/onaaa1zd/).

<script async src="https://jsfiddle.net/remarkablemark/onaaa1zd/embed/result,js,css,html/"></script>

[Preact](https://github.com/developit/preact) was once again chosen to render elements like [table](https://developer.mozilla.org/docs/Learn/HTML/Tables/Basics) and [button](https://developer.mozilla.org/docs/Web/HTML/Element/button).

```html
<!-- 2x2 puzzle -->
<table>
  <tbody>
    <tr>
      <td><button>2</button></td>
      <td><button>3</button></td>
    </tr>
    <tr>
      <td><button>1</button></td>
      <td><button></button></td>
    </tr>
  </tbody>
</table>
```

The logic for sliding the puzzle pieces around is pretty straightforward. When a tile button is clicked, it checks the left, right, top, or bottom button for an empty value. (This is also why every puzzle/solution has a single `null` value.) If an empty value is found, then the values are swapped. The puzzle is considered solved when it matches the solution array.

## Game

You can [play the game](https://remarkablegames.org/tile-slider/) and/or check out the [source code](https://github.com/remarkablegames/tile-slider). I'd love to hear your feedback and ideas.

<iframe src="https://remarkablegames.org/tile-slider/" frameBorder="0" width="100%" height="325px"></iframe>

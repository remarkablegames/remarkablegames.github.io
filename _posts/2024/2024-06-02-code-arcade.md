---
layout: post
title: Code Arcade
date: 2024-06-02 18:53:05
updated: 2026-09-16 15:32:12
excerpt: 🕹️ Learn how to program with [Code Arcade](/posts/code-arcade).
categories: kaboom educational code javascript game
image: https://remarkablegames.org/code-arcade/cover.png
---

🕹️ Learn how to program with **Code Arcade**!

<iframe src="https://remarkablegames.org/code-arcade/" frameBorder="0" width="100%" height="900" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game:

- [itch.io](https://remarkablegames.itch.io/code-arcade)
- [Newgrounds](https://www.newgrounds.com/portal/view/934247)
- [remarkablegames](https://remarkablegames.org/code-arcade/)

## How to Play

**Code Arcade** is a puzzle game where you learn to program by writing and fixing JavaScript code to beat each level.

1. Each level presents a play area (the game) and a code editor containing the level's script.
2. Read the instructions in the play area and the comments in the code to figure out the objective.
3. Write or fix the JavaScript code in the editor.
4. Press **Run** to execute the code with the [KAPLAY.js](https://kaplayjs.com/) game engine.
5. Use **WASD** or the **arrow keys** to move the player (the bean) to the exit door. In some levels you must spawn the exit, collect a key, or fight off enemies.
6. Touch the door to advance to the next level.

Buttons:

- **► Run**: run the code in the editor
- **⟳ Restart**: restore the editor to the level's original code
- **ⓘ Hint**: display a hint in the game console

> The console in the play area reports output from `console.log()`, errors, and hints.

## Features

- **31 levels** that teach JavaScript programming concepts:
  - Outputting with `console.log` and errors
  - Single-line and multi-line comments
  - Data types: strings, numbers, booleans
  - Data structures: arrays, objects
  - Variables (`let`/`const`), template literals
  - Functions: declarations, function expressions, hoisting
  - Iteration: `for` loops, `forEach()`
  - Timing: `setTimeout()`, `setInterval()`
  - Object properties and methods
  - JSON: `JSON.stringify()`, `JSON.parse()`
  - DOM events: `addEventListener`
  - Promises: fulfilled, rejected, `then`/`catch`, `async`/`await`
  - Networking: `fetch()`
- Game built on the [KAPLAY.js](https://kaplayjs.com/) engine
- In-browser code editor powered by [CodeMirror](https://codemirror.net/) with JavaScript syntax highlighting
- Keyboard (WASD/arrow keys) and mouse controls
- Progress saved when level is cleared

## Credits

- Assets from [KAPLAY Crew](https://kaplayjs.com/crew/)
- Editor from [CodeMirror](https://codemirror.net/)

## Background

I joined the [GameDev.tv Game Jam 2024](https://itch.io/jam/gamedevtv-jam-2024), but the theme was `Last Stand` and I decided not to use it.

I wanted to create a game that could teach programming fundamentals—something like [Untrusted](https://alexnisnevich.github.io/untrusted/) but more beginner-friendly.

I chose [KAPLAY.js](https://kaplayjs.com/) (formerly [Kaboom.js](https://kaboomjs.com/)) as the game engine because:

1. the API is easy-to-use and learn
2. the library has a flexible component system
3. the functions are injected into the global namespace

I created a prototype where I rendered a [CodeMirror](https://codemirror.net/) editor next to a game canvas. I added a button to "Run" the code from the editor.

But because the game keeps rendering in the same `window`, the game starts lagging after a few playthroughs due to memory leaks.

So I moved the code to [GitHub](https://github.com/remarkablegames/code-arcade) and refactored the game to render inside an [inline iframe](https://developer.mozilla.org/docs/Web/HTML/Element/iframe#srcdoc) to fix the performance issues.

I then added 20+ levels and playtested it with a bunch of people. I iterated on their feedback and adjusted the level difficulty and added hints.

Let me know what you think!

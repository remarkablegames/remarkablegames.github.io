---
layout: post
title: Code Arcade
date: 2024-06-02 18:53:05
excerpt: 🕹️ Learn how to program with [Code Arcade](/posts/code-arcade).
categories: kaboom educational code javascript game
image: https://remarkablegames.org/code-arcade/screenshots/level_0.png
---

🕹️ Learn how to program with Code Arcade:

<iframe src="https://remarkablegames.org/code-arcade/" frameBorder="0" width="100%" height="900" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game on:

- [remarkablegames](https://remarkablegames.org/code-arcade/)
- [itch.io](https://remarkablegames.itch.io/code-arcade)
- [newgrounds](https://www.newgrounds.com/portal/view/934247)

## Background

I joined the [GameDev.tv Game Jam 2024](https://itch.io/jam/gamedevtv-jam-2024), but the theme was `Last Stand` and I decided not to use it.

I wanted to create a game that could teach programming fundamentals—something like [Untrusted](https://alexnisnevich.github.io/untrusted/) but more beginner-friendly.

I chose [Kaboom.js](https://kaboomjs.com/) as the game engine because:

1. the [API](https://kaboomjs.com/#add) is easy-to-use and learn
2. the library has a [flexible component system](https://blog.replit.com/kaboom)
3. the functions are injected into the global namespace

I created a prototype in [Replit](https://replit.com/@remarkablemark/Code-Arcade) where I rendered a [CodeMirror](https://codemirror.net/) editor next to a game canvas. I added a button to "Run" the code from the editor.

But because the game keeps rendering in the same `window`, the game starts lagging after a few playthroughs due to memory leaks.

So I moved the code to [GitHub](https://github.com/remarkablegames/code-arcade) and refactored the game to render inside an [inline iframe](https://developer.mozilla.org/docs/Web/HTML/Element/iframe#srcdoc) to fix the performance issues.

I then added 20+ levels and playtested it with a bunch of people. I iterated on their feedback and adjusted the level difficulty and added hints.

Finally, I submitted the game to the game jam. Let me know what you think!

## Credits

- Assets from [Kaboom](https://kaboomjs.com/)
- Editor from [CodeMirror](https://codemirror.net/)
- Inspired by [Untrusted](https://alexnisnevich.github.io/untrusted/)

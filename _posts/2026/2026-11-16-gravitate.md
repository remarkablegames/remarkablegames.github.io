---
layout: post
title: Gravitate
date: 2026-11-16 16:52:39
excerpt: 🧲 [Gravitate](/posts/gravitate) is a puzzle platformer where you shift gravity to escape each room.
categories: phaser platformer puzzle gravity game web 2d singleplayer typescript
image: https://remarkablegames.org/gravitate/cover.png
---

🧲 **Gravitate** is a puzzle platformer where you shift gravity to escape each room. Guide the robot across walls and ceilings, and use the room itself to find your way out.

<iframe src="https://remarkablegames.org/gravitate/" title="Gravitate" frameBorder="0" width="100%" height="345" style="display: block; margin: 0 auto;"></iframe>

## Play

Play in your browser:

- [Wavedash](https://wavedash.com/games/gravitate)
- [itch.io](https://remarkablegames.itch.io/gravitate)
- [remarkablegames](https://remarkablegames.org/gravitate/)

Or download for desktop:

- [Windows](https://github.com/remarkablegames/gravitate/releases/latest/download/windows.zip)
- [macOS](https://github.com/remarkablegames/gravitate/releases/latest/download/macos.zip)
- [Linux](https://github.com/remarkablegames/gravitate/releases/latest/download/linux.zip)

<iframe width="560" height="315" src="https://www.youtube.com/embed/_Fzkyhq8CPY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## How to Play

- Control with keyboard or touchscreen:
  - **Keyboard:** WASD or arrow keys to move; W or ↑ to jump
  - **Touchscreen:** tap to walk and double-tap to jump
- Touch a green arrow to change the gravity direction
- Reach the blue portal to advance to the next level
- Hitting spikes or falling out of bounds restarts the current level

## Features

- 15 handcrafted levels with an increasing difficulty curve
- 4-direction gravity: floors, walls, and ceilings
- Momentum-based jumps and mid-air gravity shifts
- Spikes, gaps, and other hazards
- 3 sci-fi music tracks and sound effects
- Pixel-art visuals and responsive scaling

## Credits

### Art

- [Sci-fi Platformer - 16x16 Asset Pack](https://wrabitart.itch.io/sci-fi-platformer-asset-pack)
- [Pixelart Arrow Icons Pack](https://ibingames.itch.io/pixelart-arrow-icons-pack)

### Music

- [Sci-Fi Game Music Pack](https://alkakrab.itch.io/free-sci-fi-game-music-pack)

### Sounds

- [Game Sounds]({% post_url 2026/2026-11-10-game-sounds %})

## Background

I made the game for [Game Off 2026](https://itch.io/jam/game-off-2026), where the theme was **SHIFT**. I chose gravity as the mechanic that shifts, so the player has to rethink which way is down every time they collide with an arrow.

Under the hood, the room doesn’t rotate, but the player sprite does. As the gravity vector changes, the sprite and collision box reorient to match the new direction.

I bootstrapped the game from [phaser-platformer](https://github.com/remarkablegames/phaser-platformer) and built it with [Phaser](https://phaser.io/); the levels are authored in [Tiled](https://www.mapeditor.org/).

I added 15 levels with a gradual difficulty curve, and during playtesting I found that some levels have more than one solution.

I later added polish such as dust particles, landing squash, and a vignette. The level hints are rendered with [phaser-jsx]({% post_url 2024/2024-01-08-phaser-jsx %}) on a separate UI camera so they stay at a fixed size on screen.

Check out the source code on [GitHub](https://github.com/remarkablegames/gravitate) and give the game a play!

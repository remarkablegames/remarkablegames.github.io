---
layout: post
title: Room Crawler
date: 2025-04-26 13:24:57
updated: 2026-08-06 13:15:49
excerpt: 🚪 [Room Crawler is a roguelike RPG with turn-based combat.](/posts/room-crawler)
categories: renpy rpg roguelike python
image: https://remarkablegames.org/room-crawler/web-presplash.jpg
---

🚪 <kbd>Room Crawler</kbd> is a roguelike RPG with turn-based combat.

<iframe src="https://remarkablegames.org/room-crawler/" frameBorder="0" width="100%" height="388" style="display: block; margin: 0 auto;"></iframe>

## Play

Play in browser:

- [remarkablegames](https://remarkablegames.org/room-crawler)
- [Wavedash](https://wavedash.com/games/room-crawler)
- [itch.io](https://remarkablegames.itch.io/room-crawler)

Or download:

- [Windows](https://github.com/remarkablegames/room-crawler/releases/latest/download/win.zip)
- [Mac](https://github.com/remarkablegames/room-crawler/releases/latest/download/mac.zip)
- [Linux](https://github.com/remarkablegames/room-crawler/releases/latest/download/pc.zip)

## Features

- **Roguelike turn-based combat** — fight enemies in sequential encounters using energy-based actions.
- **Exploration** — move between rooms and the hall, each with randomized atmospheric descriptions.
- **Progression** — enemies and difficulty scale as you survive more encounters.
- **Skills** — unlock and upgrade abilities that change how you fight, heal, and manage energy.
- **Economy** — earn money from combat and exploration, then spend it in the shop or invest it for rewards.
- **Replayability** — randomized loot, encounters, and rewards make each run different.

## Background

This game was made for [Gamedev.js Jam 2025](https://itch.io/jam/gamedevjs-2025), which the theme was `Balance`.

I bootstrapped the game from [renpy-rpg](https://github.com/remarkablegames/renpy-rpg) so that I could make a point-and-click, turn-based combat.

[Ren'Py](https://www.renpy.org/) is a visual novel engine, but I was able to borrow mechanics from my previous games [Built to Scale]({% post_url 2024/2024-08-20-built-to-scale %}) and [Haunted Heir]({% post_url 2024/2024-09-16-haunted-heir %}).

To make the RPG system work, I created classes for the player and enemy characters. I also added RNG (random number generation) to the stats, skills, and rewards. The shop interface gives the player choices about the economy and I added an exploration mechanic to fit with the roguelike theme.

Ultimately, I created 10 levels, where you face between 1 to 3 enemies. After beating the game, you can choose to continue playing with randomly generated enemies.

The game is open sourced on [GitHub](https://github.com/remarkablegames/room-crawler). Let me know what you think!

## Credits

### Art

- [FantasyLandscapes](https://itch.io/c/3093764/pixel-art)
- [Liminal Games](https://liminal-space-dev.itch.io/free-horror-school-vn-backgrounds)

### Audio

- [Heal Up](https://pixabay.com/sound-effects/heal-up-39285/)
- [Health Pickup](https://pixabay.com/sound-effects/health-pickup-6860/)
- [Heartbeat 01 - BRVHRTZ](https://pixabay.com/sound-effects/heartbeat-01-brvhrtz-225058/)
- [Kenney Interface Sounds](https://kenney.nl/assets/interface-sounds)
- [Punch Sound Effects](https://pixabay.com/sound-effects/punch-sound-effects-28649/)
- [superbrelaxation](https://pixabay.com/sound-effects/superbrelaxation-19606/)

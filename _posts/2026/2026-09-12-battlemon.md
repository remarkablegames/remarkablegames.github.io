---
layout: post
title: Battlemon
date: 2026-09-12 21:19:56
excerpt: ⚔️ [Battlemon](/posts/battlemon) is an autobattler where you tame, fight, and level up your monsters.
categories: kaplay typescript game autobattler web
image: https://remarkablegames.org/battlemon/cover.jpeg
---

⚔️ [**Battlemon**](https://remarkablegames.org/battlemon/) is a mobile-first, Pokémon-inspired autobattler. It was made for the [Craftpix Indie Jam #1-2026](https://itch.io/jam/craftpix-indie-jam-1-2026), where the theme was "_Ten. Celebrate. Level Up._"

<iframe src="https://remarkablegames.org/battlemon/" frameBorder="0" width="100%" height="960"></iframe>

## Play

Play in your browser:

- [Wavedash](https://wavedash.com/games/battlemon)
- [itch.io](https://remarkablegames.itch.io/battlemon)
- [remarkablegames](https://remarkablegames.org/battlemon/)

Or download for desktop:

- [Windows](https://github.com/remarkablegames/battle-monster/releases/latest/download/windows.zip)
- [macOS](https://github.com/remarkablegames/battle-monster/releases/latest/download/macos.zip)
- [Linux](https://github.com/remarkablegames/battle-monster/releases/latest/download/linux.zip)

## How to Play

- **Fight** — monsters auto-attack and fire special moves on their own. Your job is to manage the battle.
- **Swap** — tap a bench slot to swap the active monster (3-second cooldown).
- **Items** — spend coins on potions, full restores, and temporary battle boosters mid-fight.
- **Tame** — after each victory, tame 1 defeated enemy to add to your team.
- **Level Up** — monsters earn XP for participating in battle, fully heal, and learn new moves.

## Features

- **🎮 Starter choice** — pick 1 of 3 monsters and preview your enemies before the battle.
- **⚔️ Real-time autobattler** — up to 3 monsters fielded from a team of 6, with mid-fight swapping and item use.
- **🧬 6 monster types** — Fire, Water, Plant, Electric, Earth, and Air with a rock-paper-scissors type chart (1.5× strong, 0.5× weak) and crit attacks (15% chance, 1.5× damage).
- **🎭 6 personalities** — Brave, Timid, Sturdy, Swift, Calm, and Fierce bias a monster's stats, making every run unique.
- **🏋️ Leveling & XP** — monsters earn XP for participating in battle, fully heal, and learn new moves on leveling up.
- **🪤 Taming** — after each victory, tame 1 defeated enemy to grow your collection.
- **🛒 Shop** — spend coins on potions, full restores, battle boosters (Enrage, Iron Skin, Haste, Enemy Debuff), and level-ups; sell monsters for coins.
- **🌊 Endless waves** — permadeath runs with rising difficulty; your best wave is saved.
- **📱 Mobile-first design** — portrait layout, large touch targets, and pixel-art sprites with 8-bit chiptune music.

## Credits

### Art

- [Dino Characters](https://arks.itch.io/dino-characters) by [@ArksDigital](https://twitter.com/ArksDigital)
- [Free Tiny Hero Sprites Pixel Art](https://free-game-assets.itch.io/free-tiny-hero-sprites-pixel-art)
- [Free Pixel Predator Plant Mob Sprites](https://free-game-assets.itch.io/free-predator-plant-mobs-pixel-art-pack)
- [Free Slime Mobs Pixel Art](https://free-game-assets.itch.io/free-slime-mobs-pixel-art-top-down-sprite-pack)
- [KAPLAY Crew](https://kaplayjs.com/crew/)

### Audio

- [xDeviruchi - 8-bit Fantasy & Adventure Music](https://xdeviruchi.itch.io/8-bit-fantasy-adventure-music-pack)
- [Pixel UI Sound Effects by Atelier Magicae](https://ateliermagicae.itch.io/pixel-ui-sound-effects)
- [FilmCow Royalty Free Sound Effects Library](https://filmcow.itch.io/filmcow-sfx)
- [Sound effects from Pixabay](https://pixabay.com/sound-effects/)

## Background

I wanted to build a mobile-first Pokémon-style autobattler where the battles play themselves but you still feel in control. I made this for the [Craftpix Indie Jam #1-2026](https://itch.io/jam/craftpix-indie-jam-1-2026), where the theme **Level Up** was a natural fit for a monster-taming game built around XP and level-ups.

This game is powered by [KAPLAY.js](https://kaplayjs.com/) and it has pixel sprites, GBA-style battle backgrounds, and chiptune music. Best-wave progress is saved to localStorage and a huge effort went into making this mobile-first and touchscreen compatible.

Check out the source code on [GitHub](https://github.com/remarkablegames/battle-monster).

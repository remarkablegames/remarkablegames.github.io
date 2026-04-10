---
layout: post
title: Awestruck
date: 2026-04-08 20:40:50
updated: 2026-04-09 21:30:15
excerpt: 🎴 [Awestruck is a deckbuilding card game that synergizes words.](/posts/awestruck)
categories: kaplay deckbuilder card game web 2d
image: https://remarkablegames.org/awestruck/screenshot.png
---

🎴 **Awestruck** is a deckbuilding card game that synergizes words.

<iframe src="https://remarkablegames.org/awestruck/" frameBorder="0" width="700" height="438" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game:

- [itch.io](https://remarkablegames.itch.io/awestruck)
- [remarkablegames](https://remarkablegames.org/awestruck/)

Or download:

- [Windows](https://github.com/remarkablegames/awestruck/releases/latest/download/windows.zip)
- [Mac](https://github.com/remarkablegames/awestruck/releases/latest/download/macos.zip)
- [Linux](https://github.com/remarkablegames/awestruck/releases/latest/download/linux.zip)

<iframe width="560" height="315" src="https://www.youtube.com/embed/aT9wrRO0wV4?si=IOc8Yw_YhVAZ9Ex7" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## How to Play

- Cards
  - The top-left number on the card is the cost, which decreases your energy
  - A modifier card enhances the payload card (and modifiers can be stacked)
  - The last card in the chain must be a payload for "Execute" to work
- Stats
  - Player stats can be found at the top-left of the screen
  - Enemy stats can be found at the top-right of the screen
- Defeat the enemy and don't let your health go below 0
- Select rewards to upgrade your cards/stats

## Credits

- [Blue_Fox](https://ko-fi.com/bluefox77551) (Art)
- [AstreFone](https://soundcloud.com/astrefone) (Music)
- [Mark](https://github.com/remarkablemark) (Programming)
- Sound effects from [Kenney](https://kenney.nl/assets/interface-sounds) and [Pixabay](https://pixabay.com/sound-effects/)

## Background

This game was made for [Unlikely Collaborators™ Game Jam](https://itch.io/jam/ucgamejam2026), which the theme was **consciousness and identity through awe and wonder - make awe playable!**

We were inspired by [Slay the Spire](https://wikipedia.org/wiki/Slay_the_Spire) and made a deckbuilding card game where you combine words to create combos and synergies.

During ideation, we had ideas like a word detective puzzle, dungeon crawler inside a library, bugs could eat paper/clothing, and words can be fed to the bugs. However, we descoped them due to time.

[Blue_Fox](https://ko-fi.com/bluefox77551) drew the art and came up with the wonderful bug designs:

- Hatchling
  - Larvae that can tackle/shove/slam
- Soldier
  - Termite with bite/crush ability
- Archer
  - Beetle with a snout for acid spray/projectile attack
- Reaver
  - Mantis moth that slices

She also drew 23 card images and the game logo.

[AstreFone](https://soundcloud.com/astrefone) composed the music and created several of the sound effects.

His 2 tracks:

1. Airwindow
   - Played during combat
2. Unertainty
   - Played during the title/menu/reward scenes)

Both BGMs were ethereal and ambient given the pads and other experimental/otherworldly sounds.

I used [KAPLAY](https://kaplayjs.com/) as the game engine for this 2D web game. I bootstrapped the game from [kaplay-template](https://github.com/remarkablegames/kaplay-template).

I created a prototype of the combat system with all text and no images and sounds before adding a reward system, level progression, and polish. I playtested the game many times to ensure the game balance felt right.

In the end, I created 8 floors and added a variety of mechanics to make the game interesting:

- Player can add, upgrade, and remove cards from their deck
- After beating the boss at floor 4, the player can add a relic that triggers every turn
- I made sure there were enough modifier and payload cards for different strategies (aggro, defensive, etc.)

We had a lot of fun making this game so feel free to give it a [play](https://remarkablegames.itch.io/awestruck)!

---
layout: post
title: Bite the Living
date: 2025-05-20 19:02:52
excerpt: 🧟 [Control zombies and attack humans!](/posts/bite-the-living)
categories: web kaplay real-time-strategy pixel-art 2d
image: https://remarkablegames.org/bite-the-living/logo.png
---

🧟 **Bite the Living** is a real-time-strategy game where you control zombies and attack humans.

<iframe src="https://remarkablegames.org/bite-the-living/" frameBorder="0" width="700" height="800" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game:

- [itch.io](https://remarkablegames.itch.io/bite-the-living)
- [remarkablegames](https://remarkablegames.org/bite-the-living)

## How to Play

- Move with mouse
- Left click to select zombie(s)
- Right click to move zombie(s)
- Defeat all humans before zombies die

## Background

The game was made for [Pixel Game Jam 2025](https://itch.io/jam/-pixel-game-jam-2025), which the theme was **From the Dead**.

We ideated on [Excalidraw](https://excalidraw.com/#json=eeiKPEwkUf2AauUocUiSH,5PfjhMuUElgs1RlALq52Dw) and decided to go with a reverse zombie game where you control zombies and attack humans (similar to [Infectonator](https://www.togeproductions.com/project/infectonator/)).

We chose [KAPLAY](https://kaplayjs.com/) as the game engine because prototyping is fast and it handles 2D pixel art. The game was bootstrapped from [kaplay-template](https://github.com/remarkablegames/kaplay-template).

We used the assets:

- [Zombie Apocalypse AssetPack](https://pixelrogueknight.itch.io/zombie-apocalypse-assetpack)
- [Free Horror Music Pack](https://void1gaming.itch.io/free-horror-music-pack)
- [Pixabay](https://pixabay.com/sound-effects/)

We added the characters:

- Zombie
  - Spawns when Human dies
  - Loses health over time
  - Does damage when it collides with Human
- Fast Zombie
  - Spawns when Gunman dies
  - Shares similar properties as Zombie except it moves 1.5x faster
- Human
  - Moves away from zombie
- Gunman
  - Shares similar properties as Human except it doesn't move
  - Shoots at zombie every 3 seconds (with friendly fire)

The player can choose one of two rewards after each level (except the tutorial):

- Increase zombie speed
- Increase zombie health
- Increase zombie damage
- Increase zombie heal after beating a human
- Increase line of sight so zombie moves to human if it's within a distance

The game has 10 levels. The initial levels are tutorials for the controls and mechanics. The later levels required strategy to defeat humans with a horde of zombies.

Check out the game and let me know what you think! You can find the code on [GitHub](https://github.com/remarkablegames/bite-the-living).

## Credits

### Art

- [Zombie Apocalypse AssetPack](https://pixelrogueknight.itch.io/zombie-apocalypse-assetpack)

### Music

- [Free Horror Music Pack](https://void1gaming.itch.io/free-horror-music-pack)

### Sound

- [080886_Bullet](https://pixabay.com/sound-effects/080886-bullet-39738/)
- [080998_Bullet Hit](https://pixabay.com/sound-effects/080998-bullet-hit-39870/)
- [086553_Bullet Hit](https://pixabay.com/sound-effects/086553-bullet-hit-39853/)
- [Zombie sound](https://pixabay.com/sound-effects/zombie-sound-224167/)
- [bulletshot impact (Sound effect)](https://pixabay.com/sound-effects/bulletshot-impact-sound-effect-230462/)
- [platzender Kopf](https://pixabay.com/sound-effects/platzender-kopf-107522/)

### Development

- [Rob Cohen](https://github.com/rmacohen)
- [remarkablemark](https://github.com/remarkablemark)

---
layout: post
title: Weather Shelter
date: 2026-06-07 20:01:57
excerpt: ☂️ [Build shelters before the storm arrives. Can your creations weather the storm?](/posts/weather-shelter)
categories: phaser puzzle game web 2d singleplayer matterjs
image: https://remarkablegames.org/weather-shelter/screenshots/cover.png
---

☂️ Build shelters before the storm arrives. Can your creations weather the storm?

<iframe src="https://remarkablegames.org/weather-shelter/" frameBorder="0" width="100%" height="400" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game:

- [Wavedash](https://wavedash.com/games/weather-shelter)
- [itch.io](https://remarkablegames.itch.io/weather-shelter)
- [remarkablegames](https://remarkablegames.org/weather-shelter/)

Or download:

- [Windows](https://github.com/remarkablegames/weather-shelter/releases/latest/download/windows.zip)
- [Mac](https://github.com/remarkablegames/weather-shelter/releases/latest/download/macos.zip)
- [Linux](https://github.com/remarkablegames/weather-shelter/releases/latest/download/linux.zip)

## Description

**Weather Shelter** is a physics-based puzzle game where you construct shelters to protect animals from the oncoming storm. Stack boxes, planks, and stones to create sturdy structures that can withstand rain, wind, and falling debris. Each level introduces new challenges and materials, testing your engineering skills and creativity.

## How to Play

Protect animals from the storm by building shelters out of building materials before the weather strikes.

### Build Phase

- **Drag blocks** onto the animals to construct a shelter around them
- Boxes, stones, and planks behave differently — experiment with stacking them
- Level 1 has no timer; later levels give you a countdown before the storm starts
- Click **Start Storm** when you're ready (or wait for the timer to run out)
- Click **Restart** to restart the current level

### Storm Phase

- Rain falls and damages any animal it hits directly
- Later levels add **wind** that pushes animals and blocks sideways
- Level 3+ drops **debris** that can knock your shelter apart
- Watch each animal's health bar — green is safe, red is critical
- The storm ends on its own; survive it with all animals alive to win

### Tips

- Stack blocks above and around animals to block falling rain
- Use **stones** to anchor structures against wind and debris
- Lean **planks** as sloped roofs to deflect rain off to the sides

### Win / Lose

- **Win**: all animals survive the storm
- **Lose**: any animal's health reaches 0

Progress is saved so you can pick up from where you left off.

## Credits

### Art

- [Sunny Land](https://ansimuz.itch.io/sunny-land-pixel-game-art) by [ansimuz](https://ansimuz.itch.io/)
- [Free Swamp 2D Tileset Pixel Art](https://free-game-assets.itch.io/free-swamp-2d-tileset-pixel-art) by [Free Game Assets](https://free-game-assets.itch.io/)

### Sounds

- [mexican mountain twilight](https://www.subsocials.com/stuff/mexican-mountain-twilight)
- [Thunder Sound](https://pixabay.com/sound-effects/nature-thunder-sound-375727/) by [SoundReality](https://pixabay.com/users/soundreality-31074404/)
- [Fist Punch or kick](https://pixabay.com/sound-effects/fist-punch-or-kick-7171/) by [rcroller](https://pixabay.com/users/freesound_community-46691455/)
- [Mouse click](https://pixabay.com/sound-effects/mouse-click-290204/) by [MatthewVakaliuk73627](https://pixabay.com/users/matthewvakaliuk73627-48347364/)
- [Pop](https://pixabay.com/sound-effects/pop-423717/) by [SoundReality](https://pixabay.com/users/soundreality-31074404/)
- [click button](https://pixabay.com/sound-effects/click-button-131479/) by [666HeroHero](https://pixabay.com/users/666herohero-25759907/)

## Background

I made this game for Wavedash Spring Jam 26, and the theme was **shelter**.

Inspired by [Fortify]({% post_url 2019/2019-01-27-fortify %}), a game I made in the past, I wanted the player to build a shelter for animals for an incoming storm.

I used [phaser-template](https://github.com/remarkablegames/phaser-template) and added the features:

- 5 levels
- Pixel art and nature sound effects
- [Matter.js](https://www.brm.io/matter-js/) physics

Check out the game on [GitHub](https://github.com/remarkablegames/weather-shelter) and give it a [play](https://wavedash.com/games/weather-shelter)!

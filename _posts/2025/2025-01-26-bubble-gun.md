---
layout: post
title: Bubble Gun
date: 2025-01-26 18:47:34
excerpt: 💦 🔫 [Shoot bubbles at enemies!](/posts/bubble-gun)
categories: web kaplay ggj arcade survival
image: https://remarkablegames.org/bubble-gun/images/cover.png
---

💦 🔫 **Bubble Gun** is a top-down survival game where you shoot bubbles at enemies.

<iframe src="https://remarkablegames.org/bubble-gun/" frameBorder="0" width="700" height="800" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game:

- [remarkablegames](https://remarkablegames.org/bubble-gun)
- [itch.io](https://remarkablegames.itch.io/bubble-gun)
- [newgrounds](https://www.newgrounds.com/portal/view/966187)

## How to Play

- Move with WASD or arrow keys
- Left click to shoot a bubble
- Enemies will pop if they get hit with too many bubbles
- Bubbled enemies can fall down the drain
- Avoid enemies and projectiles

## Credits

- KitB@sh - Artist, Composer ([SoundCloud](https://soundcloud.com/k1tb4sh), [YouTube](https://www.youtube.com/@kitbash52))
- remarkablemark - Programmer ([GitHub](https://github.com/remarkablemark))

## Background

This game was made for [Global Game Jam 2025](https://globalgamejam.org/games/2025/kiki-and-boba-4), in which the theme was `Bubble`.

I collaborated with KitBash, who did the art and composition of this game. He had an idea of a top-down survival shooter similar to [HoloCure](https://store.steampowered.com/app/2420510/HoloCure__Save_the_Fans/) and [Vampire Survivors](https://store.steampowered.com/app/1794680/Vampire_Survivors/).

We originally wanted to make it a two-player game, but we stuck with single-player to minimize scope.

I chose [KAPLAY](https://kaplayjs.com/) as the game engine since I found it fast to prototype ideas. I bootstrapped the game from [kaplay-template](https://github.com/remarkablegames/kaplay-template).

We came up with five enemies:

1. Bubbie (duck that shoots bubbles)
2. Gooba (shark that goes underwater)
3. Shellie (shellfish)
4. Spiny (flower that shoots darts but we never implemented that feature)
5. Pokey (enemy that sneezes horns)

We also added several bubble mechanics:

- bubbles can grow in size and damage
- bubble can combine
- bubbles can pop
- player and enemy can be trapped inside a growing bubble
- bubbles can slow the player and enemy

Finally, we added a drain that instant kills enemies in a bubble. Orignally, we wanted to group enemies together in one bubble and then push the bubble down the drain, but I wasn't able to build that out.

We also wanted to add a tutorial/cutscene but that wasn't fully implemented as well.

Either way, we had a blast making the game. Feel free to play it and let me know what you think! You can find the code on [GitHub](https://github.com/remarkablegames/bubble-gun).

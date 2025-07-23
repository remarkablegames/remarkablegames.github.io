---
layout: post
title: Assembly City
date: 2025-07-23 13:41:03
excerpt: ⚖️ [Roguelike deck-building card game about facilitating a Citizens' Assembly.](/posts/assembly-city)
categories: renpy deckbuilding card game python
image: https://remarkablegames.org/assembly-city/web-presplash.jpg
---

⚖️ Roguelike deck-building card game about facilitating a Citizens' Assembly.

<iframe src="https://remarkablegames.org/assembly-city/" frameBorder="0" width="690" height="388" style="display: block; margin: 0 auto;"></iframe>

## Play

Play the game on:

- [remarkablegames](https://remarkablegames.org/assembly-city)
- [itch.io](https://remarkablegames.itch.io/assembly-city)

## How To Play

- Drag the card to the citizen.
- Click on the citizen name to see their next move.
- Press **End Turn** when out of **Moves**.
- The objective is to reach the **Consensus** goal.

## Background

This game was made for the [Citizens, Assemble!](https://itch.io/jam/citizens-assemble) game jam. Read the [Game Design Document](https://docs.google.com/document/d/1PNHJMR5JvdEDIB-idLO4p4yMY9trMl1CO2deXqtjP_8/edit).

Our initial idea was to create a narrative-driven game like the [Ace Attorney](https://en.wikipedia.org/wiki/Ace_Attorney) series (see our [brainstorming session](https://excalidraw.com/#json=6czVMRbr8qxWM-nVA6Zlt,Zd68FBkx9bQ8ZplCWGlyBg)). Hence, we chose [Ren'Py](https://www.renpy.org/) as the visual novel engine.

The idea was that you play as a citizen who tries to help everyone reach a consensus in an assembly. We were thinking about interlacing comedic characters with emotional plots, like preventing the city from being overrun by cats to stopping a war.

However, our proof-of-concept didn't feel that interesting and having to talk to multiple characters to unlock branches felt like a chore. As a result, we decided to pivot.

Recently, I've been into [roguelike deck-building games](https://en.wikipedia.org/wiki/Roguelike_deck-building_game) so I did a quick [prototype in Ren'Py](https://github.com/remarkablegames/renpy-deckbuilder). I pitched my vision to the team and we decided to commit to this genre.

The card mechanic was implemented using [drag and drop](https://www.renpy.org/doc/html/drag_drop.html) screens. The other RPG mechanics were borrowed from [renpy-rpg](https://github.com/remarkablegames/renpy-rpg).

I removed the story dialogue and focused more on the card mechanics. I added a tutorial and 9 levels with increasing difficulty (as you progress, you need to reach a higher consensus goal with more citizens). After beating each level, you're rewarded with a card or upgrade and you can buy/upgrade/sell cards in the shop. Finally, I added a good and bad ending.

The game is open sourced on [GitHub](https://github.com/remarkablegames/assembly-city). Let me know what you think!

## Credits

### Art

- [Sraye](https://sraye.itch.io/mature-male-character-sprites)
- [Tainara-P](https://tainara-p.itch.io/)
- [smashingstocks](https://www.flaticon.com/free-icon/justice-scale_6744071)
- [sutemo](https://sutemo.itch.io/)

### Audio

- [Kenney Interface Sounds](https://kenney.nl/assets/interface-sounds)
- Pixabay
  - [Cash Register Purchase](https://pixabay.com/sound-effects/cash-register-purchase-87313/)
  - [Heal Up](https://pixabay.com/sound-effects/heal-up-39285/)
  - [Heartbeat 01 - BRVHRTZ](https://pixabay.com/sound-effects/heartbeat-01-brvhrtz-225058/)
  - [Level Up 03](https://pixabay.com/sound-effects/level-up-03-199576/)
  - [Punch Sound Effects](https://pixabay.com/sound-effects/punch-sound-effects-28649/)
  - [Soda can open](https://pixabay.com/sound-effects/soda-can-open-183214/)
  - [card mixing](https://pixabay.com/sound-effects/card-mixing-48088/)

### Development

- [Rob Cohen](https://github.com/rmacohen)
- [remarkablemark](https://github.com/remarkablemark)

### Music

- [Hizumi Tail](https://hizumi-tail.itch.io/)

## Resources

- [POV: a cynic's guide to Citizens' Assembly](https://oneworldornone.world/the-comic-book-explainer)
- [Citizens' Assembly Explained](https://assemblyexplainer.com/)
- [Assembling an Assembly Guide](https://assemblyguide.demnext.org/)

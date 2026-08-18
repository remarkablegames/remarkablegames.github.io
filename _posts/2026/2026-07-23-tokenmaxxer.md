---
layout: post
title: Tokenmaxxer
date: 2026-07-23 13:01:04
excerpt: 🏆 [Tokenmaxxer](/posts/tokenmaxxer) is an incremental game where you climb the corporate AI leaderboard—one token at a time.
categories: react incremental clicker game web singleplayer ai game-jam
image: https://remarkablegames.org/tokenmaxxer/cover.png
---

🏆 **Tokenmaxxer** is an incremental game where you climb the corporate AI leaderboard—one token at a time.

<iframe src="https://remarkablegames.org/tokenmaxxer/" frameBorder="0" width="100%" height="500" style="display: block; margin: 0 auto;"></iframe>

## Play

Play in your browser:

- [itch.io](https://remarkablegames.itch.io/tokenmaxxer)
- [Wavedash](https://wavedash.com/games/tokenmaxxer)
- [remarkablegames](https://remarkablegames.org/tokenmaxxer/)

Download for desktop:

- [Windows](https://github.com/remarkablegames/tokenmaxxer/releases/latest/download/windows.zip)
- [macOS](https://github.com/remarkablegames/tokenmaxxer/releases/latest/download/macos.zip)
- [Linux](https://github.com/remarkablegames/tokenmaxxer/releases/latest/download/linux.zip)

## Description

Click the **Token Reactor**, automate production, deploy increasingly questionable AI models, and chase ever-larger **High Scores**.

The production dashboard grows alongside your operation:

- Purchase manual, automation, and efficiency upgrades
- Activate **Token Surge** and **Hyperfocus** abilities
- Evolve a workstation into a **Cosmic Token Reactor**
- Earn milestones and achievements
- Follow workplace drama through **Ops Comms**
- Start new sessions for a permanent **Token Multiplier**
- Continue chasing records after the main progression ends

Every new **High Score** awards a **Performance Bonus** and reveals a larger target. Your first session takes roughly 15–20 minutes to reach the reset milestone, but the leaderboard never truly ends.

> Progress saves automatically in your browser. No account is required, and you can export or import your save data at any time.

## How to Play

- Click or tap the **Token Reactor** to generate tokens
- Purchase upgrades to improve tokens per click and tokens per second
- Use the `×1`, `×10`, or `MAX` controls to purchase upgrades in bulk
- Activate abilities when they come off cooldown
- Reach a new **High Score** to earn a **Performance Bonus**
- Start a new session to reset normal progress and gain a permanent **Token Multiplier**

Audio begins after your first interaction and can be adjusted or muted in the settings.

## Background

I made Tokenmaxxer for the [Stop Killing Games Community Jam 2026](https://itch.io/jam/skg-jam-2026), whose theme was **High Score Chasers**.

The theme made me think of an incremental game. Clickers are already about making numbers go up, but I wanted the next record to drive the experience. The current total, target, progress bar, and next **Performance Bonus** stay visible so there's always one more milestone to chase.

The first version exposed almost every system at once. Although it looked like an AI operations dashboard, it was easy for a new player to get information overload. I added progressive onboarding, delayed upgrade reveals, clearer text hierarchy, and a guided path from manual clicking to automation. I also spent a lot of time adjusting font sizes, spacing, alignment, modal readability, and upgrade states so the dashboard remained dense without feeling like a wall of data.

Balance took several rounds of playtesting. Early versions made late-game upgrades/multipliers too powerful, allowing several records to be reached instantaneously. I tuned upgrade costs, growth rates, ability durations, and automation output until the first session generally took around 15–20 minutes.

The **Token Reactor** became the visual center of progression. It evolves through six stages:

1. Workstation
2. Server Core
3. AI Cluster
4. Datacenter
5. Planetary Processor
6. Cosmic Token Reactor

Each stage uses custom SVG artwork and CSS animation. Distinct icons were created for every upgrade and ability. As the high score grows, the **Cosmic Token Reactor** changes color to signify it becoming its own entity.

The office setting also gave room to add narratives without interrupting the core game loop. **Ops Comms** delivers short workplace messages from management, IT, colleagues, and the **Token Reactor** itself. The messages react to clicks, upgrades, abilities, high scores, and new sessions. I also added a roster of parody AI models—Croak, GoPilot, TalkGPT, GeminAI, Claudio, DeepThunk, Babble, Gimme K0.5, and LegendOS—that let me poke fun at AI branding, billing, benchmarks, context windows, hallucinations, FOMO, and corporate hype.

Starting a new session resets tokens, normal upgrades, abilities, and the current **High Score** ladder. Milestones, achievements, lifetime statistics, and the **Benchmark Rating** remain as saved memories. The rating grants a permanent **Token Multiplier**, making each new session faster without turning it into a separate currency or prestige shop.

I built the game with:

- [React](https://react.dev/)
- [TypeScript](https://www.typescriptlang.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Vite](https://vite.dev/)
- [Howler.js](https://howlerjs.com/)

The game stores progress locally and includes manual save, export, import, and reset controls. It also supports reduced motion, responsive layouts, background music transitions, and sound feedback for clicks, upgrades, abilities, messages, milestones, and session resets.

Check out the [source code on GitHub](https://github.com/remarkablegames/tokenmaxxer), then see how high you can push the [AI leaderboard](https://remarkablegames.itch.io/tokenmaxxer)!

## Credits

### Music

- [DavidKBD - Code Injection Dark Techno Music Pack](https://davidkbd.itch.io/code-injection-dark-techno-music-pack)

### Sounds

- [Pixel Combat by Helton Yan & Beto Bezerra](https://heltonyan.itch.io/pixelcombat)

### Font

- [Orbitron](https://fonts.google.com/specimen/Orbitron?preview.script=Latn)

---
layout: post
title: Game Sounds
date: 2026-11-10 14:29:06
excerpt: 🎵 Procedurally generated [game sounds](/posts/game-sounds) in 4 audio styles (UI, outcomes, combat, and more).
categories: game sounds python cli audio wav ogg mp3
---

🎵 Procedurally generated [game sounds](https://remarkablegames.org/game-sounds/) in 4 audio styles (UI, outcomes, combat, and more):

<iframe src="https://remarkablegames.org/game-sounds/" frameborder="0" width="100%" height="800" style="display: block; margin: 0 auto;"></iframe>

## Download

Download the full pack:

- [sounds.zip](https://github.com/remarkablegames/game-sounds/releases/latest/download/sounds.zip)

## Motivation

I wanted a CLI that generates game sound effects from code, so a project can ship audio without sample packs, attribution, or licensing.

Everything is synthesized with Python’s standard library:

- No samples, Python packages, or audio dependencies
- Deterministic output: the same `--seed` renders the same audio
- 39 cues × 4 styles, so one style can cover an entire game
- Each sound is rendered as a 44.1 kHz mono WAV master, with optional OGG and MP3 versions

## Styles

1. **Retro**: Chiptune pulse and square leads, bitcrush/sample-hold grit, arcade sweeps
2. **Modern**: Detuned saw layers, sub-bass thumps, resonant transients, soft clipping
3. **Soft**: Sine/triangle tones, gentle attacks, low-passed noise; muted and non-fatiguing
4. **Realistic**: Noise-based scuffs and impacts, resonant band-passes, pitch-dropped thumps

## Audio Specs

- 44,100 Hz, mono, 16-bit PCM WAV
- Peak normalized to −6 dBFS by default to prevent clipping
- DC offset removed
- 3 ms fade-in and 12 ms fade-out per sound
- OGG Vorbis quality 5; MP3 at 192 kbps

## Sounds

Each style includes 39 cues and 156 sounds across the 4 styles.

### Movement

| Category | Description | Sounds |
| --- | --- | --- |
| _Jump_ | Leaving the ground | `jump_01`, `jump_02` |
| _Walk_ | Rotate for footsteps | `walk_01`, `walk_02`, `walk_03`, `walk_04` |
| _Land_ | Touching down after a jump | `land_01`, `land_02` |
| _Dash_ | Quick dodge or sprint burst | `dash_01` |

### Combat

| Category | Description | Sounds |
| --- | --- | --- |
| _Hit_ | Light, medium, and heavy impacts | `hit_light`, `hit_medium`, `hit_heavy` |
| _Swing_ | Attack whooshes | `swing_01`, `swing_02` |
| _Shoot_ | Projectiles and laser fire | `shoot_01`, `shoot_02` |
| _Explosion_ | Blasts and heavy impacts | `explosion_01` |
| _Shield_ | Block, guard, or deflect | `shield_01` |
| _Alert_ | Enemy spotted or warning | `enemy_alert_01` |

### Items & Environment

| Category | Description | Sounds |
| --- | --- | --- |
| _Pickup_ | Coins, items, collectibles | `pickup_01`, `pickup_02` |
| _Powerup_ | Rising buff or upgrade sweep | `powerup_01` |
| _Heal_ | Restoring health or healing magic | `heal_01` |
| _Splash_ | Water entry or splash | `splash_01` |

### Player

| Category | Description | Sounds |
| --- | --- | --- |
| _Hurt_ | Player damage | `hurt_01`, `hurt_02` |
| _Death_ | Death / game-over stinger | `death_01` |

### UI & Outcomes

| Category | Description | Sounds |
| --- | --- | --- |
| _UI_ | Menus, buttons, and alerts | `ui_click_01`, `ui_hover_01`, `ui_confirm_01`, `ui_back_01`, `ui_error_01`, `ui_open_01`, `ui_close_01`, `ui_notification_01` |
| _Victory_ | Win / level complete | `victory_01` |
| _Defeat_ | Loss / round over | `defeat_01` |
| _Level Up_ | Character or skill progression | `level_up_01` |
| _Achievement_ | Unlocks, trophies, and rewards | `achievement_01` |

## Generate

You can also generate the game sounds locally.

Clone the repository:

```sh
git clone https://github.com/remarkablegames/game-sounds.git && cd game-sounds
```

Install the requirements:

- Python 3.10+
- FFmpeg with `libvorbis` and `libmp3lame` (only for OGG and MP3)

Generate the full pack, including WAV, OGG, and MP3:

```sh
python3 generate.py
```

Generate one style as WAV only:

```sh
python3 generate.py --style retro --format wav
```

Use a fixed seed or adjust the master level:

```sh
python3 generate.py --seed 42 --db -1
```

Verify the output:

```sh
python3 generate.py --check
```

Explore the [source on GitHub](https://github.com/remarkablegames/game-sounds) or [preview every sound](https://remarkablegames.org/game-sounds/).

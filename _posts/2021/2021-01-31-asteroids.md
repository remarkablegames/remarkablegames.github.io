---
layout: post
title: Asteroids
date: 2021-01-31 19:54:39
updated: 2021-02-20 12:24:46
excerpt: How to create an asteroids game from p5.play examples with less than 150 lines of code.
categories: asteroids p5.play p5.js javascript web
image: https://remarkablegames.org/asteroids/screenshot.png
---

## Game

[Asteroids](https://remarkablegames.org/asteroids/) clone from [p5.play examples](https://b.remarkabl.org/2YS6LZz). See [Replit](https://replit.com/@remarkablemark/asteroids) and [repository](https://github.com/remarkablegames/asteroids).

<iframe src="https://remarkablegames.org/asteroids/" frameBorder="0" width="100%" height="600px"></iframe>

## Livestream

I recreated the asteroids game from [p5.play](https://b.remarkabl.org/p5play) examples in my [2021-02-06 livestream](https://youtu.be/q-p5lZsv3LQ?list=PLVgOtoUBG2mdLpj6qT5DXfg5_pGPTDrJZ):

<iframe width="100%" height="720" src="https://www.youtube.com/embed/q-p5lZsv3LQ?list=PLVgOtoUBG2mdLpj6qT5DXfg5_pGPTDrJZ" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Code

Load the [images](https://github.com/remarkablegames/asteroids/tree/gh-pages/assets) with [`loadImage()`](https://p5js.org/reference/#/p5/loadImage) in [`preload()`](https://p5js.org/reference/#/p5/preload):

```js
var shipImage;
var bulletImage;
var particleImage;
var asteroidImages = [];

function preload() {
  shipImage = loadImage('assets/asteroids_ship0001.png');
  bulletImage = loadImage('assets/asteroids_bullet.png');
  particleImage = loadImage('assets/asteroids_particle.png');

  for (var i = 0; i < 3; i++) {
    var asteroidImage = loadImage('assets/asteroid' + i + '.png');
    asteroidImages.push(asteroidImage);
  }
}
```

Use [`createCanvas()`](https://p5js.org/reference/#/p5/createCanvas) to create a canvas of 800px width by 600px height in [`setup()`](https://p5js.org/reference/#/p5/setup):

```js
function setup() {
  createCanvas(800, 600);
}
```

Create a ship sprite using `createSprite()`:

```js
function setup() {
  // ...
  ship = createSprite(width / 2, height / 2);
  ship.maxSpeed = 6;
  ship.friction = 0.01;
  ship.addImage('normal', shipImage);
  ship.addAnimation(
    'thrust',
    'assets/asteroids_ship0002.png',
    'assets/asteroids_ship0007.png'
  );
}
```

Replace the label identifiers for [`addImage()`](https://molleindustria.github.io/p5.play/docs/classes/Sprite.html#method-addImage) and [`addAnimation()`](https://molleindustria.github.io/p5.play/docs/classes/Sprite.html#method-addAnimation) with constants:

```diff
+var SHIP_NORMAL = 'normal';
+var SHIP_THRUST = 'thrust';

 function setup() {
   // ...
-  ship.addImage('normal', shipImage);
+  ship.addImage(SHIP_NORMAL, shipImage);
   ship.addAnimation(
-    'thrust',
+    SHIP_THRUST,
     'assets/asteroids_ship0002.png',
     'assets/asteroids_ship0007.png'
   );
 }
```

In [`draw()`](https://p5js.org/reference/#/p5/draw), set the [`background()`](https://p5js.org/reference/#/p5/background) to black and draw the ship with `drawSprites()`:

```js
function draw() {
  background(0);
  drawSprites();
}
```

Rotate the ship on `keyDown()` for the [`LEFT_ARROW`](https://p5js.org/reference/#/p5/LEFT_ARROW) and [`RIGHT_ARROW`](https://p5js.org/reference/#/p5/RIGHT_ARROW) keys:

```js
function draw() {
  // ...
  if (keyDown(LEFT_ARROW)) {
    ship.rotation -= 4;
  }
  if (keyDown(RIGHT_ARROW)) {
    ship.rotation += 4;
  }
  // ...
}
```

Move the ship forward and change the animation on `keyDown()` for the [`UP_ARROW`](https://p5js.org/reference/#/p5/UP_ARROW) key:

```js
function draw() {
  // ...
  if (keyDown(UP_ARROW)) {
    ship.addSpeed(0.2, ship.rotation);
    ship.changeAnimation(SHIP_THRUST);
  } else {
    ship.changeAnimation(SHIP_NORMAL);
  }
  // ...
}
```

Fire a bullet when `keyWentDown()` for the `x` key is triggered:

```js
function draw() {
  // ...
  if (keyWentDown('x')) {
    var bullet = createSprite(ship.position.x, ship.position.y);
    bullet.addImage(bulletImage);
    bullet.setSpeed(10 + ship.getSpeed(), ship.rotation);
    bullet.life = 30;
  }
  // ...
}
```

Prevent bullet firing when the player is dead:

```diff
 function draw() {
   // ...
-  if (keyWentDown('x')) {
+  if (!ship.removed && keyWentDown('x')) {
     // ...
   }
   // ...
 }
```

> The difference between `keyDown()` and `keyWentDown()` is that the former can be held (ship moves continuously) while the latter can only be triggered once (bullet is fired during release and press).

The [`life`](https://molleindustria.github.io/p5.play/docs/classes/Sprite.html#prop-life) property ensures that the bullet gets removed after a certain amount of time.

Create [groups](https://molleindustria.github.io/p5.play/docs/classes/Group.html) for bullets and asteroids:

```js
var asteroids;
var bullets;

function setup() {
  // ...
  asteroids = new Group();
  bullets = new Group();
}
```

Add the bullet to the bullets group:

```js
function draw() {
  // ...
  if (keyWentDown('x')) {
    // ...
    bullets.add(bullet);
  }
  // ...
}
```

Add a helper function that creates an asteroid:

```js
function createAsteroid(type, x, y) {
  var asteroid = createSprite(x, y);
  var image = asteroidImages[floor(random(0, 3))];
  asteroid.addImage(image);
  asteroid.setSpeed(2.5 - type / 2, random(360));
  asteroid.rotationSpeed = 0.5;
  asteroid.type = type;

  if (type === 2) {
    asteroid.scale = 0.6;
  }
  if (type === 1) {
    asteroid.scale = 0.3;
  }

  asteroid.mass = 2 + asteroid.scale;
  asteroid.setCollider('circle', 0, 0, 50);
  asteroids.add(asteroid);
  return asteroid;
}
```

The image is randomized and the properties are set. The custom property `type` keeps track of the large (3), medium (2), and small (1) asteroid sizes. [`setCollider()`](https://molleindustria.github.io/p5.play/docs/classes/Sprite.html#method-setCollider) sets the bounding box or circle for collision detection.

Create 8 asteroids in random positions outside of the canvas view:

```js
function setup() {
  // ...
  for (var i = 0; i < 8; i++) {
    var angle = random(360);
    var x = width / 2 + 1000 * cos(radians(angle));
    var y = height / 2 + 1000 * sin(radians(angle));
    createAsteroid(3, x, y);
  }
}
```

To make the asteroids show up, reset the sprites positions when they're out of bounds:

```js
var MARGIN = 40;

function draw() {
  // ...
  for (var i = 0; i < allSprites.length; i++) {
    var sprite = allSprites[i];
    if (sprite.position.x < -MARGIN) {
      sprite.position.x = width + MARGIN;
    }
    if (sprite.position.x > width + MARGIN) {
      sprite.position.x = -MARGIN;
    }
    if (sprite.position.y < -MARGIN) {
      sprite.position.y = height + MARGIN;
    }
    if (sprite.position.y > height + MARGIN) {
      sprite.position.y = -MARGIN;
    }
  }
  // ...
}
```

This ensures that all sprites remains in the canvas view (e.g., if a ship goes out of bounds while moving up, the position gets reset to the bottom).

Handle [`overlap()`](https://molleindustria.github.io/p5.play/docs/classes/Sprite.html#method-overlap) between asteroids and ship/bullets:

```js
function draw() {
  // ...
  asteroids.overlap(ship, asteroidHit);
  asteroids.overlap(bullets, asteroidHit);
  // ...
}

function asteroidHit(asteroid, sprite) {
  if (sprite.removed) {
    return;
  }

  var newType = asteroid.type - 1;

  if (newType > 0) {
    createAsteroid(newType, asteroid.position.x, asteroid.position.y);
    createAsteroid(newType, asteroid.position.x, asteroid.position.y);
  }

  sprite.remove();
  asteroid.remove();
}
```

Create particles when an asteroid gets hit by a ship or bullet:

```js
function asteroidHit(asteroid, sprite) {
  // ...
  for (var i = 0; i < 10; i++) {
    var particle = createSprite(sprite.position.x, sprite.position.y);
    particle.addImage(particleImage);
    particle.setSpeed(random(3, 5), random(360));
    particle.friction = 0.01;
    particle.life = 15;
  }
  // ...
}
```

Display the text instructions for player controls:

```js
function draw() {
  // ...
  drawSprites();

  fill(255);
  textAlign(CENTER);
  text('Controls: Arrow Keys + X', width / 2, 20);
}
```

> Render the text instructions last so the layer is in front of the background and sprites.

To debug collisions between sprites, enable the sprite property [`debug`](https://molleindustria.github.io/p5.play/docs/classes/Sprite.html#prop-debug):

```js
ship.debug = true;
```

This goes over how to make the asteroids game from p5.play. You can make further improvements like adding a title and game over screen and improving the physics and mechanics.

Check out the [Replit](https://b.remarkabl.org/36ONQU6) from the livestream for the full code.

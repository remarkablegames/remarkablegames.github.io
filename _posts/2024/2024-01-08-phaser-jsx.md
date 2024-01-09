---
layout: post
title: Phaser JSX
date: 2024-01-08 23:08:01
excerpt: Use [JSX](https://facebook.github.io/jsx/) in [Phaser](https://phaser.io/) with [`phaser-jsx`](https://github.com/remarkablegames/phaser-jsx).
categories: phaser-jsx npm
---

## What

[`phaser-jsx`](https://github.com/remarkablegames/phaser-jsx) allows you to use [JSX](https://facebook.github.io/jsx/) in [Phaser](https://phaser.io/).

## Why

I created this package to solve a personal pain point of mine—creating user interfaces in Phaser.

Currently, to add a text to a Phaser scene, you'd do something like this:

```js
this.add.text(0, 0, 'Hello, world!');
```

Not so bad, right? But imagine you're building a dialog modal with multiple shapes and event listeners:

```js
const button = this.add.rectangle(/* ... */);
button.setInteractive();
button.on('pointerdown', () => {
  // ...
});
```

Now things get hairy.

Given my experience with [React](https://react.dev/), I really enjoyed how the framework made _imperative_ programming **_declarative_**. So to make this possible in Phaser, I created [phaser-jsx](https://www.npmjs.com/package/phaser-jsx).

## How

Install the npm package:

```sh
npm install phaser-jsx
```

Enable JSX syntax by setting `jsxImportSource` to `phaser-jsx` in your build config like TypeScript:

```json
{
  "compilerOptions": {
    "jsx": "react-jsx",
    "jsxImportSource": "phaser-jsx"
  }
}
```

Now you can use JSX in files with the extension `.jsx` or `.tsx`:

```jsx
// game.jsx
import Phaser from 'phaser';
import { Text, render } from 'phaser-jsx';

new Phaser.Game({
  scene: {
    create() {
      render(<Text text="Hello, world!" />, this);
    },
  },
});
```

This means you can refactor your UI to the following:

{% raw %}

```jsx
import { Rectangle, Text } from 'phaser-jsx';

function Button() {
  return (
    <Rectangle onPointerDown={(pointer) => console.log('Clicked!')}>
      <Text
        text="Button"
        style={{ fontSize: 18 }}
        ref={(text) => console.log(text)}
      />
    </Rectangle>
  );
}
```

{% endraw %}

Nice, right?

Let me know what you think. I'm open to feedback and ideas. [Pull requests](https://github.com/remarkablegames/phaser-jsx) are welcome!

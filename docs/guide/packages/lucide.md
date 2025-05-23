# Lucide

Implementation of the lucide icon library for web applications.

## Installation

### Package Managers

::: code-group

```sh [pnpm]
pnpm install lucide
```

```sh [yarn]
yarn add lucide
```

```sh [npm]
npm install lucide
```

```sh [bun]
bun add lucide
```

:::

### CDN

```html
<!-- Development version -->
<script src="https://unpkg.com/lucide@latest/dist/umd/lucide.js"></script>

<!-- Production version -->
<script src="https://unpkg.com/lucide@latest"></script>
```

## Usage

### With unpkg

Here is a complete example with unpkg

```html
<!DOCTYPE html>
<body>
  <i data-lucide="volume-2" class="my-class"></i>
  <i data-lucide="x"></i>
  <i data-lucide="menu"></i>

  <script src="https://unpkg.com/lucide@latest"></script>
  <script>
    lucide.createIcons();
  </script>
</body>
```

### With ESModules

To reduce bundle size, lucide is built to be fully tree-shakable.
The `createIcons` function will search for HTMLElements with the attribute `data-lucide` and replace it with the svg from the given icon name.

```html
<!-- Your HTML file -->
<i data-lucide="menu"></i>
```

```js
import { createIcons, icons } from 'lucide';

// Caution, this will import all the icons and bundle them.
createIcons({ icons });

// Recommended way, to include only the icons you need.
import { createIcons, Menu, ArrowRight, Globe } from 'lucide';

createIcons({
  icons: {
    Menu,
    ArrowRight,
    Globe
  }
});
```

## Advanced Usage

### Additional Options

In the `createIcons` function you can pass some extra parameters to adjust the `nameAttr` or add custom attributes like for example classes.

Here is a full example:

```js
import { createIcons } from 'lucide';

createIcons({
  attrs: {
    class: ['my-custom-class', 'icon'],
    'stroke-width': 1,
    stroke: '#333'
  },
  nameAttr: 'data-lucide' // attribute for the icon name.
});
```

### Treeshake the library, only use the icons you use

```js
import { createIcons, Menu, ArrowRight, Globe } from 'lucide';

createIcons({
  icons: {
    Menu,
    ArrowRight,
    Globe
  }
});
```

### Custom Element binding

```js
import { createElement, Menu } from 'lucide';

const menuIcon = createElement(Menu); // Returns HTMLElement (svg)

// Append HTMLElement in the DOM
const myApp = document.getElementById('app');
myApp.appendChild(menuIcon);
```

#### Custom Element binding with custom attributes

```js
import { createElement, Menu } from 'lucide';

const menuIcon = createElement(Menu, {
  class: ['my-custom-class', 'icon'],
  'stroke-width': 1,
  stroke: '#333'
}); // Returns HTMLElement (svg)

// Append HTMLElement in the DOM
const myApp = document.getElementById('app');
myApp.appendChild(menuIcon);
```

### With Lucide lab or custom icons

[Lucide lab](https://github.com/lucide-icons/lucide-lab) is a collection of icons that are not part of the Lucide main library.
They can be used in the same way as the official icons.

```js
import { coconut } from '@lucide/lab';

createIcons({
  icons: {
    coconut
  }
});
```

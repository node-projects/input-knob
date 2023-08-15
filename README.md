# `<node-projects-input-knob>` ⟳ custom element

A rotating, touch-sensitive knob that you can use like an
`<input type="range">`.

## Install

The `dist` directory contains the ES module (`input-knob.js` that you can use directly.

Install [via npm](https://www.npmjs.com/package/@node-projects/input-knob) and include via the
bundler of your choice:

```sh
npm install --save @node-projects/input-knob
```

Include via unpkg:

```html
<script src="https://unpkg.com/@node-projects/input-knob"></script>
```

## Usage

This will create a knob with a minimum value of zero, a maximum of 100, a
current value of 50, and each full turn of the knob will change the value by 10.

```html
<node-projects-input-knob value="50" scale="10" min="0" max="100"></node-projects-input-knob>
```

- `value`: Current value, this will update as the knob is turned. Optional,
  defaults to `0`.
- `scale`: The change in the value for one full turn. Optional, defaults to `1`.
- `min`: Minimum allowed value. Optional, defaults to `null`.
- `max`: Maxium allowed value. Optional, defaults.to `null`.

If both `min` and `max` are set, then the knob can be turned multiple times to
reach a different `value`. If only one or none of `min` or `max` is set, then a
full turn of the knob will reset the value to `0`.

These are also exposed as properties on the object and can be set or observed in
JavaScript:

```javascript
const knob = document.querySelector('node-projects-input-knob');
knob.value = 42;
```

### Events

Three event types are dispatched for each point in an interaction:

- `knob-move-start`: fired on initial touch or click.
- `knob-move-change`: fired repeatedly for each change in rotation.
- `knob-move-end`: fired when the touch or click is released.

### Style and appearance

There are two key parts of the element that can be styled. The `<node-projects-input-knob>`
element itself, which is the container for the inner `rotator` part. The
`rotator` is accessed using the `::part(rotator)` pseudo-element. The outer
element does not rotate, so can be used for general positioning or changing the
appearance of the outer container. The inner `rotator` represents the part of
the knob the user interacts with and will rotate as the `value` changes.

Content inside the `<node-projects-input-knob>` tag will also rotate and can be used to do
things like provide a top marker for the knob.

```html
<style>
  node-projects-input-knob {
    width: 150px;
    padding: 10px;
    border: 2px dashed green;
    background: lightgreen;
  }

  node-projects-input-knob::part(rotator) {
    box-sizing: border-box;
    background: lightblue;
    border: 2px dashed blue;
    border-radius: 100%;
    width: 150px;
    height: 150px;
  }

  .mark {
    display: inline-block;
    width: 100%;
    text-align: center;
    font: bold 200% monospace;
    color: blue;
  }
</style>

<node-projects-input-knob value="50" scale="10" min="0" max="100">
  <div class="mark">▲</div>
</node-projects-input-knob>
```

![A blue knob with an upward tick on a green background](https://cdn.glitch.com/c3562722-7678-47b4-a7c3-5c26e9bc59ef%2Fstyled-knob.png?v=1566478423169)

## Demo

Try the demo at https://input-knob.glitch.me

![An example of <input-knob> in green with an upward tick indicator and slider below](https://cdn.glitch.com/c3562722-7678-47b4-a7c3-5c26e9bc59ef%2Fintpu-knob-example.png?v=1566478428792)


# Contributing

Issues and pull requests happily received. Please see
[CONTRIBUTING.md](CONTRIBUTING.md).

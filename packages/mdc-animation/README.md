<!--docs:
title: "Animation"
layout: detail
section: components
excerpt: "Animation timing curves and utilities for smooth and consistent motion."
iconId: animation
path: /catalog/animation/
-->

# Animation

Material in motion is responsive and natural. Use these easing curves and duration patterns to create smooth and consistent motion.

## Design & API Documentation

<ul class="icon-list">
  <li class="icon-list-item icon-list-item--spec">
    <a href="https://material.io/guidelines/motion/duration-easing.html">Material Design guidelines: Duration & easing</a>
  </li>
</ul>

## Installation

```
npm install --save @material/animation
```

## Usage

### Sass Variables, Mixins + Rules

| Variable | Description |
| --- | --- |
| `mdc-animation-fast-out-slow-in-timing-function` | Animations that are visible from start to finish (e.g. a FAB transforming into a toolbar) |
| `mdc-animation-linear-out-slow-in-timing-function` | Animations that cause objects to enter the screen (e.g. a fade in) |
| `mdc-animation-fast-out-linear-in-timing-function` | Animations that cause objects to leave the screen (e.g. a fade out) |

All animation variables are marked with `!default`, thus they can be overridden should the need
arise.

| Mixin | Description |
| --- | --- |
| `mdc-animation-linear-out-slow-in` | Animations that are visible from start to finish |
| `mdc-animation-fast-out-slow-in` | Animations that cause objects to enter the screen |
| `mdc-animation-fast-out-linear-in` | Animations that cause objects to leave the screen |


MDC Animation also provides helper functions for defining transitions for when something enters and exits the frame. A very common example of this is something that fades in and then fades out using opacity.

```scss
@import "@material/animation/functions";

.mdc-thing {
  transition: mdc-animation-exit(/* $name: */ opacity, /* $duration: */ 175ms, /* $delay: */ 150ms);
  opacity: 0;
  will-change: opacity;

  &:active {
    transition: mdc-animation-enter(opacity, 175ms /*, $delay: 0ms by default */);
    opacity: 1;
  }
}
```

Note that these functions also work with the `animation` property.

```scss
@import "@material/animation/functions";

@keyframes fade-in {
  from {
    transform: translateY(-80px);
    opacity: 0;
  }

  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.mdc-thing {
  animation: mdc-animation-enter(fade-in, 350ms);
}
```

### CSS Classes

| CSS Class | Description |
| --- | --- |
| `mdc-animation-linear-out-slow-in` | Animations that are visible from start to finish |
| `mdc-animation-fast-out-slow-in` | Animations that cause objects to enter the screen |
| `mdc-animation-fast-out-linear-in` | Animations that cause objects to leave the screen |

### Utility JavaScript Functions

| Method Signature | Description |
| --- | --- |
| `getCorrectEventName(windowObj: Object, eventType: string)` | Returns a JavaScript event name. Prefixed if necessary. |
| `getCorrectPropertyName(windowObj: Object, eventType: string)` | Returns a CSS property name. Prefixed if necessary. |

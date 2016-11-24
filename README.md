# vue-throttle-event

> throttle events based on requestAnimationFrame

## Features

- Uses [requestAnimationFrame](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame)
- Exposes an istance method called `$throttle` in every Vue Component
- Fires a [CustomEvent](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent) when ready

## Installation

### npm
```
$ npm install vue-throttle-event --save-dev
```

### Vue's main.js
```js
import VueThrottleEvent from 'vue-throttle-event'

Vue.use(VueThrottleEvent)
```

## Usage

### Example
```js
methods: {
  customEventHandler () {
    // logic here..
  }
}
created () {
  this.$throttle('mousemove', 'mouse-moved-throttled', this.$el)
  this.$on('mouse-moved-throttled', this.customEventHandler)
}
```

### Arguments
- type (String): the event [type](https://developer.mozilla.org/en-US/docs/Web/Events)
- customEventName (String): the custom event name that will be fired on next requestAnimationFrame
- targetObject (Object) [optional]: the physical [EventTarget](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget) where the [CustomEvent](https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent)  will be fired, defaults on [window](https://developer.mozilla.org/en-US/docs/Web/API/Window)
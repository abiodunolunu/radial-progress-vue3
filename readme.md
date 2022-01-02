# radial-progress-vue3

A simple, highly customizable, and easy to use radial progress bar.

[![npm](https://img.shields.io/npm/dt/radial-progress-vue3)](https://www.npmjs.com/package/radial-progress-vue3)

## Features

- can be clockwise or counter-clockwise
- colors can be customized

## Installation and usage

---

```bash
npm install radial-progress-vue3
```

You can register it globally like this:

```javascript
import { createApp } from "vue";
import App from "./App.vue";
import radialProgessVue3 from "radial-progress-vue3";

const app = createApp(App);

app.component("radial-progress-vue3", radialProgessVue3);
```

Alternatively, you can register it locally:

```vue
<!-- your-component.vue -->

<template>
  <radial-progress-vue3
    :percent="50"
    :stroke-width="10"
    :stroke-color="'#ff0000'"
    :fill-color="'#00ff00'"
  ></radial-progress-vue3>
</template>

<script>
import { defineComponent } from "vue";

import radialProgessVue3 from "radial-progress-vue3";

export default defineComponent({
  components: {
    radialProgessVue3,
  },
});
</script>
```

### Browser with cdn

```html
<script src="https://unpkg.com/vue@3.0.0"></script>

<script src="https://unpkg.com/radial-progress-vue3@latest/dist/radial-progress-vue3.min.js"></script>
```

```javascript
const { createApp } = Vue;

const App = {
  // component code
};

const app = createApp(App);

app.component("radial-progress-vue3", radialProgessVue3);
app.mount("#app");
```

You can customize the component by passing the following `props`:

### Props

| Prop              | Description                                                                | Type             | Default |
| ----------------- | -------------------------------------------------------------------------- | ---------------- | ------- |
| percent           | This is the percentage of the progress                                     | Number           | 42      |
| width             | The width & height of the viewBox                                          | Number           | 80      |
| strokeWidth       | This is the width of the stroke (like a border)                            | Number           | 6       |
| strokeColor       | This is the color of the stroke (can be rgb, hsl, hex, rgba)               | String           | #2e5090 |
| innerStrokeColor  | This is the color of the innerStroke (can be rgb, hsl, hex, rgba)          | String           | #ffaadd |
| fillColor         | This is the background color of the component (can be rgb, hsl, hex, rgba) | String           | #E6E6FA |
| roundedStroke     | This determines if the stroke has rounded edges or flat edges              | Boolean          | false   |
| showText          | This determines whether to show the progress in a text                     | Boolean          | true    |
| textColor         | Color of the text (if `showText` is `true`), (can be rgb, hsl, hex, rgba)  | String           | #222222 |
| fontWeight        | font weight of the text (if `showText` is `true`)                          | String Or Number | 700     |
| fontSize          | font size of the text (if `showText` is `true`) , it is in pixels          | Number           | 12      |
| showPercentSymbol | This determines if `%` is show in the text                                 | Boolean          | true    |
| clockWise         | This determines if the progress is clockwise or counter-clockwise          | Boolean          | true    |

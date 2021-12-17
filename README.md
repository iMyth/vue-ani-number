# vue-ani-number

A Vue 3 component, provide a convenient and light-weight number animation.
## Demo

TBA

### Requirements

* vue.js 3.x

### Installation
```
yarn add vue-ani-number
```

or 
```
npm install vue-ani-number
```

### Usage

* use plugin
``` ts
import { createApp } from 'vue';
import App from './App.vue';
import VueAniNumber from 'vue-ani-number'

createApp(App).use(VueAniNumber).mount('#app');
```

* animation would be triggered by number changes

``` html
<template>
  <vue-ani-number :number="number" />
</template>
```

``` js
export default {
  name: "App",
  data() {
    return {
      number: 0
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.number = 88888
      window.setTimeout(() => {
        this.number = 545876
      }, 5000)
    })
  }
};

```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

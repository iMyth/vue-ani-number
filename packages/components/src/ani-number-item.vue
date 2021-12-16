<template>
  <div class="ani-number-item">
    <span :style="spanStyle">0123456789</span>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ani-number-item',
  props: {
    number: {
      type: Number,
      default: () => 0
    }
  },
  setup() {
    return {};
  },

  computed: {
    spanStyle() {
      return { transform: `translateY(-${this.number * 10}%)` };
    }
  }
});
</script>

<style lang="less">
@import './ani-number-item.less';
</style>

<template>
  <div class="ani-number-groups">
    <AniNumberItem v-for="(item, index) in childNumber" :key="index" :number="item" />
  </div>
</template>

<script lang="ts">
import { defineComponent, nextTick, onMounted, watch, ref } from 'vue';
import AniNumberItem from './ani-number-item.vue';

export default defineComponent({
  name: 'vue-ani-number',
  components: { AniNumberItem },
  props: {
    number: {
      type: Number,
      default: 0
    }
  },

  setup(props) {
    const childNumber = ref([] as Array<number | string>);
    const animate = (v: number) => {
      const numStr = String(v);
      const length = numStr.length;
      if (childNumber.value.length !== length) {
        childNumber.value = new Array(length).fill(0);
      }

      nextTick(() => {
        childNumber.value = numStr.split('').map((p) => +p);
      });
    };

    onMounted(() => {
      animate(props.number);
    });

    watch(
      () => props.number,
      (v) => {
        animate(v);
      }
    );

    return {
      childNumber,
      animate
    };
  }
});
</script>

<style lang="less">
@import './ani-number-groups.less';
</style>

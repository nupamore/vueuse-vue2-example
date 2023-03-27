<template>
  <div id="app">
    <h3>Mouse: {{ x }} x {{ y }}</h3>
    <h3>
      Counter: {{ count }}
      <button @click="inc()" style="margin-right: 10px">+</button>
      <button @click="dec()">-</button>
    </h3>
    <h3>
      <input type="text" v-model="input" />
      <p>{{ output }}</p>
    </h3>
  </div>
</template>

<script>
import { defineComponent, ref, watch } from "vue";
import { useMouse, useCounter, watchDebounced } from "@vueuse/core";

export default defineComponent({
  setup() {
    const { x, y } = useMouse();
    const { count, inc, dec } = useCounter();

    const input = ref("");
    const output = ref("");
    watch(input, () => {
      output.value = input.value;
    });

    return {
      x,
      y,
      count,
      inc,
      dec,
      input,
      output,
    };
  },
});
</script>

<style scoped></style>

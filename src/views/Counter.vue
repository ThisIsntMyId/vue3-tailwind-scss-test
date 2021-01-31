<template>
  <div class="bg-blue-100 p-10">
    {{ count }}
    <button @click="count++">inc</button>
    <button @click="count--">dec</button>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const state = reactive({
      count: 0
    });

    return {
      ...toRefs(state)
    };
  }
};
</script>

<style lang="scss" scoped></style>

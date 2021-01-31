<template>
  <div class="bg-blue-100 p-10">
    <div class="m-2 text-4xl">
      {{ count }}
    </div>
    <button
      class="border border-blue-900 hover:bg-blue-900 hover:text-white rounded p-2 m-3"
      @click="count++"
    >
      inc
    </button>
    <button
      class="border border-blue-900 hover:bg-blue-900 hover:text-white rounded p-2 m-3"
      @click="count--"
    >
      dec
    </button>
    <button
      class="border border-blue-900 hover:bg-blue-900 hover:text-white rounded p-2 m-3"
      @click="count = count * multiplier"
    >
      mul
    </button>
    <div class="m-3">
      <input
        type="text"
        class="border p-2 text-black font-black"
        :class="{ 'text-red-500': inputError }"
        v-model="multiplier"
      />
      <p v-if="inputError" class="text-red-500 mt-2">
        multiplier should be a number between 1-100
      </p>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs, computed } from "vue";

export default {
  setup() {
    const state = reactive({
      count: 0,
      multiplier: 1
    });

    const inputError = computed(() => {
      const validMultiplierInput =
        /^\d+$/g.test(state.multiplier) &&
        parseInt(state.multiplier) > 0 &&
        parseInt(state.multiplier) < 100;
      return !validMultiplierInput;
    });

    return {
      ...toRefs(state),
      inputError
    };
  }
};
</script>

<style lang="scss" scoped></style>

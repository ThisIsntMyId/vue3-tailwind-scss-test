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
  <div>
    <h1>Sass Block</h1>
    <div class="sass-block">
      <h2 class="sass-block__title">
        Lorem ipsum dolor sit.
      </h2>
      <p class="sass-block__content">
        Lorem ipsum dolor sit amet consectetur, adipisicing elit.
        Exercitationem, laudantium? Sapiente, modi enim rem itaque laudantium
        accusantium! Consectetur vitae labore fuga aliquid fugit nesciunt enim.
        Culpa nisi ad quas totam voluptate dicta accusantium commodi minus dolor
        laudantium placeat quae explicabo, numquam doloribus facere cum pariatur
        dignissimos quam impedit eligendi voluptates?
      </p>
      <img
        src="https://www.rd.com/wp-content/uploads/2020/07/35_No-regrets-1.jpg"
        alt="sailor moon cosplay"
        class="sass-block__img"
      />
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

<style lang="scss" scoped>
.sass-block {
  padding: 500px 100px;
  background: rgb(224, 203, 175);
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-areas:
    "header header header"
    "body body image";

  &__title {
    font-size: 20px;
    font-weight: 900;
    grid-area: header;
  }
  &__content {
    line-height: 2rem;
    font-weight: normal;
    font-size: 1.2rem;
    grid-area: body;
  }

  &__img {
    display: block;
    height: 300px;
    width: 300px;
    grid-area: image;
  }
}
</style>

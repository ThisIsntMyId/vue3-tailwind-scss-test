<template>
  <div class="home">
    <h1>Home - Counter</h1>
    <Counter />
  </div>
</template>

<script>
// @ is an alias to /src
import Counter from "@/views/Counter.vue";

export default {
  name: "Home",
  components: {
    Counter
  }
};
</script>

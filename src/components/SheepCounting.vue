<script>
import One from "./One.vue";

export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {
    incrementCount() {
      this.count += 1;
    },
  },
  components: {
    One,
  },
};
</script>

<template>
  <div class="counter">
    <h2>Current Count: {{ count }}</h2>
    <button @click="incrementCount">Count a Sheep</button>
  </div>
  <One />
</template>

<style scoped>
.counter {
  margin-top: 2rem;
}
</style>

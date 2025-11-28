<script>
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
};
</script>

<template>
  <div class="counter">
    <h2>Current Count: {{ count }}</h2>
    <button @click="incrementCount">Count a Sheep</button>
  </div>
</template>

<style scoped>
.counter {
  margin-top: 2rem;
}
</style>

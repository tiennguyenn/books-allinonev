<script setup>
import { reactive } from "vue";

const state = reactive({
  count: 0,
});

function incrementCount() {
  state.count += 1;
}
</script>

<template>
  <div class="counter">
    <h2>Current Count: {{ state.count }}</h2>
    <button @click="incrementCount">Count</button>
  </div>
</template>

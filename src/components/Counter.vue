<script setup>
import { reactive, ref } from "vue";
import Test from "./Test.vue";

const state = reactive({
  count: 0,
});

const person = ref({
  name: "John Doe",
  age: 30,
});

function incrementCount() {
  state.count += 1;
  person.value.age += 1;
}
</script>

<template>
  <div class="counter">
    <h2>Current Count: {{ state.count }}</h2>
    <h3>Name {{ person.name }}, Age {{ person.age }}</h3>
    <button @click="incrementCount">Count</button>
    <Test name="Counter User" />
  </div>
</template>

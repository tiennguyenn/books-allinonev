<script setup>
import { onErrorCaptured } from "vue";
import ErrorButton from "./components/ErrorButton.vue";
import HelloWorld from "./components/HelloWorld.vue";
import Todo from "./components/Todo.vue";
import { reactive } from "vue";
import { ref } from "vue";

const err = ref(null);

onErrorCaptured((err) => {
  err.value = err.message;
});
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <Todo />
    <div v-if="err">
      There is an error {{ err }} <button @click="reserError">OK</button>
    </div>
    <ErrorButton />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

<script setup>
function throwError() {
  throw new Error("This is a test error");
}
</script>
<template>
  <h2>Error demand</h2>
  <button @click="throwError">Throw Error</button>
</template>

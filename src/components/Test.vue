<script setup>
defineProps(["name"]);
function getTime() {
  return new Date().getHours();
}
</script>
<template>
  <div>
    <p v-if="getTime() < 12">Good morning {{ name }}</p>
    <p v-else-if="getTime() < 19">Good evening</p>
    <p v-else>Good night</p>
  </div>
</template>

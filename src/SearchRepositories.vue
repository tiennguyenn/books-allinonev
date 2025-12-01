<script setup>
import { watch, ref } from "vue";

const searchTerm = ref("");
const searchResult = ref([]);

watch(searchTerm, async (term) => {
  if (term.length < 3) {
    return;
  }

  const response = await fetch(
    `https://api.github.com/search/repositories?q=${term}`
  );
  const data = await response.json();
  searchResult.value = data.items;
});
</script>
<template>
  <label>Search: </label>
  <input v-model="searchTerm" />
  <ul>
    <li v-for="repo in searchResult" :key="repo.name">
      <a :href="repo.html_url">{{ repo.name }}</a>
    </li>
  </ul>
</template>

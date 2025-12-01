<script setup>
import { computed, ref } from "vue";
const repos = ref([]);
const loading = ref(false);
const error = ref(null);
const stats = computed(() => {
  return {
    total: repos.value.length,
    stars: repos.value.reduce(
      (total, repo) => total + repo.stargazers_count,
      0
    ),
  };
});
function fetchRepos() {
  loading.value = true;
  fetch("https://api.github.com/users/vuejs/repos?per_page=10")
    .then((response) => {
      return response.json();
    })
    .then((data) => {
      repos.value = data;
      loading.value = false;
    })
    .catch((error) => {
      error.value = error;
      loading.value = false;
    });
}
</script>
<template>
  <h1>Vue's Repositories</h1>
  <button @click="fetchRepos">{{ loading ? "Loading" : "Fetch Repos" }}</button>
  <p v-if="error">{{ error.message }}</p>
  <p v-if="repos.length">
    Showing {{ stats.total }} repositories with a total of
    {{ stats.stars }} stars
  </p>
  <ul>
    <li v-for="repo in repos" :key="repo.name">
      <a :href="repo.html_url">{{ repo.name }}</a>
      <p>{{ repo.discription }}</p>
    </li>
  </ul>
</template>

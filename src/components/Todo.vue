<script setup>
import { onMounted, reactive } from "vue";
const state = reactive({
  todos: [],
  newTodo: "",
});

function addTodo() {
  state.todos.push({
    title: state.newTodo,
    done: false,
  });
  state.newTodo = "";
}

onMounted(() => {
  // Initial todos
  state.todos = [
    { title: "Learn Vue 3", done: false },
    { title: "Build a todo app", done: false },
  ];
});
</script>

<template>
  <div>
    <h2>Todo List</h2>
    <ul v-for="todo in state.todos">
      <li>
        <input type="checkbox" v-model="todo.done" />
        <span>{{ todo.title }}</span>
      </li>
    </ul>
    <input v-model="state.newTodo" />
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

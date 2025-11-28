<script>
import { onMounted, reactive } from "vue";
const vPlay = {
  mounted: (el) => {
    el.play();
  },
};
export default {
  setup() {
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

    return {
      state,
      addTodo,
    };
  },
  directives: {
    focus: {
      mounted(el) {
        el.focus();
      },
    },
    chars: {
      updated(el) {
        console.log(`Element has ${el.value.length} characters`);
      },
    },
  },
};
</script>

<template>
  <div>
    <h2>Todo List</h2>
    <ul v-for="todo in state.todos">
      <li>
        <input type="checkbox" v-model="todo.done" />
        <span v-text="todo.title" />
      </li>
    </ul>
    <input v-model="state.newTodo" v-focus v-chars />
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

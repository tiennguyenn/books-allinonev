<script>
import { onMounted, reactive } from "vue";
import Test from "./Test.vue";
import One from "./One.vue";
const vPlay = {
  mounted: (el) => {
    el.play();
  },
};
export default {
  props: ["name"],
  components: {
    One,
    Test,
  },
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
    <h2>Todo List {{ name }}</h2>
    <One />
    <ul v-for="todo in state.todos">
      <li>
        <input type="checkbox" v-model="todo.done" />
        <span v-text="todo.title" />
      </li>
    </ul>
    <input v-model="state.newTodo" v-focus v-chars />
    <button @click="addTodo">Add Todo</button>
    <h2>asdfadf</h2>
  </div>
</template>

<template>
  <div id="app">
    <h2>Todo application</h2>
    <router-link to="/">Home</router-link>
    <hr />
    <AddTodo @add-todo="addTodo" />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not Completed</option>
    </select>
    <hr />
    <Loader v-if="loading" />
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddTodo from "@/components/AddTodo";
import Loader from "@/components/Loader";
export default {
  name: "App",
  data() {
    return {
      todos: [
        { id: 1, title: "Buy bread", completed: false },
        {
          id: 2,
          title: "Buy butter",
          completed: false,
        },
        { id: 3, title: "Buy bear", completed: false },
      ],
      loading: true,
      filter: "all",
    };
  },
  components: {
    TodoList,
    AddTodo,
    Loader,
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=15")
      .then((response) => response.json())
      .then((json) => {
        setTimeout(() => {
          (this.todos = json), (this.loading = false);
        }, 1000);
      });
  },
  /*   watch: {
    filter(value) {
      console.log(value);
    },
  }, */
  computed: {
    filteredTodos() {
      if (this.filter === "all") return this.todos;

      if (this.filter === "completed")
        return this.todos.filter((t) => t.completed);

      if (this.filter === "not-completed")
        return this.todos.filter((t) => !t.completed);

      return this.todos;
    },
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((t) => t.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

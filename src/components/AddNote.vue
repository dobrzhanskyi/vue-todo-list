<template>
  <div>
    <form @submit.prevent="onSubmit">
      <div>
        <input type="text" v-model="title" />
        <input type="text" v-model="todo" />
        <button type="submit">Create</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  components: {},
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newNote = {
          id: Date.now(),
          title: this.title,
          todos: this.todo,
        };
        this.$emit("add-note", newNote);
        this.title = "";
      }
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input {
  width: 400px;
}
</style>

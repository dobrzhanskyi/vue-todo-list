<template>
  <div>
    <button class="ed">Edit</button>

    <button class="rm" v-on:click="$emit('remove-note', note.id)">
      Delete
    </button>
    <h2>{{ note.title }}</h2>
    <TodoList v-bind:todos="this.note.todos" />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
export default {
  props: {
    note: {
      Type: Object,
      required: true,
    },
    index: Number,
  },
  components: {
    TodoList,
  },
};
</script>

<style scoped>
.rm {
  background: red;
  color: black;
  border-radius: 50%;
  font-weight: bold;
  margin: 2em;
}
.ed {
  background: yellow;
  color: black;
  border-radius: 50%;
  font-weight: bold;
}
</style>

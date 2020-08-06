<template>
  <div>
    <h2>Notes</h2>
    <AddNote @add-note="addNote" />
    <NoteList v-bind:notes="this.notes" @remove-note="removeNote" />
    <!--  <Note v-bind:todos="this.todos" /> -->
    <!-- <router-link to="/todos">Todos</router-link> -->
  </div>
</template>

<script>
/* import Note from "@/components/Note"; */
import NoteList from "@/components/NoteList";
import AddNote from "@/components/AddNote";
export default {
  data() {
    return {
      notes: [
        {
          id: 1,
          title: "Title",
          todos: [
            { id: 1, title: "Buy bread", completed: false },
            {
              id: 2,
              title: "Buy butter",
              completed: false,
            },
            { id: 3, title: "Buy bear", completed: false },
          ],
        },
        {
          id: 2,
          title: "Title 2",
          todos: [
            { id: 1, title: "Buy milk", completed: false },
            {
              id: 2,
              title: "Buy ketchup",
              completed: false,
            },
            { id: 3, title: "Buy orange", completed: false },
          ],
        },
      ],
      loading: false,
      filter: "all",
    };
  },
  components: {
    NoteList,
    AddNote,
  },
  methods: {
    removeNote(id) {
      this.notes = this.notes.filter((n) => n.id !== id);
    },
    addNote(note) {
      this.notes.push(note);
    },
  },
};
</script>

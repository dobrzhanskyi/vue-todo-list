<template>
  <div class="notelist">
    <Note
      v-for="(note, i) in notes"
      v-bind:note="note"
      v-bind:index="i"
      :key="note.id"
      v-on:remove-note="removeNote"
    />
  </div>
</template>
<script>
import Note from "@/components/Note";
export default {
  props: ["notes"],
  methods: {
    removeNote(id) {
      this.$emit("remove-note", id);
    },
  },
  components: {
    Note,
  },
};
</script>
<style scoped>
.notelist {
  display: grid;
  grid-template-columns: 700px 700px;
  grid-row-gap: 10px;
  grid-column-gap: 20px;
}
* {
  box-sizing: border-box;
}

.notelist {
  /*  border: 2px solid #f76707; */
  border-radius: 5px;
  /*  background-color: #fff4e6; */
  padding: 3em;
}

.notelist > div {
  border: 2px solid #ffa94d;
  border-radius: 5px;
  background-color: #ffd8a8;
  padding: 4em;
  color: black;
  margin: 40 40 40 40;
}
</style>

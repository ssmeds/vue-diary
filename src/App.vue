<template>
  <div id="app">
    <AddNote @new-note="addNewNote" />
    <Notes @delete-note="deleteNote" :notes="notes" />
  </div>
</template>

<script>
import AddNote from "./components/AddNote.vue";
import Notes from "./components/Notes.vue";
export default {
  name: "App",
  components: {
    AddNote,
    Notes,
  },
  data() {
    return {
      notes: [],
    };
  },
  methods: {
    async deleteNote(id) {
      const data = await JSON.parse(localStorage.getItem("notes"));
      const notes = data.filter((note) => note.id !== id);
      localStorage.setItem("notes", JSON.stringify(notes));
      this.notes = this.notes.filter((note) => note.id !== id);
    },

    async addNewNote(note) {
      const data = await JSON.parse(localStorage.getItem("notes") || "[]");
      data.push(note);
      localStorage.setItem("notes", JSON.stringify(data));
      this.notes = [...this.notes, note];
    },
    async getNotes() {
      const data = await JSON.parse(localStorage.getItem("notes") || "[]");
      return data;
    },
  },
  async created() {
    console.log("created");
    this.notes = await this.getNotes();
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
  display: flex;
}
</style>

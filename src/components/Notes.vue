<template>
  <div class="notes">
    <div :key="note.id" v-for="note in notes" class="notes">
      <Note @delete-note="$emit('delete-note', note.id)" :note="note" />
    </div>
  </div>
</template>

<script>
import Note from "./Note";
export default {
  name: "Notes",
  props: {
    notes: Array,
  },
  components: {
    Note,
  },
  emits: ["delete-note"],
};
</script>

<style>
.notes {
  width: 500px;
}
</style>

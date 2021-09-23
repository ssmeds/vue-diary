<template>
  <div class="note">
    <h2>Rubrik: {{ note.headline }}</h2>
    <h3>
      Text:
      {{ note.text }}
      <i @click="$emit('delete-note', note.id)" class="fas fa-times"></i>
    </h3>
    <p>Datum: {{ note.date }}</p>
  </div>
</template>

<script>
export default {
  name: "Note",
  props: {
    note: Object,
  },
};
</script>

<style scoped>
.fas {
  color: red;
}
.note {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  max-width: 400px;
}

.note h2,
h3,
p {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
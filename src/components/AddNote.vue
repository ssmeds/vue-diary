<template>
  <form @submit="onSubmit">
    <input type="text" v-model="headline" placeholder="Rubrik" />
    <input type="date" v-model="date" />
    <textarea
      v-model="text"
      cols="30"
      rows="10"
      placeholder="Din dagboksanteckning"
    ></textarea>
    <button type="submit">Spara</button>
  </form>
</template>

<script>
export default {
  name: "AddNote",
  data() {
    return {
      headline: "",
      date: new Date().toISOString().substr(0, 10),
      text: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      console.log(e);
      const newNote = {
        id: Math.floor(Math.random() * 1000),
        headline: this.headline,
        date: this.date,
        text: this.text,
      };
      this.$emit("new-note", newNote);

      this.date = "";
      this.headline = "";
      this.text = "";
    },
  },
  emits: {},
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  margin: 2rem;
  max-width: 300px;
}
input,
textarea,
button,
input::placeholder,
textarea::placeholder {
  margin: 0.5rem;
  padding: 1rem 0.5rem;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-size: 1.1rem;
}
button {
  border: none;
  border-radius: 5px;
  outline: none;
  background: black;
  color: white;
  cursor: pointer;
  text-transform: uppercase;
}
</style>

<template>
  <header>
    <input v-model="inputFilm" type="text" />
    <button @click.prevent="$emit('cercaFilm', inputFilm)">
      cerca
    </button>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputFilm: "",
    };
  },
};
</script>

<style></style>

<template>
  <header>
    <input v-model="searchFilm" type="text" />
    <button @click.prevent="$emit('cercaFilm', searchFilm)">
      cerca
    </button>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchFilm: "",
    };
  },
};
</script>

<style></style>

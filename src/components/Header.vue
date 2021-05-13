<template>
  <header>
    <a href="https://fontmeme.com/netflix-font/"
      ><img
        src="https://fontmeme.com/permalink/210511/c072857f28ffed69c9266a55183f4c20.png"
        alt="netflix-font"
        border="0"
    /></a>
    <div class="search">
      <input
        :class="classe"
        v-model="inputFilm"
        type="text"
        @keyup="$emit('cercaFilm', inputFilm)"
        placeholder="Titolo, Film, Serie"
      />
      <i class="fas fa-search" @click="activeClass"></i>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputFilm: "",
      classe: "none",
    };
  },
  methods: {
    activeClass() {
      if (this.classe === "none") {
        this.classe = "active";
      } else {
        this.classe = "none";
      }
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/style/header.scss";
</style>

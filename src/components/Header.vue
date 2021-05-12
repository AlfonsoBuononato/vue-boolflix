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
        v-model="inputFilm"
        type="text"
        @keyup="$emit('cercaFilm', inputFilm)"
      />
      <button>
        cerca
      </button>
    </div>
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

<style scoped lang="scss">
@import "@/style/header.scss";
</style>

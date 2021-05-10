<template>
  <div id="app">
    <Header @cercaFilm="searchFilm()" />

    <Main :films="dataFilms" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiURL:
        "https://api.themoviedb.org/3/search/movie?api_key=cb3537543f166a0f6e6c859d2b931944&query=batman&language=it-IT",
      dataFilms: [],
      searchingFilm: "",
    };
  },
  created() {
    this.getArray();
  },
  methods: {
    getArray() {
      axios
        .get(this.apiURL)
        .then((res) => {
          this.dataFilms = res.data.results;
          console.log(this.dataFilms);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    searchFilm(testo) {
      console.log("ciao");
      this.searchingFilm = testo;
      console.log(this.searchingFilm);
    },
  },
};
</script>

<style lang="scss"></style>

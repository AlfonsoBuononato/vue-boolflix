<template>
  <div id="app">
    <Header @cercaFilm="searchFilm" />

    <Main :films="filteredFilm" :serie="filteredFilm" />
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
      /* SERIE */
      apiUrlSerie:
        "https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT&query=peaky blinders",
      dataSerie: [],
    };
  },
  computed: {
    filteredFilm() {
      if (this.searchingFilm === "") {
        return this.dataFilms && this.dataSerie;
      }
      return this.dataFilms.filter((element) => {
        return element.title
          .toLowerCase()
          .includes(this.searchingFilm.toLowerCase());
      });
    },
  },
  created() {
    this.getArray();
    this.getArraySerie();
  },
  methods: {
    getArray() {
      axios
        .get(this.apiURL)
        .then((res) => {
          this.dataFilms = res.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getArraySerie() {
      axios
        .get(this.apiUrlSerie)
        .then((res) => {
          this.dataSerie = res.data.results;
        })
        .catch((errore) => {
          console.log(errore);
        });
    },
    searchFilm(testo) {
      this.searchingFilm = testo;
    },
  },
};
</script>

<style lang="scss"></style>

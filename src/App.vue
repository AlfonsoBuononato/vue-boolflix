<template>
  <div id="app">
    <Header @cercaFilm="getArray" />
    <Trand :trand="dataTrand" />
    <Film :films="filteredFilm" />
    <Serie :serie="filteredSerie" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Film from "@/components/Film.vue";
import Serie from "@/components/Serie.vue";
import Trand from "@/components/Trand.vue";
export default {
  name: "App",
  components: {
    Header,
    Film,
    Serie,
    Trand,
  },
  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/movie",
      dataFilms: [],
      searchingFilm: "",
      /* SERIE */
      apiUrlSerie: "https://api.themoviedb.org/3/search/tv",
      dataSerie: [],
      /* API TRAND */
      apiTrand:
        "https://api.themoviedb.org/3/trending/movie/day?api_key=cb3537543f166a0f6e6c859d2b931944",
      dataTrand: [],
    };
  },
  created() {
    this.getArrayTrand();
  },
  computed: {
    filteredFilm() {
      if (this.searchingFilm === "") {
        return this.dataFilms;
      }

      return this.dataFilms.filter((element) => {
        return element.title
          .toLowerCase()
          .includes(this.searchingFilm.toLowerCase());
      });
    },
    filteredSerie() {
      if (this.searchingFilm === "") {
        return this.dataSerie;
      }

      return this.dataSerie.filter((element) => {
        return element.name
          .toLowerCase()
          .includes(this.searchingFilm.toLowerCase());
      });
    },
  },
  methods: {
    getArray(cerca) {
      axios
        .get(this.apiURL, {
          params: {
            api_key: "cb3537543f166a0f6e6c859d2b931944",
            query: cerca,
            language: "it-IT",
          },
        })
        .then((res) => {
          this.dataFilms = res.data.results;
          res.data.results.forEach((element) => {
            element.poster_path =
              "https://image.tmdb.org/t/p/" + "w185" + element.poster_path;

            element.vote_average = Math.ceil(element.vote_average / 2);
          });
        })
        .catch((error) => {
          console.log(error);
        });
      axios
        .get(this.apiUrlSerie, {
          params: {
            api_key: "cb3537543f166a0f6e6c859d2b931944",
            query: cerca,
            language: "it-IT",
          },
        })
        .then((res) => {
          this.dataSerie = res.data.results;
          res.data.results.forEach((element) => {
            element.poster_path =
              "https://image.tmdb.org/t/p/" + "w185" + element.poster_path;

            element.vote_average = Math.ceil(element.vote_average / 2);
          });
        })
        .catch((errore) => {
          console.log(errore);
        });
    },
    getArrayTrand() {
      axios
        .get(this.apiTrand)
        .then((res) => {
          this.dataTrand = res.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    searchFilm(testo) {
      this.searchingFilm = testo;
    },
  },
};
</script>

<style lang="scss">
@import "@/style/general.scss";
</style>

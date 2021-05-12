<template>
  <main v-show="films.length > 0">
    <div class="title">
      <h2>film</h2>
    </div>
    <div class="container">
      <div class="box" v-for="(element, index) in films" :key="index">
        <img :src="element.poster_path" alt="" />
        <ul>
          <li>Titotlo: {{ element.title }}</li>
          <li>Titolo originale: {{ element.original_title }}</li>
          <li>
            <span>Lingua: </span>
            <img
              v-if="element.original_language === 'it'"
              src="../assets/it.png"
              alt=""
            />
            <img
              v-if="element.original_language === 'en'"
              src="../assets/en.png"
              alt=""
            />
            <span
              v-if="
                element.original_language != 'en' &&
                  element.original_language != 'it'
              "
              >{{ element.original_language }}</span
            >
          </li>
          <li>
            <i
              v-for="(element, index) in element.vote_average"
              :key="index"
              class="fas fa-star"
            ></i>
            <i
              v-for="(element, index) in 5 - element.vote_average"
              :key="'A' + index"
              class="far fa-star"
            >
            </i>
          </li>
          <li>Trama: {{ element.overview }}</li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Film",
  props: ["films"],
};
</script>

<style scoped lang="scss">
@import "@/style/film.scss";
</style>

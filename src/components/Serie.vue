<template>
  <main v-show="serie.length > 0">
    <div class="title">
      <h2>Serie tv</h2>
    </div>
    <div class="container">
      <div class="box" v-for="(element, index) in serie" :key="index">
        <img v-if="element.poster_path" :src="element.poster_path" alt="" />
        <img
          v-else
          class="img-else"
          src="https://www.altavod.com/assets/images/poster-placeholder.png"
          alt=""
        />
        <ul>
          <li>Titotlo: {{ element.name }}</li>
          <li>Titolo originale: {{ element.original_name }}</li>
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
  name: "Serie",
  props: ["serie"],
};
</script>

<style scoped lang="scss">
@import "@/style/serie.scss";
</style>

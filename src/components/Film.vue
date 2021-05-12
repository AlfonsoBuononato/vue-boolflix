<template>
  <main>
    <div class="title">
      <h2>film</h2>
    </div>
    <div>
      <ul
        v-for="(element, index) in films"
        :key="index"
        :style="{ backgroundImage: 'url(' + element.poster_path + ')' }"
      >
        <li>{{ element.title }}</li>
        <li>{{ element.original_title }}</li>
        <!-- <li>
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
        </li> -->
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
      </ul>
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

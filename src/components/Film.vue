<template>
  <main>
    <div
      v-for="(element, index) in films"
      :key="index"
      :style="{ backgroundImage: 'url(' + element.poster_path + ')' }"
    >
      <ul>
        <li>{{ element.title }}</li>
        <li>{{ element.original_title }}</li>
        <li>
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
            :key="index"
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

<style>
* {
  color: red;
}

.active {
  background-color: white;
}
</style>

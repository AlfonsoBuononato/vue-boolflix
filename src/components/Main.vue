<template>
  <main>
    <div v-for="(element, index) in films" :key="index">
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
        <li>{{ element.vote_average }}</li>
      </ul>
    </div>
    <!-- SERIE TV -->
    <div v-for="(element, index) in serie" :key="index">
      <ul>
        <li>{{ element.original_name }}</li>
        <li>{{ element.name }}</li>
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
        <li>{{ element.vote_average }}</li>
      </ul>
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["films", "serie"],
};
</script>

<style></style>

<template>
  <main>
    <div v-for="(element, index) in films" :key="index">
      <ul>
        <li>{{ element.title }}</li>
        <li>{{ element.original_title }}</li>
        <li>{{ element.original_language }}</li>
        <li>{{ element.vote_average }}</li>
      </ul>
    </div>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["films"],
};
</script>

<style></style>

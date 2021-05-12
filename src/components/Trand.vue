<template>
  <div>
    <div>
      <ul v-for="(element, index) in trand" :key="index">
        <li>{{ element.title }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Trand",
  props: ["trand"],
};
</script>

<style scoped>
* {
  color: white;
}
</style>

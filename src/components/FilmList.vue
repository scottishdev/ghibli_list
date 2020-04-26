<template lang="html">
  <div>
    <ul>
      <p>Film List</p>
      <film-item v-for="(film, index) of films" :film="film" :key="index"></film-item>
    </ul>
  </div>
</template>

<script>
import FilmItem from "./FilmItem.vue";

export default {
  name: "film-list",
  props: ['films'],
  components: {
    "film-item": FilmItem
  }
}
</script>

<style lang="css" scoped>
</style>

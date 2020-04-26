<template lang="html">
  <div>
    <ul>
      <li>Title: {{filmSelect.title}}</li>
      <li>Release Date: {{filmSelect.release_date}}</li>
      <li>Director: {{filmSelect.director}}</li>
      <li>Producer: {{filmSelect.producer}}</li>
      <li>Descripton: {{filmSelect.description}}</li>
      <li><button v-on:click="handleClickWL" type="button">Add To Watch List</button></li>
      <br>
    </ul>
  </div>
</template>

<script>
import {eventBus} from "../main.js";

export default {
  name: "film-detail",
  props: ["filmSelect"],
  methods: {
    handleClickWL: function(){
      eventBus.$emit("add-film", this.filmSelect);
    }
  }
}
</script>

<style lang="css" scoped>
</style>

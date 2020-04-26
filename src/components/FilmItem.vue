<template lang="html">
  <div>
    <ul>
      <li v-on:click="handleClickOnTitle">{{film.title}}</li>
      <br>
    </ul>
  </div>
</template>

<script>
import {eventBus} from "../main.js"

export default {
  name: "film-item",
  props: ['film'],
  methods: {
    handleClickOnTitle: function() {
      eventBus.$emit("film-select", this.film)
    }
  }
}
</script>

<style lang="css" scoped>
</style>

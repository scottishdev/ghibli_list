<template lang="html">
<div class="">
  <p>Watch List</p>
  <li v-for="(film, index) of watchListArray">{{film.title}} <button v-on:click="RemoveFromList(index)">Remove</button></li>
</div>
</template>

<script>

export default {
  name: "watch-list",
  props: ['watchListArray'],
  methods:{
    RemoveFromList: function(index){
      this.watchListArray.splice(index,1)
    }
  }
}
</script>

<style lang="css" scoped>
</style>

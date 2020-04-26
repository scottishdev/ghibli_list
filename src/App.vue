<template lang="html">
  <div class="container">
    <ghibli-header title="Ghibli Header" class="header"></ghibli-header>
    <div class="main">
      <film-list :films="films" class="list"></film-list>
      <div class="secomdary">
        <film-detail v-if="filmSelect" :filmSelect="filmSelect" class="film-detail"></film-detail>
        <watch-list v-if="watchListArray.length" :watchListArray="watchListArray" class="watch-list"></watch-list>
      </div>
    </div>
    <div class="footer">

    </div>
  </div>
</template>

<script>
import GhibliHeader from "./components/GhibliHeader.vue";
import FilmList from "./components/FilmList.vue";
import FilmDetail from "./components/FilmDetail.vue";
import WatchList from "./components/WatchList.vue";

import {eventBus} from "./main.js"

export default {
  name: "app",
  data() {
    return{
      films: [],
      filmSelect: null,
      watchListArray: [],
    }
  },
  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
    .then(response => response.json())
    .then(films => this.films = films);

    eventBus.$on("film-select", (film) => {this.filmSelect = film});

    eventBus.$on("add-film", (film) => {
      if (this.watchListArray.includes(film)){
        alert("Film has already added To Watch List.")
      }else{
        this.watchListArray.push(film)
      }
    });
  },
  components: {
    "ghibli-header": GhibliHeader,
    "film-list": FilmList,
    "film-detail": FilmDetail,
    "watch-list": WatchList
  }
}
</script>

<style lang="css" scoped>
.container {
  display: flex;
  flex-direction: column;
  border-style: solid;
}
.main{
  display: flex;
  border-style: solid;
}
.list {
  display: flex;
  flex-direction: row;
  border-style: solid;
  align-items: flex-start;
  width: 500px;
  flex-wrap: nowrap;}

  .header { }

  .secondary{
    display: flex;
    flex-direction: row;
  }
  .film-detail {
    display: flex;
    flex-direction: row;
    border-style: solid;
    align-items: flex-start; }

    .watch-list {
      display: flex;
      flex-direction: row;
      border-style: solid;
      align-items: flex-start;}
      </style>

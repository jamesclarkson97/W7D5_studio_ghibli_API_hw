<template>
  <div v-if="film">
      <h4>Title: </h4>
      <p>{{film.title}}</p>
      <h4>Description: </h4>
      <p>{{film.description}}</p>
      <h4>Directed by: </h4>
      <p>{{film.director}}</p>
      <h4>Release Date: </h4>
      <p>{{film.release_date}}</p>

    <div id="buttons">
        <p>{{characters}}</p>
        </div>
      <!-- <div if see more is clicked, display more information> -->
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'film-detail',
    data() {
        return {
            film: null
        }
    },
    mounted() {
        eventBus.$on('film-select', (film) => {this.film = film})
    },
    props: ['characters']


}
</script>

<style>

</style>
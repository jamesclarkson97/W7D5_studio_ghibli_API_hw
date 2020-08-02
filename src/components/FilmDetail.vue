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
        <button v-on:click="addCharacters">Show Characters</button>
        <ul >
        <!-- <ul v-if="characters_array"> -->
            <li v-for="(character, index) in characters_array" :character="character" :key="index">{{character.name}}</li>
        </ul>
    </div>

  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'film-detail',
    data() {
        return {
            film: null,
            characters_array: []
        }
    },
    mounted() {
        eventBus.$on('film-select', (film) => {this.film = film}) 
    },
    props: ['characters'],
    methods: {
        addCharacters() {
            this.characters_array = this.characters.filter(character => character.films[0] === this.film.url);
        }
    }
}
</script>

<style>

</style>
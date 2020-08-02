<template>
  <div>
      <h2>Studio Ghibli Films:</h2>
    <select @change="handleChange" v-model="selectedFilm">
        <option selected disabled>- Please select a film -</option>
        <option v-for="(film, index) in films" :film="film" :key="index" v-bind:value="film">{{film.title}}</option>
    </select>
</div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
  name: 'film-select',
  data() {
    return {
    //   selectedfilm: null
    };
  },
  props: ['films'],
  methods: {
    handleChange() {
      eventBus.$emit('film-select', this.selectedFilm)
    }
  }
}
</script>

<style>

</style>
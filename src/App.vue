<template>
  <div>
    <film-select :films="films"/>
    <film-detail :characters="characters"/>
  </div>
</template>

<script>
import FilmSelect from './components/FilmSelect.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  name: 'App',
  data() {
    return {
      films: [],
      characters: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(data => this.films = data),
    fetch('https://ghibliapi.herokuapp.com/people/')
    .then(response => response.json())
    .then(data => this.characters = data)
  },
  components: {
    "film-select": FilmSelect,
    "film-detail": FilmDetail,
  }
}
</script>

<style>

</style>

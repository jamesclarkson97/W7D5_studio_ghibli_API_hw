<template>
  <div>
    <film-select :films="films"/>
    <film-detail/>
  </div>
</template>

<script>
import FilmSelect from './components/FilmSelect.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  name: 'App',
  data() {
    return {
      films: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(response => response.json())
    .then(data => this.films = data)
    console.log(this.films)
  },
  components: {
    "film-select": FilmSelect,
    "film-detail": FilmDetail,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

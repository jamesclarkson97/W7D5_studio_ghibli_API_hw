<template>
  <div v-if="film">
      <p>{{film}}</p>
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
    }


}
</script>

<style>

</style>
<template lang="html">
  <div>
    <movie-filter-form :movies="movies"></movie-filter-form>
    <movie-detail v-if="selectedMovie" :movie="selectedMovie"></movie-detail>
  </div>
</template>

<script>
import MovieDetail from '@/components/MovieDetail.vue'
import MovieFilterForm from '@/components/MovieFilterForm.vue'
import {eventBus} from './main.js'

export default {
  name: 'app',
  components: {
    'movie-detail': MovieDetail,
    'movie-filter-form': MovieFilterForm
  },
  data(){
    return {
      movies: [],
      selectedMovie: null
    }
  },
  mounted(){
    fetch('https://swapi.dev/api/films/')
    .then(res => res.json())
    .then(data => this.movies = data.results)

    eventBus.$on('selected-movie', (movie) =>
    this.selectedMovie = movie)
  }
}
</script>

<style lang="css" scoped>
</style>

<template lang="html">
  <div>
  <form v-on:submit.prevent>
    <select v-on:change="handleSelect" v-model="selectedMovie">
      <option disabled value="">Select a Movie</option>
      <option v-for="(movie, index) in movies" :value="movie">{{movie.title}}</option>
    </select>
  </form>
</div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'movie-filter-form',
  data(){
    return {
      selectedMovie: {}
    }
  },
  methods: {
    handleSelect(){
      eventBus.$emit('selected-movie', this.selectedMovie)
    }
  },
  props: ["movies"]
}
</script>

<style lang="css" scoped>
</style>

<template lang="html">
  <div>
    <h2>{{movie.name}}</h2>
    <character-list v-if="characters.length" :characters="characters"></character-list>
  </div>
</template>

<script>
import CharacterList from '@/components/CharacterList.vue'

export default {
  name: 'movie-detail',
  components: {
    'character-list': CharacterList
  },
  data() {
    return {
      characters: []
    }
  },
  methods: {
    getCharacters(){
      const characterPromises = this.movie.characters.map((characterURL) => {
        return fetch(characterURL).then(res => res.json())
      })
      Promise.all(characterPromises)
      .then(data => this.characters = data)
    }
  },
  mounted(){
    this.getCharacters()
  },
  props: ['movie'],
  watch: {
    movie: function(){
      this.getCharacters()
    }
  }
}
</script>

<style lang="css" scoped>
</style>

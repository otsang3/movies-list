<template lang="html">
  <div>
  <ul v-for="(character, index) in characters">
    Name: {{character.name}}
    <br>
    Height: {{character.height}}
    <br>
    <br>
  </ul>
</div>
</template>

<script>
export default {
  name: 'character-list',
  data(){
    return {

    }
  },
  props: ['characters']
}
</script>

<style lang="css" scoped>
</style>

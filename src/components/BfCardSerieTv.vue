<template>
     <div>
        <img :src="'https://image.tmdb.org/t/p/w200' + moviesObject.poster_path" :alt="moviesObject.title">
        <h2>Titolo: {{moviesObject.name}}</h2>
        <p>Titolo Originale: {{moviesObject.original_name}}</p>
        <p>Lingua Originale: {{moviesObject.original_language}}
        <lang-flag :iso="moviesObject.original_language"/>
        </p>
        <p>Voto: {{moviesObject.vote_average}}</p>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'BfCardSerieTv',
  components: {
    LangFlag,
  },
  props: {
    moviesObject: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
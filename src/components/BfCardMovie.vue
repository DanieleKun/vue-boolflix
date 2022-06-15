<template>
     <div>
        <img :src="'https://image.tmdb.org/t/p/w200' + moviesObject.poster_path" :alt="moviesObject.title">
        <h2>Titolo: {{moviesObject.title}}</h2>
        <p>Titolo Originale: {{moviesObject.original_title}}</p>
        <p>Lingua Originale: {{moviesObject.original_language}}
        <lang-flag :iso="moviesObject.original_language"/>
        </p>
        <p>Voto: {{this.ratingCalc}}</p>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'BfCardMovie',
  components: {
    LangFlag,
  },
  props: {
    moviesObject: Object
  },
  computed: {
    ratingCalc() {
      return Math.ceil(this.moviesObject.vote_average / 2);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
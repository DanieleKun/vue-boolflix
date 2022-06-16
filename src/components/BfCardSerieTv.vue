<template>
  <div class="my_card">
        <img :src="'https://image.tmdb.org/t/p/w342' + moviesObject.poster_path" :alt="moviesObject.title">
        <h2>Titolo: {{moviesObject.name}}</h2>
        <p>Titolo Originale: {{moviesObject.original_name}}</p>
        <p>Lingua Originale: {{moviesObject.original_language}}
        <lang-flag :iso="moviesObject.original_language"/>
        </p>
        <!-- <p>Voto: {{moviesObject.vote_average}}</p> -->
        <span>Voto: </span>
        <span>
          <font-awesome-icon v-for="(myStar, i) in ratingCalc()" :key="i" icon="fa-solid fa-star" />
        </span>
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
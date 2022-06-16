<template>
  <div  @mouseover="hover = true" @mouseleave="hover = false" class="my_card">
        <img :src="'https://image.tmdb.org/t/p/w342' + moviesObject.poster_path" :alt="moviesObject.title">
        

        <div v-if="hover" class="show_text">
          <h2><strong>Titolo:</strong> {{moviesObject.title}}</h2>
        <p><strong>Titolo Originale:</strong> {{moviesObject.original_title}}</p>
        <p><strong>Lingua Originale:</strong> {{moviesObject.original_language}}
        <lang-flag :iso="moviesObject.original_language"/>
        </p>
        <!-- <p>Voto: {{this.ratingCalc}}</p> -->
        <span><strong>Voto:</strong> </span>
        <span>
          <font-awesome-icon v-for="(myStar, i) in ratingCalc()" :key="i" icon="fa-solid fa-star" />
          <font-awesome-icon v-for="(myEmptyStar, j) in (5 - ratingCalc())" :key="j" icon="fa-regular fa-star" />
        </span>
        <p><strong>Descrizione:</strong> {{moviesObject.overview}}</p>
        </div>
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

  data() {
    return {
      hover: false,
    }
  },

  methods: {
    ratingCalc() {
      return Math.round(this.moviesObject.vote_average / 2);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .my_card{
    width: 20%;
    background-color: black;
    color: white;
    margin: 20px;
    padding: 10px;
    position: relative;


    img{
      width: 100%;
    }

    .fa-star{
      color: gold;
    }

    .show_text{
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.8);
      padding: 10px;
      overflow: auto;
      
    }

  }
</style>
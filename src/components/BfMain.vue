<template>
  <div id="my_header">
    <div class="title"><h1>Booflix</h1></div>
    <div class="my_input">
        <input type="text">
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'BfMain',

  // API per ricerca film
    data() {
        return {
            apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=e0d448c1e7dce7079f34bc165c15b525&language=it-IT&query=",
            moviesList: [],
            userInput: "",

        }
    },

      created() {
        this.getMovies()
    },

    methods: {
      getMovies(){

        axios
        .get(this.apiUrl)
        .then((result) => {
          this.moviesList = result.data.results
        })
        .catch((error) => {
          console.log("errore", error);
        })
      }
    }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #my_header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 80px;
        background-color: black;

        h1{
            color: red;
        }
    }
</style>

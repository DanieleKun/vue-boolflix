<template>
  <div id="container">
    <div class="my_header">
      <div class="title">
        <h1>Booflix</h1>
      </div>

      <div class="search_bar">
        <BfSearchBar @mySearch="searchMovies" />
      </div>
    </div>


    <main id="card_container">
      <BfCard v-for="(item, i) in moviesList" :key="i" :moviesObject="item" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import BfCard from './BfCard.vue';
import BfSearchBar from './BfSearchBar.vue';

export default {
  name: 'BfMain',
  components: {
    BfCard,
    BfSearchBar
  },

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
    getMovies() {
      if (this.userInput !== "") {
        const myUrl = this.apiUrl + this.userInput;
        axios
          .get(myUrl)
          .then((result) => {
            this.moviesList = result.data.results;
          })
          .catch((error) => {
            console.log("Errore", error);
          })
      }
    },

    searchMovies(userText) {
      this.userInput = userText;
      this.getMovies()
    }



  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.my_header {
  height: 80px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;

  h1 {
  color: red;
}

  // #card_container{
  //   display: flex;
  //   justify-content: space-evenly;
  //   flex-wrap: wrap;
  // }
}




</style>

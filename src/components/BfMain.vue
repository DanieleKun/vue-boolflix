<template>
  <div id="my_header">
    <div class="title">
      <h1>Booflix</h1>
    </div>

      <BfSearchBar @mySearch="searchMovies"/>
    

    <BfCard v-for="(item, i) in moviesList" :key="i" :contentObject="i" />
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

    searchMovies(userText){
      this.userInput = userText;
      this.getList()
    }



  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
#my_header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  background-color: black;

  h1 {
    color: red;
  }
}
</style>

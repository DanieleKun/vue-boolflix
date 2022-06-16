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


    <main>
      <section class="card_container">
        <BfCardMovie v-for="item in moviesList" :key="item.id" :moviesObject="item" />
        <BfCardSerieTv v-for="itemTv in serieList" :key="itemTv.id" :moviesObject="itemTv" />
      </section>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import BfCardMovie from './BfCardMovie.vue';
import BfSearchBar from './BfSearchBar.vue';
import BfCardSerieTv from './BfCardSerieTv.vue';


export default {
  name: 'BfMain',
  components: {
    BfCardMovie,
    BfSearchBar,
    BfCardSerieTv
  },

  // API per ricerca film
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/movie?api_key=e0d448c1e7dce7079f34bc165c15b525&language=it-IT&query=",
      apiUrlSerie: "https://api.themoviedb.org/3/search/tv?api_key=e0d448c1e7dce7079f34bc165c15b525&language=it-IT&query=",
      moviesList: [],
      serieList:[],
      userInput: "",

    }
  },

  created() {
    this.getMovies()
  },

  methods: {
    getMovies() {
      if (this.userInput !== "") {
        // Movie
        const myUrl = this.apiUrl + this.userInput;
        axios
          .get(myUrl)
          .then((result) => {
            this.moviesList = result.data.results;
          })
          .catch((error) => {
            console.log("Errore", error);
          });
          
          // serie tv
          const myUrlSerie = this.apiUrlSerie + this.userInput;
        axios
          .get(myUrlSerie)
          .then((result) => {
            this.serieList = result.data.results;
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

#container{
  background-color: gray;
}
.my_header {
  height: 80px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;

  h1 {
  color: red;
}

.title, .search_bar{
  margin: 0 20px;
}

}

.card_container{
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}




</style>

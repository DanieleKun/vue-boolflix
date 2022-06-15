<template>
     <div>
        <h2>Titolo: {{moviesObject.title}}</h2>
        <p>Titolo Originale: {{moviesObject.original_title}}</p>
        <p>Lingua Originale: {{moviesObject.original_language}}</p>
        <p>Voto: {{moviesObject.vote_average}}</p>
    </div>
</template>

<script>
export default {
  name: 'BfCard',
  props: {
    moviesObject: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
<template>
  <div class="search_bar">
    <input type="text" placeholder="Search Movie" v-model="userText" @keyup.enter="inputValue">
  </div>
</template>

<script>
export default {
  name: 'BfSearchBar',

  data(){
    return {
        userText:""
    }
  },

  methods: {
    inputValue(){
        this.$emit('mySearch', this.userText)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
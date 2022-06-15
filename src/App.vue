<template>
  <div id="app">
    <BfMain/>
    <!-- <BfCard/> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import BfMain from './components/BfMain.vue'
// import BfCard from './components/BfCard.vue'
// import BfSearchBar from './components/BfSearchBar.vue'


export default {
  name: 'App',
  components: {
    BfMain,
    // BfCard,
    // BfSearchBar
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;
}
</style>

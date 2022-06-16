<template>
  <div id="app">
    <BfMain/>
  </div>
</template>

<script>

import BfMain from './components/BfMain.vue'



export default {
  name: 'App',
  components: {
    BfMain,
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Scrollbar */
*::-webkit-scrollbar {
    width: 10px;
  }
  
  *::-webkit-scrollbar-track {
    background: black;
  }
  
  *::-webkit-scrollbar-thumb {
    background-color: rgb(79, 79, 79);
    border-radius: 20px;
    border: 2px solid rgb(79, 79, 79);;
  }

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  // color: #2c3e50;
  // margin-top: 60px;
  background-color: gray;
  height: 100vh;
}
</style>

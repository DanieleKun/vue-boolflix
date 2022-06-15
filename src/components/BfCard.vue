<template>
  <div class="my_card">
    <ul>
      <li>{{moviesObject.title}}</li>
    </ul>
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
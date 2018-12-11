<template>
  <div class="alert alert-secondary greeting">
    <h1 class="pb-20">Please solve the below equation</h1>
    <h2> {{ x }} + {{ y }} = {{ result }} </h2>

  </div>
</template>

<script>
export default {
  name: 'GameCanvas',
  data () {
    return {
      x: 0,
      y: 0,
      result: '?'
    }
  }
}
</script>

<style scoped>
.greeting {
    width: 70%;
    margin: 20px auto;
    text-align: center;
}
</style>

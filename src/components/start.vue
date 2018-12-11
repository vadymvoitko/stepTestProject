<template>
  <div class="alert alert-secondary greeting">
    <h3>Are you ready ?</h3>
    <button @click="$emit('startGame', 'gameCanvas')">Get Started</button>
  </div>
</template>

<script>
export default {
  name: 'Start',
  data () {
    return {

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

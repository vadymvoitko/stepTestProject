<template>
  <div class="alert alert-secondary greeting">
    <h3>{{ intMessage }}</h3>
    <button >Next question</button>
  </div>
</template>

<script>
export default {
  name: 'Info',
  data () {
    return {

    }
  },
  props: ['intMessage']
}
</script>

<style scoped>
.greeting {
    width: 70%;
    margin: 20px auto;
    text-align: center;
}
</style>

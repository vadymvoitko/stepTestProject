<template>
  <div class="container">
    <form >
      <input v-for="(v, i) in fields" :type="v" :key="i">
    </form>
  </div>
</template>

<script>
export default {
  name: 'Forms',
  data(){
    return {

    }
  },
  props: ['fields']
}
</script>

<style scoped>
  .container {
    width: 20%;
    margin: auto;
    background-color: #ebebeb;
    box-shadow: 1px 2px 2px grey;
  }
</style>

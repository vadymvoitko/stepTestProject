<template>
  <div class="container">
    <div v-for="i in 5" :key="i">
      {{ i }}
      <Forms v-if="!count" count='1'/>
    </div>
  </div>
</template>

<script>
import Forms from './forms'
export default {
  name: 'Forms',
  data(){
    return {
      input1: ''
    }
  },
  components: {
    Forms
  },
  // props: ['fields', 'header', 'footer']
  props: {
    'fields': Array,
    'header': String,
    'footer': {
      type: Number
    },
    count: String
  },
  methods: {
    al() {
      alert()
    }
  }
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

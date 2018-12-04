<template>
  <div class="container">
    <form>
      <div>{{ header }}</div>
      <input
        v-for="(v, i) in fields"
        v-model='input1'
        :type="v"
        :key="i"
        @keyup.enter="$emit('eventName')"
        @contextmenu.prevent="al"
      >
      <button
        @click="$emit('left')"
        @contextmenu="$emit('right')"
      >
      click
      </button>
      <div>{{ footer }}</div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Forms',
  data(){
    return {
      input1: ''
    }
  },
  // props: ['fields', 'header', 'footer']
  props: {
    'fields': Array,
    'header': String,
    'footer': {
      type: Number
    }
  },
  methods: {
    handleEnter(event) {
      this.$emit('eventName') parentEvent(this.input1)
      this.input1 = ''
    },
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

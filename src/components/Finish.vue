<template>
  <div class="alert alert-secondary greeting">
    <h3>{{ finalMessage }}</h3>
    <button @click="finalClick">GO</button>
  </div>
</template>

<script>
export default {
  name: 'Finish',
  data () {
    return {

    }
  },
  computed: {
    finalMessage () {
      return this.succeeded == this.numberOfSteps ? 'Good Job! Continue?'
      : `You failed. ${this.succeeded} / ${this.numberOfSteps} is correct.
      Start again?
      `
    }
  },
  methods: {
    finalClick () {
      this.$emit('finalClick', this.succeeded == this.numberOfSteps)
    }
  },
  props: ['finishMessage', 'succeeded', 'numberOfSteps']
}
</script>

<style scoped>
.greeting {
    width: 70%;
    margin: 20px auto;
    text-align: center;
}
</style>

<template>
  <div class="alert alert-secondary greeting">
    <h1 class="pb-20">Please solve the below equation</h1>
    <h2> {{ x }} + {{ y }} = {{ result }} </h2>
    <button
      v-for="(item, index) in answerOptions"
      :key="index"
    >
    {{ item }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'GameCanvas',
  data () {
    return {
      x: 0,
      y: 0,
      result: '?',
      from: -100,
      to: 100,
      expectedResult: 0,
      numberOfButtons: 3,
      answerOptions: []
    }
  },
  methods: {
    generateNumber(from, to) {
      return Math.ceil(Math.random()*(to - from) + from)
    },
    generateMembers(){
      this.x = this.generateNumber(this.from, this.to);
      this.y = this.generateNumber(this.from, this.to);
      this.expectedResult = this.x + this.y
      this.answerOptions.push(this.expectedResult)
      for (let i=0; i < this.numberOfButtons - 1; i++) {
        const newOption = this.expectedResult + this.generateNumber(-10, 10);
        this.answerOptions.push(newOption)
      }
    }
  },
  created () {
    this.generateMembers()
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

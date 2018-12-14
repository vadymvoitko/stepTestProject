<template>
  <div class="alert alert-secondary greeting">
    <h4 class="pb-20">Please solve the below equation</h4>
    <h2> {{ x }} + {{ y }} = {{ result }} </h2>
    <button
      v-for="(item, index) in answerOptions"
      :key="index"
      class="btn btn-primary answers"
      @click="insertOption"
    >
    {{ item }}
    </button>
    <hr>
    <button @click="proceed">Continue</button>
    {{ test }}
  </div>
</template>

<script>
export default {
  name: 'GameCanvas',
  data () {
    return {
      x: 0,
      test: 10,
      y: 0,
      result: '?',
      from: -100,
      to: 100,
      expectedResult: 0,
      numberOfButtons: 3,
      answerOptions: []
    }
  },
  timers: {
    log: { time: 1000, autostart: true, repeat: true }
  },
  methods: {
    log () {
      this.test--
      if (!this.test) {
        this.$timer.stop('log')
      }
    },
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
      this.shuffle(this.answerOptions)
    },
    shuffle(targetArray){
      return targetArray.sort(() => {
        return Math.random() - 0.5
      })
    },
    insertOption(event){
      this.result = event.target.innerHTML
    },
    proceed () {
      if (this.result === '?') {
        alert('Please select the answer');
        return;
      }
      if (this.result == this.expectedResult) {
        this.$emit('checkOneAnswer', `Your answer is correct !
        Would you like to proceed`)
        this.$emit('success')
      } else {
        this.$emit('checkOneAnswer', `Your answer is wrong,
        Correct answer is ${this.expectedResult}!
        Would you like to proceed`)
      }
      this.$emit('switchView', 'Info')
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

.answers {
  margin: 12px;
  width: 70px;
}
</style>

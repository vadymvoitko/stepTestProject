<template>
  <div class="">
    <div class="progress">
      <div
        class="progress-bar"
        role="progressbar"
        aria-valuenow="70"
        aria-valuemin="0"
        aria-valuemax="100"
        :style="{width: currentWidth}"
        >
      <span class="sr-only">70% Complete</span>
      </div>
    </div>
    <transition name="rotate" mode="out-in">
        <Start @startGame="switchView" v-if="currentView === 'start'"/>
        <GameCanvas
            @switchView="switchView"
            @success="succeeded++"
            @checkOneAnswer="checkOneAnswer"
            v-else-if="currentView === 'gameCanvas'"/>
        <Info
            :intMessage="intMessage"
            @switchView1="switchView"
            v-else-if="currentView === 'Info'"/>
        <Finish
          :succeeded="succeeded"
          :numberOfSteps="numberOfSteps"
          @finalClick="levelCompleted"
          v-else-if="currentView === 'Finish'"
        />
    </transition>
  </div>
</template>

<script>
import Start from './components/start'
import Info from './components/Info'
import Finish from './components/Finish'
import GameCanvas from './components/GameCanvas'

export default {
    name: 'App',
    data() {
        return {
          currentView: 'start',
          intMessage: '',
          currentStep: 0,
          numberOfSteps: 3,
          succeeded: 0
        }
    },
    components: {
      Start,
      GameCanvas,
      Info,
      Finish
    },
    computed: {
      currentWidth () {
        return (this.currentStep/this.numberOfSteps)*100 + '%';
      }
    },
    methods: {
      switchView (view, token) {
        if (token) {
          if (this.currentStep < this.numberOfSteps) {
            this.currentView = 'gameCanvas'
          } else {
            this.currentView = 'Finish'
          }
          return;
        }
        this.currentView = view
      },
      checkOneAnswer (message) {
        this.currentStep++
        this.intMessage = message
      },
      levelCompleted (token) {
        console.log('Next level - ', token)
        this.currentView = 'gameCanvas';
        this.currentStep = 0;
        this.succeeded = 0;
      }
    },
    created() {

    }
}
</script>

<style>
    .rotate-enter-active{
       animation: rotateInX 0.3s linear;
    }
    .rotate-leave-active{
        animation: rotateOutX 0.3s linear;
    }
    .rotate-enter, .rotate-leave-to {

}
    @keyframes rotateInX{
        from{transform: rotateX(90deg);}
        to{transform: rotateX(0deg);}
    }
    @keyframes rotateOutX{
        from{transform: rotateX(0deg);}
        to{transform: rotateX(90deg);}
    }
</style>

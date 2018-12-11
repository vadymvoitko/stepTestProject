<template>
  <div class="">
    <Start @startGame="switchView" v-if="currentView === 'start'"/>
    <GameCanvas v-else-if="currentView === 'gameCanvas'"/>
  </div>
</template>

<script>
import Start from './components/start'
import GameCanvas from './components/GameCanvas'

export default {
    name: 'App',
    data() {
        return {
          currentView: 'start'
        }
    },
    components: {
      Start,
      GameCanvas
    },
    methods: {
      switchView (view) {
        this.currentView = view
      }
    },
    created() {

    }
}
</script>

<style>

</style>

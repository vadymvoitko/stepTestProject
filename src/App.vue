<template>
  <div>
    <Forms :fields="fields1"></Forms>
    <Forms :fields="fields2"></Forms>
    <Forms :fields="fields3"></Forms>
  </div>
</template>

<script>
import Forms from './components/forms'

export default {
    name: 'App',
    data() {
        return {
          currentView: 'square',
          fields1: ['text', 'radio', 'checkbox', 'submit'],
          fields2: ['text', 'text', 'submit'],
          fields3: ['text', 'number',  'submit']
        }
    },
    components: {
      Forms
    },
    methods: {

    }
}
</script>

<style>
* {
    box-sizing: border-box;
}

body {
    padding: 0;
    margin: 0;
    font-family: 'Roboto', sans-serif;
}

header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 48px;
}

nav {
    list-style:none;
    margin:0;
    padding:0;
    text-align:center;
}

nav a {
    display: inline-block;
    padding: 16px 20px;
    text-decoration: none;
    color:  #8a8d96;
    font-weight: 400;
}

nav a:hover {
    color: #272727;
}

/* Фигуры */
.square,
.triangle,
.circle,
.egg {
    position: absolute;
    top: 120px;
    left: 50%;
}

.square {
    width: 240px;
    height: 240px;
    background-color: #00bcd4;
    margin-left: -120px;
}

.triangle {
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 120px 207.8px 120px;
    border-color: transparent transparent #3f51b5 transparent;
    margin-left: -120px;
}

.circle {
    width: 240px;
    height: 240px;
    border-radius: 50%;
    background-color: #cddc39;
    margin-left: -120px;
}

.egg {
    width: 168px;
    height: 240px;
    background-color: #ffc107;
    border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
    margin-left: -84px;
}

.switch-enter-active,  .switch-leave-active {
    transition: all 0.6s ease-in-out;
}

.switch-enter {
    left: -50%;
}
.switch-leave-to {
    left: 150%;
}

.switch-enter-to {
    left: 50%
}
.switch-leave {
    left: 50%
}
</style>

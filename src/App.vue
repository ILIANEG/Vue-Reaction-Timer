<template>
<div class="mainMenu">
  <h1>Ninja Reaction Timer</h1>
  <button class="startButn" v-if="!gameStarted" @click="startGame()">play</button>
  <Block v-if="gameStarted" @hit="finishGame()" @start="startTimer()" />
  <Results :time="time" v-if="isOver" />
</div>
</template>

<script>
import Block from './components/Block'
import Results from './components/Results'

export default {
  data() {
    return {
      isOver: false,
      gameStarted: false,
      startTime: 0,
      time: 0,
    }
  },
  name: 'App',
  components: { Block, Results },
  methods: {
    startGame() {
      this.gameStarted = true
    },
    startTimer() {
      this.startTime = new Date().getTime()
    },
    finishGame() {
      this.gameStarted = false
      this.isOver = true
      this.time = new Date().getTime() - this.startTime
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.startButn {
  background-color: rgb(0, 150, 219);
  color: white;
  border: 0;
  padding: 8px 25px 8px 25px;
  border-radius: 5px;
  opacity: 20%
}
.startButn:hover {
  opacity: 100%;
}
</style>

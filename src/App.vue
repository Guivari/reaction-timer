<template>
  <h1>{{ title }}</h1>
  <div class="backdrop">
    <button :disabled="isPlaying" @click="start">Play<span v-show="score!=null && !isPlaying"> again</span>!</button>
    <Block v-if="isPlaying" :delay="timer" @end="endGame"/>
    <Result v-if="score!=null && !isPlaying" :score="score"/>
  </div>
  
</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components:{ Block, Result },
  data() {
    return {
      isPlaying: false,
      title: "Test your reaction time!",
      timer: null,
      score: null
    }
  },
  methods: {
    start() {
      if (!this.isPlaying) {
        this.timer = 2000 + Math.random()*5000
        this.isPlaying = true
        console.log(this.timer)
      }
    },
    endGame(reactionTime) {
      this.isPlaying = false
      console.log(reactionTime)
      this.score = reactionTime
    }
  }
}
</script>

<style>
#app, .mnodals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

</style>

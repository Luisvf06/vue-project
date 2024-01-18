<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: {Block},
  data() {
    return {
      isPlaying: false,
      delay: null,
      score:null,
      showResults:false
    }
  },
  methods: {
    start(){
      this.delay=1000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults=false
    },
    endGame(reactionTime){
      this.isPlaying=false
      this.showResults=true
      this.score=reactionTime
      document.getElementById('boton').innerText='play again'
    }
  }
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  </header>


  <main>
   <h1> Ninja Reaction Timer</h1>
   <button id="boton" @click="start" :disabled="isPlaying">Play</button>
   <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
   <Results v-if="showResults" :score="score"></Results>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

</style>

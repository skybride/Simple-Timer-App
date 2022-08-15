<template>
  <h1>Hello Peaches!</h1>
  <button @click="onPlay" :disabled="start">play</button>
  <Block v-if="start" :delay="delay" @score="getScore"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue'
export default {
  name: 'App',
  components: { Block, Results },
  data(){
    return {
      start: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods:{
    onPlay(){
      this.delay = Math.floor(Math.random() * 7000);
      this.start = true;
      this.showResults = false;
    },
    getScore(reactionTime){ 
      this.score = reactionTime;
      this.start = false;
      this.showResults = true;
    }
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
</style>

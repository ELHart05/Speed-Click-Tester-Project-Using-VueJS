<template>
  <h1>Speed Click Tester</h1>
  <button class="btn" @click="togglePlay()" :disabled="disabled">Play!</button>
  <ResultBar v-if="result" :score="score" :message="message" />
  <BlockBar v-if="isPlaying" :class="{Active: isPlaying}" @haltPlay="stopPlaying" />
</template>

<script>
  import BlockBar from './components/BlockBar.vue';
  import ResultBar from './components/ResultBar.vue';


  export default {
    name: 'App',
    components: {
      BlockBar,
      ResultBar
    },
    data() {
      return {
        isPlaying: false,
        disabled: false,
        result: true,
        delay: null,
        score: '...',
        message: 'State Will be displayed here!'
      }
    },
    methods: {
      changePlayingState() {
        this.isPlaying = true;
      },
      togglePlay() {
        this.delay = 2000 + Math.random() * 4000;
        this.disabled = true;
        this.score = '...';
        this.message = 'State Will be displayed here!';
        setTimeout(this.changePlayingState, this.delay);
      },
      stopPlaying(reactionTime) {
        this.score = reactionTime;
        this.disabled = false;
        this.isPlaying = false;
        if (this.score < 250) {
          this.message = "What a Reaction"
        } else if (this.score < 400) {
          this.message = "Rapid Reflexes"
        } else {
          this.message = "Snail Pace ..."
        }
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
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  .btn {
    padding: 5px 10px;
    font-size: 20px;
    outline: none;
    border: transparent;
    background-color: #42b883;
    border-radius: 10px;
    transition: 1s;
    cursor: pointer;
  }

  .btn:hover {
    background-color: #066138;
  }

  .btn:disabled {
    background-color: red;
  }
</style>
<template>
  <div id="app">
    <Header @setting="setting"/>
    <div class="container">
    <div class="board" contenteditable="true" @input="onInput">
      <span 
        v-for="word in words" 
        :key="word.id" 
        :style="{
          color: settings.color,
          fontSize: settings.fontSize + 'px',
          backgroundColor: settings.backgroundColor,
          fontFamily: settings.fontFamily,
          fontWeight: settings.fontWeight,
          }"
        > 
          {{word.text}}
        </span>
    </div>
  </div>
  </div>
</template>

<script>
import './assets/normalize.scss'
import Header from './components/Header'
export default {
  name: "App",
  data() {
    return {
      board: '',
      settings: {
        fontSize: '14',
        color: 'black',
        backgroundColor: 'white',
        fontFamily: 'Arial',
        fontWeight: 'normal'
      },
      words: [],
      clearBord: ''
    }
  },
  components: {
    Header
  },
  methods: {
    onInput(e) {
      this.board = e.target.innerText
      this.debounce()
    },
    setting(e) {
      this.settings = e
    },
    setWords() {
      this.board.split(' ').map(item => {
        this.words.push({
          id: Date.now(),
          text: item,
          fontSize: this.settings.fontSize,
          color: this.settings.textColor,
          backgroundColor: this.settings.backgroundColor,
          fontFamaly: this.settings.font,
          fontWeight: this.settings.fontWeight
        })
      })
      console.log(this.words)
    }
  },
  computed: {
    debounce() {
      let timeoutId
      return () => {
        clearTimeout(timeoutId)
        timeoutId = setTimeout(() => {
          timeoutId = null
          this.setWords()
          document.querySelector('.board').innerHTML = ''
        }, 1000)
      }
    },
  },
};
</script>

<style lang="scss">
.board {
  width: 100%;
  height: calc(100vh - 75px);
}
</style>

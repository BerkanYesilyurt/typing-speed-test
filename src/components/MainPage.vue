<template>
    <div class="container py-4">
      <header class="pb-3 mb-4 border-bottom">
        <a href="/" class="d-flex align-items-center text-dark text-decoration-none">
          <span class="fs-4">Typing Speed Test</span>
        </a>
      </header>

      <div class="p-5 mb-4 bg-body-tertiary rounded-3">
        <center>
        <div class="card">
          <div class="card-body">
              <div class="container-fluid py-5">
                <h1 class="display-5 fw-bold">Test your typing skills!</h1>
                <p class="col-md-8 fs-4">Want to know how to improve your typing speed? The first step to learn to type fast and increase your typing speed is to take a timed typing test!</p>

                <div v-if="!isFinished">
                <div class="row g-0 text-center p-2 mb-4" style="background-color: #ced4da">
                  <div class="col-sm-6 col-md-12 display-6 p-3">
                    <span class="m-lg-2" v-for="(word,key) in filteredWords" :key="key" v-bind:class="key!==0 || checkWrittenWord">
                      {{word}}
                    </span></div>
                </div>
                <div class="input-group">
                <input class="form-control form-control-lg" type="text" placeholder="Start typing the words above..." v-model="writtenWord">
                  <span class="input-group-text">{{timer}} seconds</span>
                  <button :disabled="this.isStarted" type="button" class="input-group-lg btn btn-primary" @click="setWords">Reload</button>
                </div>
                </div>
                <div v-else>
                  <button type="button" @click="newGame" class="btn btn-primary btn-lg">Start A New Test!</button>
                </div>
              </div>
          </div>
        </div>
        </center>
      </div>

      <div class="row align-items-md-stretch">
        <div class="col-md-6">
          <div class="h-100 p-5 text-bg-dark rounded-3">
            <h2>Change the background</h2>
            <p>Swap the background-color utility and add a `.text-*` color utility to mix up the jumbotron look. Then, mix and match with additional component themes and more.</p>
            <button class="btn btn-outline-light" type="button">Example button</button>
          </div>
        </div>
        <div class="col-md-6">
          <div class="h-100 p-5 bg-body-tertiary border rounded-3">
            <h2>Results</h2>
            <div v-if="this.isFinished">
            <span style="font-size: x-large"><b>True Count:</b> {{trueCount}}</span><br>
            <span style="font-size: x-large"><b>False Count:</b> {{falseCount}}</span><br>
              <span style="font-size: x-large"><b>Total Words:</b> {{trueCount + falseCount}}</span>
            </div>
            <div v-else>
              <span style="font-size: large">You can observe the results in this area when you time is over.</span>
            </div>
          </div>
        </div>
      </div>

      <footer class="pt-3 mt-4 text-body-secondary border-top">
        &copy; 2023
      </footer>
    </div>
</template>

<script>
import wordList from '@/assets/commonWords.json'

export default {
  data () {
    return {
      words: [],
      writtenWord: null,
      trueCount: 0,
      falseCount: 0,
      isCorrect: true,
      timer: 60,
      interval: false,
      isStarted: false,
      isFinished: false,
      wordList: wordList
    }
  },
  watch: {
    writtenWord (value) {
      if (!value || value === ' ') {
        this.writtenWord = ''
        return
      }
      if (!this.isStarted) this.toggleTimer()
      const trueWord = this.words[0].slice(0, value.length)
      this.isCorrect = trueWord === value.replace(' ', '')

      if (value.indexOf(' ') !== -1) {
        this.isCorrect ? this.trueCount++ : this.falseCount++
        this.words.splice(0, 1)
        this.writtenWord = ''
        this.isCorrect = true
      }
    }
  },
  computed: {
    checkWrittenWord () {
      return this.isCorrect ? 'selected-word fw-semibold' : 'selected-word fw-semibold bg-danger'
    },
    filteredWords () {
      return this.words.filter((data, index) => index < 7)
    }
  },
  mounted () {
    this.setWords()
  },
  methods: {
    newGame () {
      this.setWords()
      this.timer = 60
      this.isCorrect = true
      this.isFinished = false
      this.isStarted = false
      this.trueCount = 0
      this.falseCount = 0
      this.writtenWord = ''
    },
    shuffle (array) {
      let counter = array.length
      let temp
      let index

      while (counter--) {
        index = (Math.random() * counter) | 0
        temp = array[counter]
        array[counter] = array[index]
        array[index] = temp
      }

      return array
    },
    toggleTimer () {
      this.isStarted = true
      this.interval = setInterval(() => {
        if (this.timer === 0 || this.timer < 1) {
          clearInterval(this.interval)
          this.isFinished = true
          return
        }
        this.timer--
      }, 1000)
    },
    setWords () {
      this.words = this.shuffle(wordList)
    }
  }

}
</script>

<style scoped>
.selected-word{
  padding: 5px;
  border-radius: 5px;
  background-color: rgb(222,184,135);
}
</style>

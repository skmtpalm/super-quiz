<template>
  <div id="app">
    <app-header></app-header>
    <main class="section">
      <div class="container">
        <div class="columns is-centered">
          <div class="column is-8 is-narrow">
            <transition
                  name="flip"
                  mode="out-in">
              <quiz-board
                  :quiz="quiz"
                  @correctAnswer="checkAnswered"
                  v-if="!this.isCorrect"></quiz-board>
              <correct-board v-else>
                <button
                    class="button is-primary"
                    @click="nextQuiz">Next Question</button>
              </correct-board>
            </transition>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import AppHeader from './components/Header.vue'
import QuizBoard from './components/QuizBoard.vue'
import CorrectBoard from './components/CorrectBoard.vue'

const operator = {
  plus: '+',
  minus: '-'
}

export default {
  components: {
    AppHeader,
    QuizBoard,
    CorrectBoard
  },
  data() {
    return {
      quiz: {
        x: 12,
        y: 34,
        operator: operator.minus
      },
      isCorrect: false
    }
  },
  methods: {
    checkAnswered(isCorrect) {
      if (isCorrect) {
        this.isCorrect = isCorrect
      } else {
        if (confirm('continue?')) {
          return
        }
      }
    },
    nextQuiz() {
      this.isCorrect = false
      this.updateQuiz()
    },
    updateQuiz() {
      this.quiz.x = Math.floor(Math.random() * 100)
      this.quiz.y = Math.floor(Math.random() * 100)
    }
  }
}
</script>

<style lang="scss">
@import "../node_modules/bulma/bulma";
.flip-enter, .flip-leave-to {
  opacity: 0.5;
  transform: rotateY(90deg)
}
.flip-enter-active, .flip-leave-active {
  transition: all 0.3s ease-out;
}
</style>

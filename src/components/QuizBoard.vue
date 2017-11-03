<template>
  <div class="message">
    <div class="message-header is-centered">
      <p class="">Q. What's {{ quiz.x }} {{ quiz.operator }} {{ quiz.y }}?</p>
    </div>
    <div class="message-body">
      <div class="buttons">
        <span class="button"
              v-for="answer in answers"
              @click="handleCorrectAnswer(answer)">{{ answer }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import _ from 'lodash'

export default {
  props: ['quiz'],
  data() {
    return {
      answersCount: 4,
      min: -50,
      max: 50,
      correctAnswer: null
    }
  },
  methods: {
    handleCorrectAnswer(answer) {
      if (answer == this.correctAnswer) {
        console.log(answer + ' is Correnct!')
        this.$emit('correctAnswer', true)
      } else {
        console.log(answer + ' is Wrong')
        this.$emit('correctAnswer', false)
      }
    },
    generateNumbers(min, max, count) {
      let numbers = []
      for (let i=1; i < count; i++) {
        numbers.push(Math.floor(Math.random() * (max - min) + min))
      }
      return numbers
    }
  },
  computed: {
    answers() {
      let answersList = this.generateNumbers(this.min, this.max, this.answersCount)

      switch (this.quiz.operator) {
        case '+':
          this.correctAnswer = this.quiz.x + this.quiz.y
          answersList.push(this.correctAnswer)
          break
        case '-':
          this.correctAnswer = this.quiz.x - this.quiz.y
          answersList.push(this.correctAnswer)
          break
      }

      return _.shuffle(answersList)
    }
  }
}
</script>

<style lang="scss" scoped>
  .buttons {
    .button {
      width: 49%;
      margin: 1rem 0;
    }
  }
  .question__title {
    text-align: center;
  }
</style>

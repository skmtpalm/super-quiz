<template>
  <div id="app">
    <app-header></app-header>
    <main class="section">
      <div class="container">
        <div class="columns is-centered">
          <div class="column is-8 is-narrow">
            <quiz-board></quiz-board>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import AppHeader from './components/Header.vue'
import QuizBoard from './components/QuizBoard.vue'
export default {
  components: {
    AppHeader,
    QuizBoard
  }
}
</script>

<style lang="scss">
@import "../node_modules/bulma/bulma";
</style>

<template>
  <div id="app">
    <app-header></app-header>
  </div>
</template>

<script>
import AppHeader from './components/Header.vue'
export default {
  components: {
    AppHeader
  }
}
</script>

<style lang="scss">
@import "../node_modules/bulma/bulma";
</style>

<template>
  <div class="message is-success">
    <div class="message-header">
      <p>Great!</p>
    </div>
    <div class="message-body has-text-centered">
        <h2 class="title">That's Correct!</h2>
        <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
.title {
  margin-top: 1rem;
}
.button {
  margin: 0.5rem 0;
}
</style>

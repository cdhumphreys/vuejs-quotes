<template>
  <header>
      <h1>Quotes Added</h1>
      <progress-bar :current="numQuotes" :maximum="maxQuotes"></progress-bar>
  </header>
</template>

<script>
import ProgressBar from './ProgressBar.vue';
export default {
    props: ['numQuotes', 'maxQuotes'],
    components: {
        ProgressBar
    }
}
</script>

<style>
    header {
        padding: 20px;
        margin-bottom: 20px;
    }
</style>
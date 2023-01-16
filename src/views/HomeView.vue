<template>
  <Capsules/>
</template>

<script>
import Capsules from '../components/Capsules.vue'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'HomeView',
  components: {
    Capsules
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
}
</style>

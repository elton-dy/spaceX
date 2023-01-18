<template>
  <Launche :launche-id="this.$route.params.id"/>
</template>

<script>
import Launche from '../components/Launche.vue'
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'LaucheView',
  components: {
    Launche
  },

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

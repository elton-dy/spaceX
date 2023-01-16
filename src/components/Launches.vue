<template>
  <div class="hello">
    <h1>Launches</h1>
    <div class="wrapper">

    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Launches',
  props: {

  },
  data()  {
    return {
      Launches: null,
    }
  },
  mounted() {
    axios.get('https://api.spacexdata.com/v4/launches')
        .then((response) => {
          this.Launches = response.data
        })

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wrapper {
  display: grid;
  margin: 30px auto;
  grid-template-columns: repeat(auto-fill, 400px);
  grid-gap: 10px;
  justify-items: center;
}
</style>

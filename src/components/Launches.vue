<template>
  <div class="hello">
    <h1>Launches</h1>
    <div class="wrapper">
      <div class="card" style="width: 18rem;" v-for="launche in launches" :key="launche.id">
        <img :src="launche.links.patch.small" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">{{launche.name}}</h5>
          <p class="card-text">{{getDetails(launche.details)}}</p>
          <a href="#" class="btn btn-primary"><router-link :to="'/launche/' + launche.id"  style="color: white">Read more</router-link></a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Launches',
  components: {

  },
  props: {

  },
  data()  {
    return {
      launches: null,
    }
  },
  mounted() {
    axios.get('https://api.spacexdata.com/v4/launches')
        .then((response) => {
          this.launches = response.data
        })

  },
  methods: {
    getDetails(text){
      if(text) {
        if (text.length > 50 ){
          let result = text.substring(0,50)
          return result + '...'
        }
        return text + '...'
      }
    }
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

<template>
  <div class="hello">
    <h1 v-if="launche">{{launche.name}}</h1>
    <div class="wrapper" v-if="launche">
      <div class="wrapper-img">
        <img :src="launche.links.patch.large" style="height: 70%">
      </div>
      <div>
        <h2 class="card-title">launch Date: {{getDate(launche.date_utc)}}</h2>
        <h2 v-if="launche.success === false">success: <span class="text-danger">{{launche.success}}</span></h2>
        <h2 v-if="launche.success !== false">success: <span class="text-success">{{launche.success}}</span></h2>
        <p>Failures: {{launche.failures[0].reason}}</p>
        <p>{{launche.details}}</p>
        <iframe width="560" height="315" :src="getLinkYb()" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        <div>
          <button type="button" class="btn btn-primary" @click="rtn()">return</button>
          <button type="button" class="btn btn-warning"> <a :href="launche.links.wikipedia" style="color: white ; text-decoration: none">wikipedia</a> </button>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Launche',
  props: {
    launcheId : String
  },
  data()  {
    return {
      launche: null,
    }
  },
  async mounted() {
    await axios.get("https://api.spacexdata.com/v4/launches/"+this.launcheId)
        .then((response) => {
          this.launche = response.data
        })
  },
  methods: {
    getDate(utc){
      let d = new Date(utc)
      return d.getDate() + '/' + (d.getMonth()+1) + '/' + d.getFullYear()
    },
    getLinkYb(){
      return 'https://www.youtube.com/embed/' + this.launche.links.youtube_id
    },
    rtn(){
      window.history.back();
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
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 10px;
  justify-items: center;
}
</style>

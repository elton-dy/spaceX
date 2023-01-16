<template>
  <div class="hello">
    <h1>Capsules</h1>
    <div class="wrapper">
      <div class="card" v-for="capsule in capsules" :key="capsule.id" style="width: 18rem;">
        <div class="card-body">
          <h5 class="card-title">{{capsule.type}},{{capsule.serial}}</h5>
          <p class="card-text">{{capsule.water_landings}} Water landings</p>
          <p class="card-text">{{capsule.land_landings}} land landings</p>
          <p class="card-text">{{capsule.launches.length}} launche</p>
          <p class="card-text text-success" v-if="capsule.status === 'active'"> Status : {{capsule.status}}</p>
          <p class="card-text text-danger" v-if="capsule.status === 'retired'"> Status : {{capsule.status}}</p>
          <p class="card-text text-secondary" v-if="capsule.status === 'unknown'"> Status : {{capsule.status}}</p>
          <p class="card-text">{{capsule.last_update}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Capsules',
  props: {
    msg: String
  },
  data()  {
    return {
      capsules: null,
    }
  },
  mounted() {
    axios.get('https://api.spacexdata.com/v4/capsules')
        .then((response) => {
          this.capsules = response.data
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

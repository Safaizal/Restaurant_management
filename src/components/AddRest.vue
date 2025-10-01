<template>

  <HeaderCom />

  <h1>Add Restaurant</h1>

  <form class="addition">
    <input type="text" v-model="restaurant.name" placeholder="Name">
    <input type="number" v-model="restaurant.contact" placeholder="Contact">
    <input type="text" v-model="restaurant.address" placeholder="Address">
    <button type="button" v-on:click="add"> Submit </button>
  </form>
</template>

<script>

import HeaderCom from './HeaderCom.vue'
import axios from 'axios';

export default {
  name: "AddRest",
  data () {
    return {
      restaurant : {
        name : "",
        contact : "",
        address : ""
      }
    }
  },
  components: {
    HeaderCom
  },
  methods : {
    async add () {
      let result = await axios.post("http://localhost:3000/restaurant", {
        name : this.restaurant.name,
        contact : this.restaurant.contact,
        address : this.restaurant.address
      })

      if(result.status == 201){
        this.$router.push({
          name : "HomePage"
        })
      }
    }
  }
}
</script>

<style>

</style>

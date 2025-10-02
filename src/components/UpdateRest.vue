<template>

  <HeaderCom />

  <h1>Update Restaurant</h1>

  <form class="update">
    <input type="text" v-model="restaurant.id" placeholder="Id">
    <input type="text" v-model="restaurant.name" placeholder="Name">
    <input type="number" v-model="restaurant.contact" placeholder="Contact">
    <input type="text" v-model="restaurant.address" placeholder="Address">
    <button type="button" v-on:click="update"> Submit </button>
  </form>
</template>

<script>

import HeaderCom from './HeaderCom.vue';
import axios from 'axios';

export default {
  name: "UpdateRest",
  data () {
    return {
      restaurant : {
        id : "",
        name : "",
        contact : "",
        address : ""
      }
    }
  },
  components : {
    HeaderCom
  },
  methods : {
    async update () {
      const result = await axios.put("http://localhost:3000/restaurant/" + this.$route.params.id, this.restaurant)
      if(result.status == 200){
        this.$router.push({
          name : "HomePage"
        })
      }
    }
  },
  async mounted () {
    let user = localStorage.getItem("user_info")
    if(!user){
      this.$router.push({
        name : "SignUp"
      })
    }

    const result = await axios.get("http://localhost:3000/restaurant/" + this.$route.params.id)
    
    this.restaurant = result.data

    //console.log(this.$route.params.id) // To get the id which passed in the router-link here the .id is written because in router.js file we put that update:id that's why
  }
}
</script>

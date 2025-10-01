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
      let result = await axios.get("http://localhost:3000/restaurant")
      console.log(result)
    }
  }
}
</script>

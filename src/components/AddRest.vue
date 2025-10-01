<template>

  <HeaderCom />

  <h1>Add Restaurant</h1>

  <div class="addition">
    <input type="text" v-model="name" placeholder="Name">
    <input type="number" v-model="contact" placeholder="Contact">
    <input type="text" v-model="address" placeholder="Address">
    <button v-on:click="add"> Submit </button>
  </div>
</template>

<script>

import HeaderCom from './HeaderCom.vue'
import axios from 'axios';

export default {
  name: "AddRest",
  data () {
    return {
      name : "",
      contact : 0,
      address : ""
    }
  },
  components: {
    HeaderCom
  },
  methods : {
    async add () {
      let result = await axios.post("http://localhost:3000/restaurant", {
        name : this.name,
        contact : this.contact,
        address : this.address
      })

      console.warn(result)
    }
  }
}
</script>

<style>

</style>

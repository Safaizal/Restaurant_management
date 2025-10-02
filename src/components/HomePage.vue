<template>

  <HeaderCom>

  </HeaderCom>

  <h1> Hi {{name}}. This is Home page </h1>
  <div class="table">
    <table border="1">
      <tr>
        <td>Id</td>
        <td>Name</td>
        <td>Contact</td>
        <td>Address</td>
        <td>Actions</td>
        <td>Delete</td>
      </tr>
      <tr v-for="item in restaurants" :key = "item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.contact }}</td>
        <td>{{ item.address }}</td>
        <td><router-link :to="'/update-rest/'+item.id">Update</router-link></td>
        <td><button v-on:click="deleteRest(item.id)">Delete</button></td>
      </tr>
    </table>
  </div>

</template>
<script>

import HeaderCom from './HeaderCom.vue';
import axios from 'axios';

export default {
  name: "HomePage",
  data () {
    return {
      name : "",
      restaurants : []
    }
  },
  components : {
    HeaderCom
  },
  methods : {
    async deleteRest (id) {
      // console.log(id)
      let result = await axios.delete("http://localhost:3000/restaurant/" + id)
      if(result.status == 200){
        this.load()
      }
    },
    async load () {
      let user = localStorage.getItem('user_info')
      this.name = JSON.parse(user).name
      if(!user){
        this.$router.push({
            name : "SignUp"
          })
      }
      let result = await axios.get("http://localhost:3000/restaurant")
      // console.warn(result)
      this.restaurants = result.data
    }

  },
  async mounted () {
    this.load()
  }
}

</script>

<style>
.table {
  display: block;
  display: block;
  justify-items: center;
}
td {
  width: 200px;
  height: 50px;
}
</style>

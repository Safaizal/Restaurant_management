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
      </tr>
      <tr v-for="item in restaurants" :key = "item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.contact }}</td>
        <td>{{ item.address }}</td>
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
  async mounted () {
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

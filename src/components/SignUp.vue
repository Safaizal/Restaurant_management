<template>

  <img class="logo" src="../assets/restaurant-logo-Graphics-12037753-1.jpg" alt="#">

  <h1>Sign Up</h1>

  <div class="register">
    <input type="text" v-model="name" placeholder="Name">
    <input type="email" v-model="email" placeholder="Email">
    <input type="password" v-model="password" placeholder="Password">

    <button v-on:click="SignUp">Sign Up</button>
    <p>
      <router-link to="/login"> Login </router-link>
    </p>
  </div>

</template>

<script>

import axios from 'axios'

export default {
  name : "SignUp",
  data () {
    return {
      name : "",
      email : "",
      password : ""
    }
  },
  methods : {
    async SignUp () {
      let result = await axios.post("http://localhost:3000/users", {
        email:this.email,
        name:this.name,
        password:this.password
      });

      console.warn(result)
      if(result.status == 201){
        localStorage.setItem("user_info", JSON.stringify(result.data))
        this.$router.push({
          name : "HomePage"
        })
      }
    }
  },
  mounted () {
    let user = localStorage.getItem('user_info')
    if(user){
      this.$router.push({
          name : "HomePage"
        })
    }
  }
}
</script>

<style>

</style>

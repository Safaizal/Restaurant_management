<template>

  <img class="logo" src="../assets/restaurant-logo-Graphics-12037753-1.jpg" alt="#">

  <h1>Sign Up</h1>

  <div class="register">
    <input type="text" v-model="name" placeholder="Name">
    <input type="email" v-model="email" placeholder="Email">
    <input type="password" v-model="password" placeholder="Password">

    <button v-on:click="SignUp">Sign Up</button>
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
.logo {
  width: 150px;
}
.register input{
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 2px solid rgb(0, 0, 0);
  border-radius: 5px;
}
.register button{
  width: 320px;
  height: 40px;
  border: 1px solid rgb(0, 0, 0);
  border-radius: 10px;
  background: black;
  color: white;
  cursor: pointer;
}
</style>

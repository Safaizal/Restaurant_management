<template>

  <img class="logo" src="../assets/restaurant-logo-Graphics-12037753-1.jpg" alt="#">

  <h1>Sign Up</h1>

  <div class="register">
    <input type="text" placeholder="Name">
    <input type="email" placeholder="Email">
    <input type="password" placeholder="Password">

    <button>Sign Up</button>
  </div>

</template>

<script>
export default {
  name : "SignUp"
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

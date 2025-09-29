<template>
  <img class="logo" src="../assets/restaurant-logo-Graphics-12037753-1.jpg" alt="#">

  <h1>Login</h1>

  <div class="">
    <input type="email" v-model="email" placeholder="Email">
    <input type="password" v-model="password" placeholder="Password">

    <button >Login</button>
    <p>
      <router-link to="/sign-up"> Sign Up </router-link>
    </p>
  </div>

</template>

<script>

export default {
  name : "LoginPage"
}
</script>

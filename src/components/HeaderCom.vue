<template>
  <div class="nav">
    <router-link to="/"> Home </router-link>
    <router-link to="/add-rest"> Add Restaurant </router-link>
    <a v-on:click="logout" href="#">Logout</a>
  </div>

</template>

<script>

export default {
  name: "HeaderCom",
  methods: {
    logout() {
      localStorage.clear()
      this.$router.push({
        name: "LoginPage"
      })
    }
  }
}

</script>

<style>
.nav {
  background-color: black;
  overflow: hidden;
}

.nav a {
  float: left;
  color: rgb(255, 255, 255);
  padding: 15px 15px;
  text-align: center;
  text-decoration: none;
  margin-right: 10px;
}

.nav a:hover {
  background-color: white;
  color: black;
  transition: 500ms;
}
</style>

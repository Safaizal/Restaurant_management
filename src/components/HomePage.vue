<template>

  <h1> Home page </h1>
  <router-link to="/login"> LogOut </router-link>

</template>
<script>

export default {
  name: "HomePage",
  mounted () {
    let user = localStorage.getItem('user_info')
    if(!user){
      this.$router.push({
          name : "SignUp"
        })
    }
  }
}

</script>

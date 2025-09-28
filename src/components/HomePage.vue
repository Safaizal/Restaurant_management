<template>

  <h1> Home page </h1>

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

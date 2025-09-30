<template>

  <HeaderCom>

  </HeaderCom>

  <h1> Home page </h1>
  <router-link to="/login"> LogOut </router-link>

</template>
<script>

import HeaderCom from './HeaderCom.vue';

export default {
  name: "HomePage",
  components : {
    HeaderCom
  },
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

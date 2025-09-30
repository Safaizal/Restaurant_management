<template>

  <HeaderCom>

  </HeaderCom>

  <h1> Hi {{name}}. This is Home page </h1>

</template>
<script>

import HeaderCom from './HeaderCom.vue';

export default {
  name: "HomePage",
  data () {
    return {
      name : ''
    }
  },
  components : {
    HeaderCom
  },
  mounted () {
    let user = localStorage.getItem('user_info')
    this.name = JSON.parse(user).name
    if(!user){
      this.$router.push({
          name : "SignUp"
        })
    }
  }
}

</script>

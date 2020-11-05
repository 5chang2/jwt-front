<template>
  <div class="login">
    <h1>login</h1>
    <div>
      username : <input type="text" v-model="credentials.username">
      <br>
      password : <input type="password" v-model="credentials.password">
      <br>
      <button @click="getAuthToken">login</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'LoginForm',
  props: {
    msg: String
  },
  data: function(){
    return {
      credentials: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    getAuthToken(){
      axios.post('http://127.0.0.1:8000/accounts/api-token-auth/', this.credentials)
      .then((e)=>{
        console.log(e)
        localStorage.setItem('jwt-token', e.data.token);
      })
      .catch((err)=>{
        console.log(err)
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <div class="create">
    <h1>create</h1>
    <div>
      title : <input type="text" v-model="articleData.title">
      <br>
      content : <input type="password" v-model="articleData.content">
      <br>
      <button @click="createArticle">create</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ArticleForm',
  data: function(){
    return {
      articleData: {
        title: '',
        content: '',
        user: 1
      }
    }
  },
  methods: {
    createArticle(){
      const headers = {
        'Authorization': 'JWT ' + localStorage.getItem('jwt-token')
      }
      console.log(headers)
      axios.post('http://127.0.0.1:8000/articles/', this.articleData, {headers})
      .then(e=>{
        console.log(e)
      })
      .catch(err=>{
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

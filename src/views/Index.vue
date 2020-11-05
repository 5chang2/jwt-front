<template>
  <div class="index">
    <h1>index</h1>
    <div>
      <p v-for="article in articles" v-bind:key="article.id">
        {{ article }}
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Index',
  data: function(){
    return {
      articles: []
    }
  },
  methods: {
    getArticles(){
      const headers = {
        'Authorization': 'JWT ' + localStorage.getItem('jwt-token')
      }
      
      axios.get('http://127.0.0.1:8000/articles/', {headers})
      .then(e=>{
        console.log(e)
        this.articles = e.data
      })
      .catch(err=>{
        console.log(err)
      })
    }
  },
  mounted: function(){
    this.getArticles()
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

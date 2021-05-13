<template>
  <div id="app">
    <h1>Headless news</h1>
    <div v-for="item in news"
    :key="item.id"
    >
      <h2>{{ item.title }}</h2>
      <p>{{ item.intro }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      news: []
    }
  },
  mounted(){
    axios
    .get('http://127.0.0.1:8000/api/v2/pages/?type=news.NewsPage')
    .then(response => (this.news = response.data.items))
  }
}
</script>

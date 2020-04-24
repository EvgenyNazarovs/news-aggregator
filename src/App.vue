<template lang="html">
  <div>
    <ArticleList :articles="articles"></ArticleList>
  </div>


</template>

<script>

import ArticleList from './components/ArticleList';
import ArticleListItem from './components/ArticleListItem';
import {eventBus} from './main.js'

export default {
  name: 'App',
  components: {
    ArticleList
  },
  data(){
    return {
      articles: []
    }
  },
  mounted(){
    fetch('https://newsapi.org/v2/everything?q=bitcoin&pageSize=50&language=en&apiKey=b5eecd356735456598f2942ec30cc690')
    .then(res => res.json())
    .then(data => {
      this.articles = data.articles
      console.log(this.articles);
    })
  }
}
</script>

<style lang="css" scoped>
</style>

<template lang="html">
  <div>
    <ArticleList :articles="feedOne"></ArticleList>
    <ArticleList :articles="feedTwo"></ArticleList>
  </div>


</template>

<script>

import ArticleList from './components/ArticleList';
import ArticleListItem from './components/ArticleListItem';
import {eventBus} from './main.js'

export default {
  name: 'app',
  components: {
    ArticleList
  },
  data(){
    return {
      feedOne: [],
      feedTwo: [],
      apiKey: 'b5eecd356735456598f2942ec30cc690'
    }
  },
  mounted(){
    this.getArticlesFeedOne('bitcoin')
    this.getArticlesFeedTwo('coronavirus')
  },
  methods: {
    getArticlesFeedOne(subject){
      fetch(`https://newsapi.org/v2/everything?q=${subject}&pageSize=25&excludeDomains=thenextweb.com&language=en&apiKey=${this.apiKey}`)
        .then(res => res.json())
        .then(data => this.feedOne = data.articles)
      },
      getArticlesFeedTwo(subject){
        fetch(`https://newsapi.org/v2/everything?q=${subject}&pageSize=50&language=en&apiKey=${this.apiKey}`)
          .then(res => res.json())
          .then(data => this.feedTwo = data.articles)
      }
    }
}
</script>

<style lang="css" scoped>
</style>

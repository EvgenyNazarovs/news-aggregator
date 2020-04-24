<template lang="html">
  <li @mouseover="onArticleHighlight" @mouseleave="onLeave" @click="onArticleSelect">
    <img :src="article.urlToImage" width="150px">{{article.title}}
    <div v-show="selectedArticle">
      {{article.description}}
    </div>
  </li>

</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'ArticleListItem',
  data(){
    return {selectedArticle: null}
  },
  props: ['article'],
  methods: {
    onArticleHighlight(){
      this.selectedArticle = this.article
    },
    onLeave(){
      this.selectedArticle = ""
    },
    onArticleSelect(){
      this.$emit('articleSelect', this.article)
    }
  }
}
</script>

<style lang="css" scoped>
</style>

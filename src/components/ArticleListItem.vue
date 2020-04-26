<template lang="html">
  <li>
    {{article.title}}
    {{article.source.name}}
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

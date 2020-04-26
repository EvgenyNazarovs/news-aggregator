<template lang="html">
  <v-card>
    <v-card-title>
    {{article.title}}
  </v-card-title>
  <v-card-text>
    Source: {{article.source.name}}
  </v-card-text>
</v-card>
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

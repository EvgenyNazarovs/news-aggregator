<template lang="html">
  <ul>
    <ArticleListItem v-for="(article, key) in articles"
                     :article="article"
                     :key="key"
                     >
                     </ArticleListItem>
  </ul>
</template>

<script>

import ArticleListItem from './ArticleListItem';

export default {
  name: 'ArticleList',
  props: ['articles'],
  components: {
    ArticleListItem
  }
}
</script>

<style lang="css" scoped>
</style>

<template lang="html">
  <div>
    <ArticleListItem v-for="(article, key) in articles"
                     :article="article"
                     :key="key"
                     >
                     </ArticleListItem>
  </div>
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

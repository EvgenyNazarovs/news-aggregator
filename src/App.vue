<template lang="html">
  <v-app>
    <NavBar :hotTopics="hotTopics"></NavBar>
  <v-content>
    <v-container fluid>
      <h5>Current topic: {{currentTopic}}</h5>
      <v-row justify="space-around">
        <v-col cols="12" lg="6">
    <ArticleList :articles="articles"></ArticleList>
  </v-col>
</v-row>
  </v-container>
  </v-content>

</v-app>
</template>

<script>
import ArticleList from './components/ArticleList';
import ArticleListItem from './components/ArticleListItem';
import {eventBus} from './main.js'
import NavBar from './components/NavBar';

export default {
  name: 'app',
  components: {
    ArticleList,
    NavBar
  },
  data(){
    return {
      articles: [],
      apiKey: 'b5eecd356735456598f2942ec30cc690',
      currentTopic: 'bitcoin',
      hotTopics: ['bitcoin', 'coronavirus', 'trump']
    }
  },
  mounted(){
    this.getArticles(this.currentTopic)

    eventBus.$on('newTopic', (topic) => {
      this.getArticles(topic)
      this.currentTopic = topic

    })
  },
  methods: {
    getArticles(subject){
      fetch(`https://newsapi.org/v2/everything?q=${subject}&pageSize=25&excludeDomains=thenextweb.com&language=en&apiKey=${this.apiKey}`)
        .then(res => res.json())
        .then(data => this.articles = data.articles)
      }
    },
    created(){
      this.$vuetify.theme.dark = true;
    },
    computed: {
      updateArticles(subject){
        getArticles(subject)
      }
    }
}
</script>

<style lang="css" scoped>
</style>

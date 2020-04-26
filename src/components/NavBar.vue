<template lang="html">
  <v-app-bar app dark>
    <v-toolbar-title>24/7 NEWS</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn v-for="topic in hotTopics"
             :topic="topic"
             v-on:click.native="changeTopic(topic)"
            >{{topic}}
          </v-btn>
  </v-app-bar>

</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'NavBar',
  props: ['hotTopics'],
  methods: {
    changeTopic(topic){
      eventBus.$emit("newTopic", topic)
    }
  }
}
</script>

<style lang="css" scoped>
</style>

<template>
  <div id="app" class="container" >

    <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
    <Newslist v-bind:source="source"></Newslist>

  </div>
</template>

<script>
import Newslist from './components/Newslist'
import SourceSelection from './components/SourceSelection'
export default {
  name: 'app',
  components: {
    Newslist,
    SourceSelection
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    sourceChanged: function (source) {
      this.source = source;
    }
  }
}
</script>

<style>
body {
  background-color: rgba(22, 22, 22,1);
  color: white;
  font-size: 20px!important;
}
#app {
  padding-top: 20px;
}
</style>

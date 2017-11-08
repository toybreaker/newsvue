<template>
  <div id="app" class="container" >

    <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
    <Newslist v-bind:source="source"></Newslist>
    <SourceYears v-on:sourceChanged="sourceChanged"></SourceYears>

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
#app {
 padding-top: 20px;
}
</style>

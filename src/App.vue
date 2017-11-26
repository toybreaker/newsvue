<template>
  <div id="app">
    <div class="bg">
    </div>
    <a class="by" title="coded by Junglestar, check our services!" target="_blank" href="https://junglestar.org">Made by junglestar.org</a>
    <div class="container">
      <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
      <Newslist v-bind:source="source"></Newslist>
    </div>
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
  background-color: #0069cc;
  /*background-color: rgba(22, 22, 22,1);*/
  color: white;
  font-size: 20px!important;
}

.container {
  position: relative;
  z-index: 10;
}

#app {
  padding-top: 20px;
}

.by {
  position: fixed;
  bottom: 0;
  width: 100%;
  text-align: center;
  line-height: 2;
  z-index: 1000;
  color: white;
  font-weight: 300;
  background-color: #0069cc;
}

.bg {
  user-select: none;
  pointer-events: none;
  z-index: 0;
  position: fixed;
  bottom: 8%;
  height: 100vh;
  left: 20%;
  width: 60%;
  background: url("data:image/svg+xml;charset=utf8,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 400'%3E %3Cpath fill='white' d='M328.813 60.47L328.78 224.3c-.006 43.783-11.565 75.953-34.648 96.506-23.096 20.562-53.638 31.03-91.638 31.43-38.827.4-69.976-9.04-93.463-28.317-23.496-19.284-35.235-44.104-35.228-74.486.003-13.4 6.537-20.18 19.618-20.315 13.89-.144 20.838 4.912 20.835 15.163 0 22.482 7.86 40.15 23.593 53.008 15.72 12.85 36.863 19.146 63.433 18.87 27.783-.29 49.23-8.007 64.355-23.153 15.116-15.146 22.688-37.906 22.693-68.28l.036-192.883C261.95 17.906 231.884 10 200 10 95.233 10 10 95.234 10 200.002 10 304.77 95.233 390 200 390c104.766 0 190-85.23 190-189.998 0-55.104-23.588-104.795-61.187-139.533zM56.593 184.72l52.3-49.918-12.416-70.414 64.732 33.195L225.88 64.28l-12.297 70.435 52.39 49.832-72.33 10.334-32.296 64.1-32.408-64.044-72.35-10.215z'/%3E %3C/svg%3E") bottom center no-repeat;
}

@media screen and (min-width: 480px) {
  .bg {
    height: 30vh;
  }
}

</style>
